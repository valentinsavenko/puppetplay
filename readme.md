# prerequisites
## install vagrant dependencies
```bash
vagrant plugin install vagrant-docker-compose
   # vagrant plugin install vagrant-vbguest
```

# setup
both up all compoments with docker-compose
```bash

docker-compose up -d

# or
docker-compose up -d

# for volume cleanup
#  docker-compose down && sudo rm -rf -d ./puppet* && docker-compose up
```




## Connect to postgresql
```bash
docker  exec -it puppetplay-postgres-1 bin/bash
``` 


### verify connection to postgresql
connect to postgresql inside of the docker container

```bash
psql -h localhost -U puppetdb
```


```sql
SELECT
   pid,
   datname,
   usename,
   application_name,
   client_hostname,
   client_port,
   backend_start,
   query_start,
   query,
   state
FROM pg_stat_activity
WHERE state = 'active';
```

## check puppetdb-webinterface is running

http://localhost:8080/pdb/dashboard/index.html

## check puppet dashboard is running
Also this dashboard is usefull to check the puppetserver state in general: 
http://localhost:8088/inventory



# vagrant for target nodes
https://developer.hashicorp.com/vagrant/downloads

```bash
export VAGRANT_WSL_ENABLE_WINDOWS_ACCESS="1"
export PATH="$PATH:/mnt/c/Program Files/Oracle/VirtualBox"
"/mnt/c/Users/valen/workspace"
export VAGRANT_WSL_WINDOWS_ACCESS_USER_HOME_PATH=$HOME

```