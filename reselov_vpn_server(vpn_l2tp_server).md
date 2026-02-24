The `vpn_l2tp_server` variable is passed in from the Web and obtained via the `nvram_get` function in `reselov_vpn_server`, causing a stack overflow vulnerability that can lead to arbitrary command execution.



main-->syb_40C360-->start_single_service-->connect_vpn-->reselov_vpn_server

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771762732473-1a0eb9dd-0211-404f-bf5c-080baaca22e1.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771759436031-777bd09c-0253-4ab5-be90-53912669731e.png?x-oss-process=image%2Fformat%2Cwebp)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771762887140-a39bf7c2-a31c-4104-8370-df1e8d3b06e3.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771762974482-7178a730-3f0d-4c3a-b6e8-89ff6ed545a7.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771763051505-57739c04-4a18-4b31-be3e-2d7887b918d6.png)

