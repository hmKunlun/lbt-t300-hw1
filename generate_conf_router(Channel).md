The `Channel` variable is passed in from the Web_URL and obtained via the `nvram_get` function in `generate_conf_router`, causing a stack overflow vulnerability that can lead to arbitrary command execution.

main-->sub_40C360-->start_lan-->start_wlan-->config_wlan-->generate_conf-->generate_conf_router
<img width="791" height="316" alt="image" src="https://github.com/user-attachments/assets/aeb5ce53-d690-41db-bf47-f1cfcf388621" />
<img width="500" height="228" alt="image" src="https://github.com/user-attachments/assets/ff761bbd-5fe1-49d1-ade5-029e32de0455" />
<img width="611" height="445" alt="image" src="https://github.com/user-attachments/assets/818f537f-5776-4207-860b-5a6c8a384b8e" />
<img width="850" height="524" alt="image" src="https://github.com/user-attachments/assets/22992204-d8a9-4b5e-83c8-b7d6ae5c813e" />
<img width="820" height="529" alt="image" src="https://github.com/user-attachments/assets/796003ee-0620-40e1-9749-89c22615401f" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/06e62d32-cf68-4c36-b269-71479f773959" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/043e44d0-4660-47aa-b665-077db96c9284" />

