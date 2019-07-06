#### İşletim sistemi paketini bulmak

Başlangıç olarak kullandığınız linuz sürümüne göre EventStore package yönetim sisteminden özelleştirebilirsiniz.
(https://packagecloud.io/EventStore/EventStore-OSS/install)


#### İşletim sistemi paket repo eklemek.

İlk adım olarak EventStore paket ilgili dağıtım deposunu işletim sisteminize eklemeniz gerekmektedir.
`curl -s https://packagecloud.io/install/repositories/EventStore/EventStore-OSS/script.deb.sh | sudo bash`{{execute}}

Dağıtım deposunun listeye eklendiğini 
`clear&&cat /etc/apt/sources.list.d/EventStore_EventStore-OSS.list`{{execute}} kontrol edebilirsiniz.
