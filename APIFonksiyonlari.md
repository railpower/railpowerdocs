# API Fonksiyonları

``` c
int initCore();
```
Simülasyon süresince gerekli olacak olan nesnelerin hafızada yerini ayırır.

``` c
int mapPointers();
```
Tüm fiziksel nesne ekleme/çıkarma işlemlerinden sonra hafızadaki nesnelerin pointerlarını kullanılır hale getirir.
``` c
int addVehicleToSim(int ttype, double mass, double pos, double velo, double acce);
```
+ *int ttype* : Araç tipini belirtir.
+ *double mass* : Araç kütlesini belirtir. **(kg)**
+ *double pos* : Aracın ilk iterasyona başlamadan önceki uzlamsal konumunu belirtir. **(m)**
+ *double velo* : Aracın ilk iterasyona başlamadan önceki hızını belirtir. **(m/s)**
+ *double acce* : Aracın ilk iterasyona başlamadan önceki ivmesini belirtir. **(m/s<sup>2</sup>)**

Sisteme araç ekler.

**NOT: ** Bu fonksiyon çağrısından sonra tüm pointerlar `mapPointers` yardımıyla map edilmelidir.
``` c
int addCouplingToSim(double frontDistRefToCoupling, double rearDistRefToCoupling, double tensionDistance, bool nullify);
```
+ *double frontDistRefToCoupling* : öndeki aracın orta noktasının couplinge olan uzaklığı
+ *double rearDistRefToCoupling* : arkadaki aracın orta noktasının couplinge olan uzaklığı
+ *double tensionDistance* : iki araç arasında kuvvet aktarımı olmayan en kısa uzaklık
+ *bool nullify **(opsiyonel)*** : NULL PTR tipinde bir coupling ekler. Test durumlarının gözetimi içindir önerilmez.

Sisteme bağlantı ekler.

**NOT: ** Bu fonksiyon çağrısından sonra tüm pointerlar `mapPointers` yardımıyla map edilmelidir.
``` c
int addForce(int vehIndex, double startTime, double stopTime, double forceValue);
```
+ *int vehIndex* : kuvvetin uygulanacağı aracın eklenme sırasına göre(FILO) indeks numarasını belirtir.
+ *double startTime* : kuvvetin integrasyon süresi boyunca hangi saniyeden itibaren uygulanacağını belirtir.**(s)**
+ *double stopTime* : kuvvetin uygulanmasının integrasyon süresi boyunca hangi saniyede sonlanacağını belirtir.**(s)**
+ *double forceValue* : kuvvetin değerini belirtir **(N)**

Sisteme kuvvet ekler.

**NOT: ** Bu fonksiyon çağrısından sonra tüm pointerlar `mapPointers` yardımıyla map edilmelidir.
``` c
int setMainCouplerSpringConstant(int coupIndex, double sprConst);
```
+ *int coupIndex* : spring sabitinin ekleneceği aracın indexini belirtir.
+ *double sprConst* : spring sabitini belirtir.

Spring sabitini set eder.

***Spring sabiti default olarak `1e8`dir.***

``` c
int setCouplerDampingConstant(int coupIndex, double dmpConst);
```
+ *int coupIndex* : damping sabitinin ekleneceği aracın indexini belirtir.
+ *double dmpConst* : damping sabitini belirtir.

Damping sabitini set eder.

***Damping sabiti default olarak `1e6`dır.***
``` c
int setFrontCouplingToVehicle(int vehindex, int coupindex);
```
+ *int vehindex* : öndeki bağlantının set edileceği aracın indexi
+ *int coupindex* : bağlantının indeksi

İndeksi belirtilen araç nesnesinin önündeki bağlantının atamasını yapar.

``` c
int setRearCouplingToVehicle(int vehindex, int coupindex);
```
+ *int vehindex* : arkadaki bağlantının set edileceği aracın indexi
+ *int coupindex* : bağlantının indeksi

İndeksi belirtilen araç nesnesinin arkasındaki bağlantının atamasını yapar.

``` c
int setFrontVehicleToCoupling(int coupindex, int vehindex);
```
+ *int coupindex* : önündeki aracın set edileceği coupling'in indeksi
+ *int vehindex* : set edilecek aracın indeksi

İndeksi belirtilen coupling nesnesinin önündeki aracın atamasını yapar.

``` c
int setRearVehicleToCoupling(int coupindex, int vehindex);
```
+ *int coupindex* : arkasındaki aracın set edileceği coupling'in indeksi
+ *int vehindex* : set edilecek aracın indeksi

İndeksi belirtilen coupling nesnesinin arkasındaki aracın atamasını yapar.

``` c
int linkVehiclesToCoupling(int coupIndex, int frontVehicleIndex, int rearVehicleIndex);
```
Yukarıda belirtilen
`setFrontVehicleToCoupling` ve `setRearVehicleToCoupling` fonksiyonlarını birlikte işler. *Çift yönlü ilişkilendirme yapar.*

``` c
int linkCouplingsToVehicle(int vehIndex, int frontCouplingIndex, int rearCouplingIndex);
```
Yukarıda belirtilen
`setFrontCouplingToVehicle` ve `setRearCouplingToVehicle` fonksiyonlarını birlikte işler. *Çift yönlü ilişkilendirme yapar.*

``` c
int setDt(double dt);
```
+ *double dt* : integrasyon adım aralığının değeri

İntegrasyon adım aralığını set eder.

``` c
int prepareSim();
```

İntegratörün gereksinimi olan pointer koleksiyonlarını integratöre verir ve sistemi başlamaya hazır hale getirir.

``` c
int clearVehicles();
```
Tüm araçları sistemden siler.

``` c
int clearCouplings();
```
Tüm bağlantıları sistemden siler.

``` c
int clearForces();
```
Tüm kuvvetleri sistemden siler.

``` c
int clearSimulator();
```
Simülatörü sistemden siler. (Debug amaçlıdır yapılması tasvip edilmez.)

``` c
int runIntegration(double runningTime);
```
+ *double runningTime* : integrasyonun koşulacağı süre

İntegrasyonu belirtilen süre boyunca koşar.

***Default olarak `test.txt` dosyasına çıktıları oluşturmaktadır.***
