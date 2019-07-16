İlk EventStore işlemi olarak bir event'in nasıl eventstream olarak yazıldığını göreceğiz. 

Eventstore kayıt edeceğimiz ilk event aşağıdaki json örneğinde görüldüğü gibi "data" elementi içinde yer almaktadır. EventType, mesajın tipi; EventId, mesajın tekil id sini temsil etmektedir. 

 `cat example/test-event.json`{{execute}}
EventStore 2113 portundan yayın yapan Rest API aşağıdaki şekilde event kayıt edilmektedir.

 `curl -i -d "@example/test-event.json" "http://127.0.0.1:2113/streams/newstream" -H "Content-Type:application/vnd.eventstore.events+json"`{{execute}}

 Dosyada yer alan mesaj EventStore'a "newStream" id si ile eklenmiştir.