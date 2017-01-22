### Splinter.pcap Sorusu


Bu soruda bize verilen pcap dosyası üzerinde gene bir bilgi sahibi olmak için Protocol Hierarchy üzerinden bilgi elde ediyoruz.

<img src="/resimler/usb.png"/>

Elde edilen bu bilgiler doğrultusunda araştırma yaptığımızda, amacımızın fare hareketlerinin koordinatlarına erişmek olduğunu düşündüm. 

**Bunun için aşağıdaki adımları takip ettm:**

```python
tshark -r splinter.pcap -T fields -e usb.capdata > data.txt

awk -F: 'function comp(v){if(v>127)v-=256;return v}{x+=comp(strtonum("0x"$2));y+=comp(strtonum("0x"$3))}$1=="01"{print x,y}' data.txt > fare.txt

```
Daha sonra en son elde ettiğimiz, fare.txt isimli dosyayı aşağıda belirtildiği gibi **"gnuplot"** ile açıyoruz.

<img src="/resimler/gnuplot.png"/>


Elde edilen bu görüntüyü evirip çevirdğimizde flag karşımıza çıkıyor.

<img src="/resimler/buldum.jpg" width="350" height="300"/>
