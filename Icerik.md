# İçerik

Bu bölümde sistemin bilimsel içeriği oluşturulacaktır. Sistemin çalışma prensiplerine değinilecek ve çıktıları gözlenecektir.

Sistem birçok alt üniteden oluşur. Bu alt üniteler bu bölümde verilecektir, alt üniteler sistemin içinde oluşturulma sırasına göre aşağıdaki gibi sıralanabilir:

* Numerik İntegratör
* Araçlar
* Bağlantılar
* Ana simülasyon

ve bunların dışında sisteme yapılan çağrıların bu katmanlara aktarıldığı
* Runtime Birimi

yer almaktadır.

## Gereçler

Proje genel olarak C++'ta kodlanmıştır.
Çağrılar C çağrısı olup `__cdecl` konvansiyonunu kullanır. `C++11` standardını kullanır. `Boost` kütüphanesinin içine sonradan dahil edilen `ODEINT` integratörü sistemin numerik integratörü olarak görev yapmaktadır.
