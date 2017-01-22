### USOM-FORENSICS sorusu

Bu soruda bizlere bir dosya verilmişti.

* **Dosya ismi :** usom-forensics

Bu gibi sorularda ilk olarak yapmamız gereken şey dosya hakkında bilgi almak için "**file**" komutunu kullanmaktır. Bizde bu soruda bu komu ile dosyayı incelediğimizde aşağıdaki gibi bir sonuç ile karşılaştık.

* **Komut:** file usom-forensics

<img src="/resimler/file.png" />


Bu bilgiden sonra "mv" komutu ile dosyanın uzantısını değiştiriyoruz.

* **Komut:** mv usom-forensics usom-forensics.7z

Daha sonra "7za" aracı ile dosya içerisindeki veriyi çıkartıyoruz.

* **Komut:** 7za e usom-forensics.7z

<img src="/resimler/7ze.png" />

İçerisindeki veri tekrar file komutu ile incelendiğinde bir data olduğu bilgisini alıyoruz. Bu işlemden sonra volatility aracı ile incelemeye alıyoruz.

Bunun için ilk olarak image hakkında bilgi almak için aşağıdaki komutu kullanıyoruz.

* **Komut:** volatility -f usom-forensics imageinfo
 - "-f": incelenecek dosya tanımlanır.
 
RAM imajı analizi sorularında genelde ilk yapılması gereken şey, "**pslist**" komutu ile çalışan işlemleri listelemek ve sistemde o anda ki işleyiş hakkında bilgi sahibi olmaktır.

* **Komut:** volatility -f usom-forensics --profile=Win7SP0x86 pslist

<img src="/resimler/pslist.png" />

Bu çıktı sonucunda dikkat çeken işlemler:

 - mspaint.exe
 - notepad.exe
 - lsass.exe
 
 mspaint.exe dumpı alınıp gimp ile incelenip üzerine çalışılan resim üzerinden bilgi elde edilebilir. CTF lerde bu tarz sorular görüyoruz. Ancak böyle bir inceleme sonucunda aşağıdaki gibi bir sonuç ile karşılaştık.
 
 <img src="/resimler/flagdegil.jpg" />

Zaten bize sorulan şey bir parolaydı. 

* Soru: Zararlı bir hacker'ın bilgisayarından veri elde ettik, içerisindeki hackerin şifresini bulabilir misin ?

Bu nedenle volatility içerisinde kullanılabilen hashdump parametresi de denenebilirdi. Ancak burda da tatmin edici bir sonuç yoktu.

"pslist" dışında en çok işinize yarayacak bir diğer parametre "**filescan**" parametresidir.

Dosya üzerinde "**filescan**" çalıştırıldığında flag adı ile bazı dosyalar olduğu gözlemlenmiştir.

* **Komut:** volatility -f usom-forensics --profile=Win7SP0x86 filescan

 <img src="/resimler/filescan.png" />


Bu veriler "**dumpfiles**" parametresi ile elde edilebiliyordu. 

 <img src="/resimler/dumpfiles.png" />

Elde edilen bu verilerden **flag.txt** incelendiğinde lsass dump dosyasına ait bir link elde ediliyordu.

 <img src="/resimler/flag.png" />

Bu dump mimikatz ile incelendiğinde parola elde edilebiliyordu.

**Adımlar:** 

 * privilege::debug
 * sekurlsa::minidump lsass
 * sekurlsa::logonPasswords

 <img src="/resimler/pass.png" />


