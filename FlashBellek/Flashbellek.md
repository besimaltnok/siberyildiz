### Flash Bellek Sorus


**Soru:**

```python

Elimizde bir flash bellek var, içerisindeki resimlerden biri bize lazım.
Toplam Puan:200 Göreve Başla

```

Bu soruyu çözebilmek için;

 * Active NTFS Data Recovery Toolkit isimli aracı kullandık.

Bu aracın kurulumunu yaptıktan sonra, içerisinde bulunan 

 * Active@ File Recovery aracını açıp elimizdeki dosyayı ekledik.
 
<img src="/resimler/ntfs-recovery.png"/>

 Ekldikten sonra içerisinde ki verilerde 3 tane resim dikkatimizi çekti. Bunları içerisinden kurtaıyoruz.
 
<img src="/resimler/filesss.png"/>

url-list.txt içerisinde oltalama sitelerine ait bazı veriler var :D

<img src="/resimler/urlist.png"/>

Ancak aradığımız bu değildi :D 

Kurtardığımız resimleri açtmaya çalıştığımzda açılmadıklarını gördük. Resimleri hex editör ile açtığımızda başlık bilgisinin bozuk olduğunu gördük.

<img src="/resimler/bozukbaslık.png"/>

Bozuk başlık bilgisini düzeltmek için:

```python
 HxD Hex Editör aracı ile bozuk resimi açın. 
 Daha sonra aynı tipte bir resim daha açın (png ise png, jpeg ise jpeg). 
 Çalışan resmin başlık bilgisini alıp, bozuk olan resime ekleyin.
```

Başlık bilgsini düzelttikten sonra **"usom"** resminin exif bilgilerinde flag değerinin olduğunu gördük.

<img src="/resimler/exif.png"/>
