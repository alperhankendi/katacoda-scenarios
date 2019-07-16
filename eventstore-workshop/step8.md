
Projection örneği için öncelikle birkaç veri ekleyelim.

Aşağıdaki komutlar ile sepetlere ürünler ekleyelim. shoppingCart-{guid} li  her gibi ayrı sepet oluşturuluyor. buradaki shoppingCart-{guid} her birisi ayrı EventStore da "Stream" olarak eklenmektedir.

`curl -i -d "@example/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1164.json" "http://127.0.0.1:2113/streams/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1164" -H "Content-Type:application/vnd.eventstore.events+json"`{{execute}}

`curl -i -d "@example/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1165.json" "http://127.0.0.1:2113/streams/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1165" -H "Content-Type:application/vnd.eventstore.events+json"`{{execute}}

`curl -i -d "@example/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1166.json" "http://127.0.0.1:2113/streams/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1166" -H "Content-Type:application/vnd.eventstore.events+json"`{{execute}}

`curl -i -d "@example/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1167.json" "http://127.0.0.1:2113/streams/shoppingCart-b989fe21-9469-4017-8d71-9820b8dd1167" -H "Content-Type:application/vnd.eventstore.events+json"`{{execute}}

###İlk EventStore projection yaratalım
```
fromAll()
.when({
    $init: function(){
        return {
            count: 0
        }
    },
    ItemAdded: function(s,e){
        if(e.body.Description.indexOf("Xbox One S") >= 0){
            s.count += 1;
        }
    }
})
```
Yaratacağımız ilk projection gelen tüm shoppingCart streamlerine eklenen ürünlerden "XBox One S" ürününün sepet adetleri olacaktır.

Projection REST API ile aşağıdaki komut ile yaratılmaktadır. Aynı şekilde EventStore UI üzerinden yaratılabilmektedir.

`curl -i --data-binary "@example/xbox-one-s-counter.json" http://localhost:2113/projections/continuous?name=xbox-one-s-counter%26type=js%26enabled=true%26emit=true%26trackemittedstreams=true -u admin:changeit`{{execute}}


### Yarattığımız projection üzerinden sorgulamak

Sepette ekli "Xbox One S" ürünleri REST API üzerinden sorgulayabiliriz.
`curl -i http://localhost:2113/projection/xbox-one-s-counter/state`{{execute}}

