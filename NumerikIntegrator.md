# Numerik İntegratör

`Boost` kütüphanesine dahil edilen ordinary differential equation solver olarak tabir edilen `odeint` sistemin numerik integratörüdür.

Numerik integratör sistemde gelecek versiyonlarda özellikler eklenecek şekilde kodlanmıştır. Şu anda kullanılan integratör **adaptif integratör**dür.

``` C
integrate_adaptive( stepper_controlled , *this , x , 0.0 , step_time , getDT() , observer );
```
Genel adaptif integratör dökümantasyonu için:
[Boost / Integrate functions](http://www.boost.org/doc/libs/1_55_0/libs/numeric/odeint/doc/html/boost_numeric_odeint/odeint_in_detail/integrate_functions.html) kısmına bakılabilir. Adaptif geliştirme bu konunun kapsamına girmektedir.<sup>1</sup>

* * *

### Stepper

Başlı başına integratörler hiçbir anlam ifade etmemekte olup integrasyonların alındığı aralıkları düzenleyen bu aralıklarda her hesaplamanın sonucunu bize geri döndüren bir yapıya ihtiyaç vardır, bu yapılar **stepper** olarak adlandırılırlar. Bu sistemde **controlled stepper** kullanılmıştır. Bu stepper birim zamanda hata aralığının içinde kalan her değer için integrasyon aralığını düşürür ve daha doğru sonuçlar vermeye çalışır. Buna rağmen adım sayısı verilen aralıkta değişmez, hata artarsa ve adımlar iterasyona yetmeyecek duruma gelmeye başlarsa adım genişliğini arttırır.

``` C
auto stepper_controlled = make_controlled( 1E-12 , 1E-12 , runge_kutta_dopri5< state_type >() );
```
**Railpower** projesinin sürümlerinde ilerleme kaydedildikçe diğer stepperların kullanımı da dahil edilecektir.

Stepper **Dormand-Prince** metodunu kullanmaktadır 5. dereceden çözüm üretmektedir.

Şu anda yukarıda verilen kod örneğinde görüldüğü üzere kontrollü stepper kullanılmıştır. Stepper'ın ilk argümanı **absolute error(mutlak hata)**, ikinci argümanı **relative error(bağıl hata)** olarak belirlenmiştir ve değerleri `1E-12`dir.
