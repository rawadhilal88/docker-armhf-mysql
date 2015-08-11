This docker file enables you to easily configure a mysql docker container.
<br/>
To run it call:
<br/>
<code>
docker run --name mysql -e MYSQL_ROOT_PASSWORD=<password> -v /opt/mysql/data:/var/lib/mysql -p 3306:3306 eagos/armhf-mysql 
</code>

<br/>
The following is an example of a systemd service.
```
[Unit]
Description=Docker apache server.
After=docker.service

[Service]
ExecStartPre=-/usr/local/bin/docker rm mysql 
ExecStart=/usr/local/bin/docker run --name mysql -e MYSQL_ROOT_PASSWORD=<password> -v /opt/mysql/data:/var/lib/mysql -p 3306:3306 eagos/armhf-mysql
Restart=on-failure
TimeoutSec=20

[Install]
WantedBy=multi-user.target
```
