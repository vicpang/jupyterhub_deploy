# jupyterhub_deploy

## environment
	1 install docker 
	2 install anaconda
	3 create env: conda create -n jup python=3.5
	4 install jupyterhub:
		 conda install -c conda-forge jupyterhub
		 conda install notebook
		 jupyterhub -h
	->make sure jupyterhub is readable and executable by all users
	5 install spawner
		pip install dockerspawner
	6 install certbot
		 sudo apt-get install certbot 
## running
	1. better run hub as root
	2. generate ssl key
		openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout jupyterhub.key -out jupyterhub.crt
	3. create certificate
		 sudo certbot certonly --standalone -d localhost.tld
	4. config
		jupyterhub --generate-config
	5. grant access for nonroot
		sudo setcap 'cap_net_bind_service=+ep' `which node`