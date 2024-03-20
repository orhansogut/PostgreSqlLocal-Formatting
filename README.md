# PostgreSql Local-Formatting Error

## Hata
Hizmetler üzerinden başlatma sırasında verdiği hata <br>
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/7613f571-b58b-4597-8b63-ae75a937351d)

Postgreyi cmd üzerinden başlatmayı deniyoruz.
```shell
pg_ctl -D "C:\Program Files\PostgreSQL\15\data" start
```
_Cmd üzerinde pb_ctl kullanabilmek için ortam değişkenlerine postgreye ait bin ve lib dosya yollarını path'e eklemelisiniz._

- Hataya Ait ekran görüntüsü
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/c8373e14-9bff-4a8a-b229-b132dca748b7)

* Hatamız C:\Program Files\PostgreSQL\15\data yolunda bulunan postgresql.conf içinde bulunan aşağıda belirttiğim kısımlardan kaynaklanıyor.
  * Locale and Formatting bölümü altında bulunan
    - lc_messages = 'Turkish_Turkey.1254'                  
    - lc_monetary = 'Turkish_Turkey.1254'                  
    - lc_numeric = 'Turkish_Turkey.1254'                   
    - lc_time = 'Turkish_Turkey".1254'

## Hata Sebebi
Ülkemizin uluslararası adının Turkey'den Türkiye olarak değişmesinden kaynaklı oluşuyor. Eğer isim değişikliğinden önce postgreyi kurup daha sonra sunucu/bilgisayarınıza güncelleme yaptıysanız bu hatayla karşılaşma şansınız çok yüksek. 

## Hata Çözümü
Öncelikle conf içerisinde elle düzeltme yapmam bende işe yaramadı ve daha farklı hatalara sebep oldu. Bu kısımda düzenleme yapmanızı pek önermem.
### 1.Adım
https://www.microsoft.com/en-us/download/detaLoils.aspx?id=41158 Adresine giderek Locale Builder uygulamasını indiriyoruz.
### 2.Adım
Kurulumu tamamladıktan sonra aşağıdaki gibi bir ekran gelecek. 
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/9f80ade0-5cfb-4736-86c7-3e8255fe04c7)
### 3.Adım
İleri diyerek Türkiye olarak eklenmiş dil paketininin detayına geçiyoruz. Aşağıdaki gibi bir ekran gelmeli.
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/f37c2bde-e051-4184-9808-eeab7f5da656)
### 4.Adım
Burada English names ve Native names sekmeleri altında bulunan Region name inputunu değiştiriyoruz. Burada sizde hatadan önceki dil paketinize göre düzenleme yapabilirsiniz. Bende daha önce Turkey olarak çalışan set Türkiye olunca bozulduğu için Turkey olarak bir paket oluşturuyorum.
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/0c0f48d4-56ad-43d4-b1a5-f2e3e5a9c833)
### 5.Adım
Son olarak Build sekmesi altında bulunan Build Locale Installer'ı kullanarak bir msi uzantılı çıktı alıyoruz. Bu çıktıyı bilgisayarımıza kurduktan ve bilgisayarı yeniden başlattıktan sonra hata çözülmüş olacaktır.
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/0343c040-7762-4297-b358-2bde86b7fcb7)
### Sonuç
![image](https://github.com/orhansogut/PostgreSqlLocal-Formatting/assets/89242655/0a82448a-19d8-4002-8da2-6eae54484bf7)
Buradaki çözüm benim başıma gelen bir soruna ait özel bir çözüm olabilir, benzer bir hatayı yaşadıysanız ve farklı bir çözüm ile sorunu çözdüyseniz bana da iletirseniz sevinirim ve öğrenmek isterim. <br> <br>
Mail Adresim : okurkodlar@gmail.com


