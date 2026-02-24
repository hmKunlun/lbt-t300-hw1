The `Channel` variable is passed in from the Web_URL and obtained via the `nvram_get` function in `generate_conf_router`, causing a stack overflow vulnerability that can lead to arbitrary command execution.



main-->sub_40C360-->start_lan-->start_wlan-->config_wlan-->generate_conf-->generate_conf_router

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771925273451-353e043f-6144-4535-8175-19d9f49e950f.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771921803555-dfc824b5-5663-4b2e-bfae-722b10f318fb.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771924756328-084844b8-705c-485f-8f62-7ce7606c2886.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771924765138-b69d1ce3-e99e-494e-a802-41304fae07ad.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771924804632-0c696a25-3b54-417e-9e64-6e3dbf3934d6.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771925102711-e5dddfd0-72f0-42cf-840d-ed0d6b2b4480.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/42847421/1771763051505-57739c04-4a18-4b31-be3e-2d7887b918d6.png)

