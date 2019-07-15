### EventStore konfigurasyonu

EventStore localhost dışında erişime açmak için konfigurasyon değişikliği yapılıyor. İç ve dış ip adreslerine 0.0.0.0 verilerek eventstore dışarıdan erişim sağlanıyor.

`echo '
IntIp : 0.0.0.0
ExtIp : 0.0.0.0
RunProjections: ALL
ClusterSize: 1
' > /etc/eventstore/eventstore.conf`{{execute}}

`systemctl restart eventstore.service`{{execute}}