Bir önceki adımda eklediğimiz "newStream" idli event okumak için aşağıdaki komutu çalıştırılmalıdır.

 `curl -i -H "Accept:application/vnd.eventstore.atom+json" -H "authorization: Basic YWRtaW46Y2hhbmdlaXQ=" "http://127.0.0.1:2113/streams/newstream"`{{execute}}

EventStore 'un REST API si ile /streams/{StreamId veya AggregateId} eklenerek ilgili steam eklenen tüm event elde edebiliriz.