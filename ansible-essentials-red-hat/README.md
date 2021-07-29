ANSIBLE ESSENTIALS: SIMPLICITY IN AUTOMATION TECHNICAL OVERVIEW (DO007) - RED HAT

- Ad-hoc commands |
-i : inventory path, -m : module (ping, setup, yum). Idempotence principle.
```
ansible all -i hosts -m ping // for connection test
ansible all -i hosts -m setup // for facts gathering
ansible web -i hosts -m yum -a "name=httpd state=present" -b // installing Apache server with root privileges (-b parameter)
ansible web -i hosts -m yum -a "name=httpd state=absent" -b // deleting Apache server with root privileges (-b parameter)
```

- Variable precedence

1. Extra vars
2. Task vars (only for the task)
3. Block vars (only for the tasks in the block)
4. Role and include vars
5. Play var_files
6. Play vars_promt
7. Play vars
8. Set_facts
9. Registered vars
10. Host facts
11. Playbook host_vars
12. Playbook group_vars
13. Inventory host_vars
14. Inventory group_vars
15. Inventory vars
16. Role defaults

- Tasks in play
```
tasks:
   - name: add cache dir
     file:
        path: /opt/cache
        state: directory
        
   - name: install nginx
     yum:
        name: nginx
        state: latest
        
   - name: restart nginx
     service:
        name: nginx
        state: restarted
```
- Handler in a play
```
tasks:
    - name: add cache dir
      file:
        path: /opt/cache
        state: directory
        
    - name: install nginx
      yum:
        name: nginx
        state: latest
      notify: restart nginx
        
handlers:
    - name: restart nginx
      service:
        name: nginx
        state: restarted
```
