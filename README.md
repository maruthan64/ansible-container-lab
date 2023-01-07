# Simple Ansible labolatory in Docker containers  
This action creates four Docker containers are created on which you can practice simple plays with Ansible.

### How to use
Run Docker composer
```
docker-compose up -d
```

Login to Ctl container
```
ssh kimyk@10.18.0.10 -i ubuntu/keycontainer
```

Play ad-hoc acction from ~/ansible folder
```
ansible nodes -i inventory.yml -m ping
```
### 
