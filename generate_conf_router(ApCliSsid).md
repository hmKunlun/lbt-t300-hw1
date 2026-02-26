The `ApCliSsid` variable is passed in from the Web and obtained via the `nvram_get` function in `generate_conf_router`, causing a stack overflow vulnerability that can lead to arbitrary command execution.



main-->sub_40C360-->start_lan-->start_wlan-->config_wlan-->generate_conf-->generate_conf_router
<img width="735" height="411" alt="image" src="https://github.com/user-attachments/assets/886a677c-febd-4893-a2a3-f4153023e111" />

<img width="445" height="298" alt="image" src="https://github.com/user-attachments/assets/f425d9d2-b8bc-4fd9-883b-72f5652bf306" />
<img width="500" height="228" alt="image" src="https://github.com/user-attachments/assets/55ab13a4-cab5-455f-b49b-9b84a6cb9669" />
<img width="611" height="445" alt="image" src="https://github.com/user-attachments/assets/ad5e8016-dc46-432d-8bee-052d49f7ee55" />
<img width="850" height="524" alt="image" src="https://github.com/user-attachments/assets/a7c97a0d-94aa-4458-aeb6-2db5081dfc1d" />
<img width="820" height="529" alt="image" src="https://github.com/user-attachments/assets/bc5a31ee-2175-47af-9cc3-4317240c50c7" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/3b74068e-8724-4f40-99d7-c2d4c466057f" />

