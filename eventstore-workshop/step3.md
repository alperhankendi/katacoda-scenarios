### EventStore konfigurasyonu

`cat >> /etc/eventstore/eventstore.conf
IntIp : 0.0.0.0
ExtIp : 0.0.0.0
RunProjections: ALL
ClusterSize: 1`{{execute}}

`systemctl restart eventstore.service`{{execute}}

