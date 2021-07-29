ANSIBLE ESSENTIALS: SIMPLICITY IN AUTOMATION TECHNICAL OVERVIEW (DO007) - RED HAT

- Ad-hoc commands |
-i : inventory path, -m : module (ping, setup, yum). Idempotence principle.
```
ansible all -i hosts -m ping // for connection test
ansible all -i hosts -m setup // for facts gathering
ansible web -i hosts -m yum -a "name=httpd state=present" -b // installing Apache server with root privileges (-b parameter)
ansible web -i hosts -m yum -a "name=httpd state=absent" -b // deleting Apache server with root privileges (-b parameter)
```

