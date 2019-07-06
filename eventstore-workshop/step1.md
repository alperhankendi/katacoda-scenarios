#### İşletim sistemi paketini bulmak

Başlangıç olarak kullandığınız linuz sürümüne göre EventStore package yönetim sisteminden özelleştirebilirsiniz.
(https://packagecloud.io/EventStore/EventStore-OSS/install)


#### İşletim sistemi paket repo eklemek.

İlk adım olarak EventStore paket ilgili dağıtım deposunu işletim sisteminize eklemeniz gerekmektedir.
`curl -s https://packagecloud.io/install/repositories/EventStore/EventStore-OSS/script.deb.sh | sudo bash`{{execute}}

Dağıtım deposunun listeye eklendiğini 
`clear&&cat /etc/apt/sources.list.d/EventStore_EventStore-OSS.list`{{execute}} kontrol edebilirsiniz.

#### EventStore-oss paketini kurulumu

Dağıtım deposunun hazırlanması sonrasında eventstore-oss kurulumu için  `apt-get install eventstore-oss`{{execute}}
çalıştırılmalıdır.

paket kurulumu tamamlandıktan sonra eventStore.service durumunu `systemctl status eventstore.service`{{execute}}
ile kontrol edebilirsiniz.


Servisi çalıştırmak için `systemctl start eventstore.service`{{execute}} kullanabiliriz.


### EventStore konfigurasyonu

`cat >> /etc/eventstore/eventstore.conf
IntIp : 0.0.0.0
ExtIp : 0.0.0.0
RunProjections: ALL
ClusterSize: 1
EOF`{{execute}}


`systemctl restart eventstore.service`{{execute}}

### EventStore UI hazır!!
https://[[HOST_SUBDOMAIN]]-2113-[[KATACODA_HOST]].environments.katacoda.com/web/index.html
