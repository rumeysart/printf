# printf
----------------------------------------
Değişken(Variadic) Fonksiyonlar
----------------------------------------

*Argüman sayısı kadar değişken alabilen fonksiyonlardır. C prog.'da değişken fonk, programa esneklik katar. Bir sabit argüman alır ve daha sonra herhangi bir sayıda argüman iletilebilir. 
*Variadik fonksiyon en az bir sabit değişkenden ve ardından son parametre olarak bir üç noktadan (…) oluşur.
________
|Syntax::    int function_name(data_type variable_name, ...);
---------
İletilen bağımsız değişkenlerin değerlerine şu başlık dosyası(kütüphaneyle) erişilebilir: #include <stdarg.h>

***************************
<stdarg.h> şu metodları içerir::
***************************
___________________________
>>va_start(va_list ap, argN)<<        Bu, variadic fonksiyon argümanlarına erişim sağlar. Burada *va_list* variadic fonksiyondaki 
___________________________
son sabit argümanın işaretçisi olacaktır. *argN* variadic fonksiyondaki son sabit argümandır. 
Yukarıdaki variadic fonksiyondan (fonk_adı (veri_tipi değişken_adı,…);), değişken_adı, onu argN yapan son sabit argümandır. Oysa *va_list ap* argN'ye (değişken_adı) bir işaretçi olacaktır.

________________________
>>va_arg(va_list ap, type)<<         Bu, bir sonraki variadic fonksiyon argümanına erişir. *va_list ap* yukarıdakiyle 
--------------------------------------- aynıdır, yani  argN'ye bir işaretçi *type*, *va_list ap*'nin beklenen veri türünü belirtir (double, float, int vb.)  


_________________________________
>>va_copy(va_list dest, va_list src)<<     Bu, variadic fonksiyon argümanlarının bir kopyasını oluşturur.
-----------------------------------------------------
____________________
>>va_end(va_list ap)<<	  Bu, variadic fonksiyon argümanlarının geçişini sona erdirir.
--------------------------------

Burada va_list, va_start, va_arg, va_end ve va_copy'nin ihtiyaç duyduğu bilgileri tutar.

#-----------------------------------------------------------------#

write(1, &"0123456789"[a % 10], 1);
write() fonksiyonu, bir veriyi standart çıktıya yazar. Bu fonksiyon, üç parametre alır:

int fd: Veriyi yazılacağı dosya tanımlayıcısı. Burada, 1 kullanılmıştır ve bu, standart çıktıyı (ekranı) ifade eder.

*const void buf: Yazılacak veri. Burada, &"0123456789"[a % 10] ifadesi kullanılmıştır. Bu ifade, "0123456789" dizisinin a % 10 indeksine göre elemanının adresini verir. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade "4" karakterinin adresini verir.

size_t count: Yazılacak verinin boyutu. Burada, 1 kullanılmıştır ve bu, yalnızca bir karakter yazılacağını ifade eder. Bu ifade, değişken a'nın mod 10 (yani son basamağı) ile işaretli rakamı yazar. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade 4 rakamını yazar.

buf parametresi, yazılacak verinin adresini belirtir. Bu parametre, bir void * (gösterici) türündedir ve yazılacak verinin adresini içerebilir. Örneğin, bir karakter dizisi için kullanılabilecek bir ifade &"hello" şeklinde olabilir ve bu ifade, "hello" dizisinin adresini verir.

Bu kod bloğunda, &"0123456789"[a % 10] ifadesi kullanılmıştır ve bu ifade, "0123456789" dizisinin a % 10 indeksine göre elemanının adresini verir. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade "4" karakterinin adresini verir.

Bu ifade, write() fonksiyonunun buf parametresine geçirilerek, standart çıktıya yazdırılır. Örneğin, eğer a değişkeninin değeri 1234 ise, bu ifade write(1, &"4", 1) şeklinde kullanılır ve 4 rakamı ekrana yazdırılır.*

