### EventStore Cluster konfigurasyonu

Eğer EventStore Linux bazlı bir ortama kurulduğunda konfigurasyon dosyası /etc/eventstore/eventstore.conf altında yer almaktadır.


```
IntIp: 10.168.100.115
ExtIp: 10.168.100.115
IntTcpPort: 1111
IntHttpPort: 2113
ExtTcpPort: 1112
ExtHttpPort: 2114
DiscoverViaDns: false
GossipSeed: ['10.168.100.116:2113']
ClusterSize: 3
RunProjections: all
Db: /data/esdb
Index: /data/esdb/index
StatsPeriodSec: 30
```

| Parametre | Açıklama |
| --- | --- |
| IntIp |  Cluster iç iletişim ip adresi |
| ExtIp |  Cluster dış iletişim ip adresi  |
| IntTcpPort | Cluster tcp iç iletişim port  |
| IntHttpPort | Cluster http(Rest API) iç iletişim port  |
| ExtTcpPort | Cluster tcp dış iletişim port  |
| ExtHttpPort | Cluster http(Rest API) dış iletişim port  |
| DiscoverViaDns | DNS ile cluster node keşfedilmesini sağlar.(Default:true)  |
| GossipSeed | Verilen endpoint adreslerinden seed alması sağlanır.(Cluster diğer node larından en az iki tane eklenmesi uygundur.)  |
| ClusterSize | Cluster dahil edilen ve beklenen   node sayısını belirler.Verilen sayı değerinin altına düştüğünde "Close" node birisi otomatik olarak "slave" olarak cluster dahil edilir.  |
| RunProjections | Node üzerinde projection çalıştırır.Default:None  |
| Db | Veritabanı dosyalarının path belirler. |
| Index | Index dosyalarının path belirler. |
| StatsPeriodSec | Node lar arasındaki healty check periyod süresini tanımlar.(Default:5 saniye)  |

EventStore tüm parametreleri görmek için [tıklayın.](https://eventstore.org/docs/server/command-line-arguments/index.html)