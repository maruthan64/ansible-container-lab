# Simple Ansible lab in Docker containers.
This action creates four Ubuntu Docker containers on which you can practice simple plays with Ansible.

``` Be sure to only use this lab in a POC environment on a secure local network. ```

## How to use
Clone this repo.

``` 
git clone git@github.com:kmkamyk/ansible-container-lab.git 
```

Enter to repository and generete ssh key
```
cd ansible-container-lab ;ssh-keygen -f ubuntu/keycontainer
```
Run Docker composer from `ansible-container-lab` directory.
```
docker-compose up -d
```

Login to Ctl container.
```
ssh kimyk@10.18.0.10 -i ubuntu/keycontainer
```

Play ad-hoc action from `~/ansible` folder.
```
cd ansible ; ansible nodes -i inventory.yml -m ping
```
###### Have fun !
\
If you do something wrong, just rebuild the containers.
```
docker-compose up --build --force-recreate -d
```
## Clean up
Or if you decide to stop playing, clean up after yourself
```
docker-compose down
```
