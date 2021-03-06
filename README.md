[![Build Status](https://travis-ci.com/MolSSI/covid_apis.svg?branch=master)](https://travis-ci.com/MolSSI/covid_apis)
[![codecov](https://codecov.io/gh/MolSSI/covid_apis/branch/master/graph/badge.svg)](https://codecov.io/gh/MolSSI/covid_apis)

MolSSI COVID APIs
========================

Description

How to run and use for development:
===================================

### 1- Install Python requirements:

Run in shell, create python env, and install requirements:

```bash
conda create -n covid_apis 
conda activate covid_apis
pip install -r requirements.txt
```


### 2- Install JavaScript requirements:

Next, install Node (front-end), and install JS requirements, 
which will be fetched from package.json automatically. In Ubuntu:

```bash
sudo apt-get install nodejs
cd covid_apis/app/static
npm install
```

### 3- Database setup

1. Install mongodb based on your operating system from 
https://docs.mongodb.com/guides/server/install/

2. Create a `covid_apis/.env` file, and add your DB URI to the config file:
```.env
MONGO_URI='mongodb://usr_username:user_password@localhost:27017/covid_apis_db'
```

Replace `user_username` and `user_password` with your own values from your installation. 
You **don't** have to create a database after your install mongodb because the application will do
 it later.


Note: In the future when you need to, add PUBLICLY shared environment attributes to `.flaskenv` file, with key values that will be exported to the environment (dev, prod, etc).
Use `.env` file for private variables that won't be shared or pushed to Github. Note that `.env` overrides `.flaskenv`, and both override `config.py`.



### 4- Run the local server

To run the website locally, use: 

```bash
flask run
```


## To Use Docker Compose (instead of the above steps):

Run docker-compose directly, or optionally, change any desired environment variables by creating 
a `.env` file which will be read automatically by docker-compose.

** It is very important to make sure that the shared folder has the right user NOT root owner. **

```bash
# create the host volume folder with non-root access
mkdir docker_data
chown -R myUser:myUse docker_data
# clean unused docker images and containers
./dockerclean.sh
# build and run containers
docker-compose up --build 
```

## More resources:

1. For Docker deployment config example, check this
https://www.digitalocean.com/community/tutorials/how-to-set-up-flask-with-mongodb-and-docker

2. A service file has been included for getting this running as a service. See this url for more details
https://community.hetzner.com/tutorials/docker-compose-as-systemd-service 
