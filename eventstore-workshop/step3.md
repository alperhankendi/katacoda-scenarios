### EventStore konfigurasyonu

`echo '
IntIp : 0.0.0.0
ExtIp : 0.0.0.0
RunProjections: ALL
ClusterSize: 1
' > /etc/eventstore/eventstore.conf`{{execute}}

`systemctl restart eventstore.service`{{execute}}

