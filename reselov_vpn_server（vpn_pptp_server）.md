The `vpn_pptp_server` variable is passed in from the Web and obtained via the `nvram_get` function in `reselov_vpn_server`, causing a stack overflow vulnerability that can lead to arbitrary command execution.



main-->syb_40C360-->start_single_service-->connect_vpn-->reselov_vpn_server
<img width="718" height="847" alt="image" src="https://github.com/user-attachments/assets/5f996c8c-5265-4343-a7a2-3203b34e3dff" />
<img width="801" height="605" alt="image" src="https://github.com/user-attachments/assets/7e00cac5-974e-496b-8fd0-9d8b52e26f61" />
<img width="889" height="501" alt="image" src="https://github.com/user-attachments/assets/bfbb1457-b1ae-4561-b08e-d436a23828a3" />
<img width="865" height="524" alt="image" src="https://github.com/user-attachments/assets/20650585-8f66-4c2c-9b72-9e211ae79eee" />
<img width="705" height="460" alt="image" src="https://github.com/user-attachments/assets/a909f679-5092-4758-a37e-9691294115b4" />
