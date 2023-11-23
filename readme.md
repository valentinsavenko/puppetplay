# setup
both up all compoments with docker-compose
```bash

docker-compose up -d

# or
 docker-compose down && sudo rm -rf -d ./puppet* && docker-compose up
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

## check puppetserver/webinterface is running
```bash

docker exec -it puppetplay-puppet-1 bash
```
in the container

```bash
netstat -tulpen
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name    
tcp        0      0 0.0.0.0:8140            0.0.0.0:*               LISTEN      999        55596      -                   
```

tunnel the puppetserver port to the host
```bash
