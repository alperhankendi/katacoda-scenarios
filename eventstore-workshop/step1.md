To start,

`curl -s https://packagecloud.io/install/repositories/EventStore/EventStore-OSS/script.deb.sh | sudo bash`{{execute}}

#### Health Check

Once started, you can get the status of the cluster with `apt-get install eventstore-oss`{{execute}}

`systemctl start eventstore.service`{{execute}}

`systemctl status eventstore.service`{{execute}}

`cat << EOF >> /etc/eventstore/eventstore.conf
IntIp : 0.0.0.0
ExtIp : 0.0.0.0
EOF`{{execute}}

`sudo ufw allow 2113` {{execute}}

`systemctl restart eventstore.service`{{execute}}


https://[[HOST_SUBDOMAIN]]-2113-[[KATACODA_HOST]].environments.katacoda.com/web/index.html
