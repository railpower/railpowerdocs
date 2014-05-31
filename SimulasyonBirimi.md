# Simülasyon Birimi

Simülasyon birimi `test.txt` dosyasına her iterasyon sonrası:
+ İterasyon aralığının yazılıma ait iç iterasyon zamanını
+ i. aracın ivmesini
+ i. aracın hızını
+ i. aracın pozisyonunu

yazdırmaktadır. İlerleyen versiyonlarda dosyanın adının da kullanıcıya bağlı olması sağlanacaktır.

Bu iterasyon sonrası veriler matlab'da görselleştirilebilir ve doğruluğu kontrol edilebilir.
**Matlab**da sadece lokomotifin olduğu bir test görsellemesi aşağıdaki şekilde oluşturulabilir:

``` matlab
    A = importdata('test.txt');
    disp('DATA IMPORTED');

    figure('name', 'ACCELERATION');
    slice_acce = [A(:,1), A(:,2)];
    plot(slice_acce(:,1), slice_acce(:,2), 'r');
    grid on;
    disp('ACCELERATION PLOT');

    figure('name', 'VELOCITY');
    slice_velo = [A(:,1), A(:,3)];
    plot(slice_velo(:,1), slice_velo(:,2), 'm');
    grid on;
    disp('VELOCITY PLOT');

    figure('name', 'POSITION');
    slice_pos = [A(:,1), A(:,4)];
    plot(slice_pos(:,1), slice_pos(:,2), 'b');
    grid on;
    disp('POSITION PLOT');
```
