### Holowy Conz - Holowy Conz den beklediğimiz mesaj geldi, acaba nedir?

Bu soruda kullanılan araç
 * Stegsolve
 
**Aracın Kurulumu ve Kullanımı:**

```python
wget http://www.caesum.com/handbook/Stegsolve.jar -O stegsolve.jar
java -jar stegsolve.jar
```

Resim açıldıktan sonra, analiz gerçekleştirildiği zaman aşağıdaki görselde tanımlanan **QR kod** elde edilmiştir.

<img src="/resimler/stegsolve.png"/>

QR kod okutulduğunda, **siberstar** adı elde edilmekteydi.

Bundan sonraki süreç internet üzerinden araştırma yapmak üzereydi. Bu soru için twitterda açılmış bir kullanıcı mevcuttu.

**Hesap:**
 * https://twitter.com/siber_star
 
<img src="/resimler/twitter.png" width="500" height="300" />

Bu hesap üzerinde atılan twitte bulunan mesajı elde etmek için google üzerinden **"Twitter Hidden Message"** diye arama yaptığınızda bir site tespit ediliyor.

<img src="/resimler/google.png"/>

**Site:**
 * http://holloway.co.nz/steg/
 
Site içerisinde twitter dan elde edilen mesaj girildiğinde aşağıdaki veri elde ediliyor:
 * freenode cyb3rst4rs    
 
<img src="/resimler/hidden.png"/>

 
Bundan sonra internette **"freenode"** diye arama yapıldığında ilk sırada iki tane 

 * https://freenode.net/
 * https://kiwiirc.com/client/irc.freenode.net
 
Bu sitelerden ikincisine girip twitterdan elde edilen bilgiler ile kanala giriş yapıldığında size yarışmayaı düzenleyen ekip tarafından hazırlanan bot ile flag verilmekteydi.

<img src="/resimler/freenode.png"/>

