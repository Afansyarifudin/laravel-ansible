<div align="center">

# laravel-ansible
Template for Automation Deployment Laravel into VPS just using one run command

</div>

## Instalation

```bash
git clone https://github.com/Afansyarifudin/laravel-ansible.git
```

## Requirmenets
- Windows => reccommended to use WSL (Windows Subsystem for Linux)
- Mac
- Linux
- Install python [pip](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#ensuring-pip-is-available)
- Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- SSH ACCESS to you server if you don't have ssh-keys juts generate using this command
```bash
ssh-keygen
```
make sure you locate you ssh-keys to copy you ssh-key into your vps
```bash
ssh-copy-id ./path-to your-public-key/name-of-your-public-key.pub USERNAME@PUBLIC_IP_OF_YOUR_VPS 
```
Try login to you vps using private key
```bash
ssh -i ./path-to-your-private-key/name-of-your-private-key USERNAME@PUBLIC_IP_OF_YOUR_VPS 
```


## Usage
### Project Structure

├── ansible.cfg
├── db_tasks
│   ├── database_setup.yml
│   ├── database_user_tasks.yml
│   ├── Ubuntu_database_tasks.yml
│   └── vars
├── inventory
├── main.yml
├── README.md
├── ssh-keys
│   ├── id_rsa
│   └── id_rsa.pub
└── web-server_tasks
    ├── apache-conf
    └── server.yml

> **Note**
> Make sure you have meet the requirement to install this
>

Edit `inventory` put your `PUBLIC_IP_OF_YOUR_VPS`. 
If you have only one vps just put the same IP
```bash
vi inventory
```
Change the repo on the Task Install Laravel Project (find the command `# CHANGE LARAVEL REPO` and change your git repo)
```bash
vi web-server_tasks/server.yml
```
If you want to chnage apache configuration go to `web-server_tasks/apache-conf/my-app.conf.j2` (Optional)
```bash
vi web-server_tasks/apache-conf/my-app.conf.j2
```

Run The Playbook
```bash
ansible-playbook main.yml
```
To check your dataabse you can check on this file `db_tasks/vars/group_vars/all.yml`
```bash
cat db_tasks/vars/group_vars/all.yml 
```


## Contributing
Pull Request are open for any improvement

## License 

[MIT](https://choosealicense.com/licenses/mit/)