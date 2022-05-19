> Rough Note. Probably tidy up later or never.

_______________

creating and launch ec2 instance

- creating a new aws account and linked to local indonesia digital bank.
- enabling the `ap-southeast-3` (jakarta region) and take several minutes to be enabled.
- the url to ec2 ap-southeast-3 : https://ap-southeast-3.console.aws.amazon.com/ec2/v2/home?region=ap-southeast-3
- click launch instance button
- name the ec2 instance (i named it dtc-mlops)
- select ubuntu and the AMI (amazon machine image) with `Ubuntu Server 22.04 LTS (HVM), SSD Volume Type`, architecture `x64-bit (x86)`
- the instance type: `t3.xlarge 4vCPU 16GiB Memory` (t2.xlarge isn't available in jakarta region at the time)
- I dont have key pair at the time and I create it for the first time. I named the keypair with my laptop name. I use `RSA` type and `.pem` format. it will download the key in the browser and make sure the new created key pair is selected for the key pair option.
- make sure to put the .pem file in your .ssh directory in n your machine
- leave the network setting section to default
- in configure storage section, set to `30 GiB gp2` (30GiB still in free-tier eligible)
- leave advanced details to default
- at summary section, make sure to run just 1 instance
- check summary info and everything else if it correct for your need.
- ready? click launch instance!
- after it launched, click that instance ID link to redirect you the instance list page
- check if the server is running

_________

login to instace via ssh

- open gitbash 
- `ssh -i ~/.ssh/yourpem.pem ubuntu@xxx.xxx.xxx.xxx`
- enter and voila! you are in the VM
- the xxx.xxx.xxx.xxx is your instance public IPv4 address

- in the gitbash, type: `nano .ssh/config`. add this to last line:

```
Host dtc-mlops
    HostName xxx.xxx.xxx.xxx
    User ubuntu
    IdentityFile c:/Users/yourusername/.ssh/yourpemname.pem
    StrictHostKeyChecking no
```

- now login to vm with ssh is easy as typing: `ssh dtc-mlops`

___________

installing anaconda

- login to vm
- check the anaconda latest linux installation at https://anaconda.com/products/distribution#Downloads or https://repo.anaconda.com/archive/ 
- my latest at the time: https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh
- type: `wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh`
- type: `bash Anaconda3-2022.05-Linux-x86_64.sh`
- the above command will open installation interface like toc toa, instalation path, confirmation by typing yes and leave everything to use default. make sure to confirm yes to init anaconda when shell opened later. this will takes effect when you reopen shell by logout and login back with ssh.

___________

installing docker

- `sudo apt install docker.io` or `sudo apt update` first
- check `https://github.com/docker/compose/releases` and find latest for linux
- i got `https://github.com/docker/compose/releases/download/v2.5.1/docker-compose-linux-x86_64` at the time.
- create `~/soft` directory
- download docker-compose inside soft directory: `wget https://github.com/docker/compose/releases/download/v2.5.1/docker-compose-linux-x86_64 -o docker-compose` 
- make it executable: `chmod +x docker-compose`
- back to home dir
- `nano .bashrc`
- add this to last line: `export PATH="${HOME}/soft:${PATH}"`
- build: `source .bashrc`
- confirm it installed: `which docker-compose`
- test docker by: `sudo docker run hello-world`

______

adding docker command to group to avoid typing sudo every single time

- guide ref: https://docs.docker.com/engine/install/linux-postinstall/
- `sudo groupadd docker`
- `sudo usermod -aG docker $USER`
- `newgrp docker`
- try again test docker without sudo: `docker run hello-world`

______

- `git clone https://github.com/DataTalksClub/mlops-zoomcamp.git`
-  install `SSH Remote` extension in VSCODE
- click lightning icon left-bottom screen and start to connect with available ssh profile (dtc-mlops)
- open terminal in the new opened VSCODE window and you will use the logged ssh CLI
- when you click open folder in the vscode it will list available folder in your vm home.

____

- `mkdir notebooks`
- `cd notebooks`
- run `jupyter notebook`
- you may see address similar like `http://localhost:8888/?token=cede973cfed363f828895286649dbbdf2e7a95ad5288a3a5` that we will open later in OUR LOCAL BROWSER?!
- in your vm session vscode, there is a PORTS tab next to the TERMINAL tab when you open terminal.
- click it and forward port to example `8888`
- now the above link can be opened in local browser.

____________

IMPORTANT!

Stop your instance (not reboot), and start it when you need it