Bu seneryoda  (Ges)EventStore (https://eventstore.org) nasıl kurulduğunu öğreneceğiz.  

EventStore, verilerinizi zaman serisi içinde bir dizi değişmez(immutable) etkinlik(events) olarak depolar ve eventsourced uygulamalar oluşturmayı kolaylaştırır.

##Yüksek Kullanılabilirlik (High Availability)
Event Store, aynı verileri içeren bir node kümesi(node cluster) olarak çalışabilir. Event Store cluster node larından en az yarısının canlı ve cluster bağlı olması konuşuyla yazma işlemi için kullanılabilir durumda kalır.

## Projeksiyon (Projections)

Projection, event lerin yazıldığı gibi tepki vermenize ve ilginç kombinasyonlar oluştuğunda yeni eventler oluşturmanıza olanak sağlar. Tarihsel veriler üzerinden ve geleceğe yönelik geçici korelasyon sorguları yazmak için aynı modeli kullanabilirsiniz. Event Store üzerinde bulunan tüm eventler ile ve geri giderek (zaman makinası gibi) tekrar çalıştırarak farklı veri modelleri oluşturabilinir.

## Performans (Great Performance)

Performans konfigürasyon ve kullanım şekillerine bağlı olmasına rağmen, saniyede yaklaşık 15.000 yazma ve saniyede 50.000 okuma işlemi yapılabilmektedir.

## Açık kaynak kodlu (Open Source)

Tek node veya nodelardan oluşan bir cluster ücretsiz olarak kullanabilirsiniz. Ticari destek servisi ücretlidir.

# Kullanıcı arayüzü (Client Interface)

EventStore, kullanım durumlarının çoğu için yeterince hızlı olan AtomPub (https://tools.ietf.org/html/rfc5023) protokolünü temel alan yerel bir HTTP arayüzüne sahiptir. Yüksek performanslı kullanım için .NET, Akka ve Erlang için yerel sürücüler vardır.