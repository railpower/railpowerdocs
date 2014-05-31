# Bağlantılar

Bağlantılar diğer adıyla **coupling** yapıları iki aracı birbirine bağlanmaya ve/veya araçlar arasında güç aktarmaya yarayan sistemlerdir.
Bir coupling'in genel yapısı aşağıdaki şekildedir:

![Temel coupling yapısı](images/coupling.png "Temel coupling yapısı")

#### Bağlantı sabitleri

+ Damping sabiti (bağlantı yayının/yaylarının damping sabiti)
+ Spring sabiti (bağnatı yayının sabiti)

#### Kuvvet
Bağlantının aktardığı kuvveti bulmak için çeşitli denklemler bulunmaktadır. Bu projede aşağıda belirtilen bağlantı kuvveti hesaplama denklemi kullanılmıştır.<sup>3</sup>
![Bağlantı Kuvveti](images/cfformul.png "Bağlantı kuvveti hesaplama denklemi")
`m` ve `a` sırasıyla kütle ve ivmeyi, `c` damping sabiti, `k` spring sabitidir. Denklemin sağ el tarafı net kuvvet olarak coupling kuvvetini bize vermektedir.
![Bağlantı Kuvveti](images/damping.png "Bağlantı kuvveti ile ilgili bir çizim")
Bağlantı kuvvetinin integrasyon sürecinde simülasyonun bir sonraki adımı kuvvetin hesaplama adımından her zaman bir `dt` hesabı kadar önde olması gerekmektedir.<sup>4</sup>
