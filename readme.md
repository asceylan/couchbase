

# Kodluyoruz-Trendyol System_Infra Bootcamp Database  Case

Bu case de Couchbase kurulumu ve 2.ci bir node eklenip Rebalance işlemlerinin gerçekleştirilmesi yapılmıştır.

Kurulumla ve sistemin düzeniyle  ilgili kanıtlar screenshots klasörün dedir.

Docker Üzerinden kurulum yapılmıştır.


 

    docker run -d --name db1 -p 8092:8091 couchbase
    docker run -d --name db2 -p 8091:8091 couchbase


Couchbase nodelarının birbiriyle iletişimi için Docker iç ağ Iplerine bakılmıştır.

    [root@localhost ~]# docker inspect --format '{{ .NetworkSettings.IPAddress }}' db1
    172.17.0.2
    [root@localhost ~]# docker inspect --format '{{ .NetworkSettings.IPAddress }}' db2
    172.17.0.3

Docker kurulumu yapıldıktan sonra 2.node için 

> Join Existing Cluster    

Seçeneği kullanılmış ve  172.17.0.2:8092 adresindeki mevcut asimceylan cluster ına eklenmiştir.

Ardından `Rebalance` işlemi gerçekleştirilirken hata alınmıştır.


