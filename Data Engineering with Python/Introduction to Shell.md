# Introduction to Shell

## Manipulating files and directories

- `pwd` *Print Working Directory*: Aktif olan dizinin çıktısını verir.
- `ls` *Listing*: İçerisinde bulunduğunuz dizindeki dosyaların adlarını verir.
- `ls working/dir/to/go`: İleride veya geride bulunan klasörlerdeki içerisindeki dosyaları verir.
- `cd` *Change Directory*: İleri veya geride bulunan klasörlere gitmemize yarar.
- `cd ~`: Home klasörüne gitmemize yarar.
- `cd /`: Root klasörüne gitmemize yarar.
- `ls ~`: Home klasöründeki dosyaları verir.
- `cp dosya1.txt kopya_dosya.txt` *Copy*: Bir dosyanın kopyasını oluşturmamıza yarar.
- `mv dosya1.txt ..` *Move*: Bir dosyanın farklı klasörlere taşınmasını sağlar.
- `mv eski_dosya.txt yeni_dosya_adı.txt`: Bir dosyanın adını değiştirmemize yarar.
- `rm gereksiz_dosya.txt` *remove*: Bir dosyayı silmemize olanak sağlar.
- `mkdir "Dosya adı"` *Make directory*: Yeni bir boş klasör oluşturmamızı sağlar.
- `rmdir "Dosya adı"` *Remove directory*: Bir klasörü silmemize olanak sağlar.

## Manipulating Data

- `cat okunması_gereken_dosya.txt` *Concatenate*: Bir dosyanın içeriğini ekrana yazdırmaya yarar.
- `less okunacak_dosya.txt`: Bir dosyanın ekranda interaktif olarak okunmasını sağlar. **Q** ile çıkış yapılır.
- `head okunacak_dosya.txt`: Bir dosyanın **ilk 10** satırını ekrana getirir.
- `head okunacak_dosya.txt -n 25` *Number of lines*: Bir dosyanın **ilk 25** satırını ekrana getirir.
- `ls -R` *List directory Recursive*: Bir klasörün içerisindeki dosyaları ve alt klasörlerinin dosyalarını ekrana yazdırmamızı sağlar.
- `man help` *Manual*: Bir komutun (burada help komutu) yardım sayfasını getirir.
- `cut -d ; -f 2 okunacak_dosya.csv`: *-d* parametresiyle dosya ayırıcısı olan işareti belirlerken *-f* parametresiyle kaçıncı kolonun (1'den başlar) gösterileceği seçilir.
- `cut -d ; -f 2-5 okunacak.csv`: 2 ile 5. kolonların girdilerini ekrana bastırır.
- `history`: Geçmişte girilen komutları bastırır ve bastırılan komutların satırını `!satır_sayısı_numarası` ile tekrar çalıştırır.
- `grep -c -h -i pattern serkan.txt`: *pattern* girdisini *serkan.txt* dosyası içerisinde arar ve, **-i** parametresi ile büyük-küçük harflerin duyarlılığını engelleriz, **-c** parametresi ile *pattern* ile eşleşen satırların sayısını bastırır, **-h** parametresi ile de birden fazla dosya girdiğimizde eşleşen her satırın başına o dosya adını yazmasını engelleriz.
- `grep -v -l -n pattern serkan.txt`: **-v** parametresi ile eşleşmelerin olmadığı satırları işleme alırız, **-l** parametresi ile eşleşme yapan her satırın dosya adını satır başlarına yazdırırız, **-n** parametresi ile de eşleşme yapılan satır numaralarını satır başına yazdırırız.
- `paste dosya1.csv dosya2.csv`: 2 farklı fakat aynı kolonları bulunduran dosyaları tek bir çıktı olarak vermeye yarar.

## Combining Tools

- `head -n 5 serkan.csv > ilk_bes.csv`: Bu komut ile terminal ekranına bastırmak yerine çıktı olarak **ilk_bes.csv** dosyasının içerisine yazarız.
- `head -n 5 serkan.csv | tail -n 2` *pipe işlemleri*: **serkan.csv** içerisinde bulunan ilk 5 satırı işleme alıp sonrasında gelen komut ile ilk 5 satırın son 2 satırını ekrana bastırırız.
- `cut -d ; -f 2-5 serkan.csv | grep -v UYSAL | head -n 25`: Ilk işlem olarak **serkan.csv** içerisinden ayırıcı olarak *;* kullanarak **2 ile 5** arasındaki kolonları getirir. sonraki işlem olarak bu kolonlarda bulunan **UYSAL** satırlarını eler ve son işlem olarak elde ettiğimiz satırların ilk *25*'ini ekrana bastırır.
- `head -n 5 serkan.csv | wc` *Word Count*: serkan.csv dosyasındaki ilk 5 satırı getirir ve wc komutunu gerçekleştirir. Bu komut parametre de alır; **-c** byte sayar, **-m** karakter sayar, **-l** satır sayar, ve **-w** kelime sayar.
- `cut -d ; -f 1 klasör/*.csv` *Asteriks operator*: **.csv** uzantılı tüm dosyaları operasyona alır. Eğer uzantı girmeyip direkt * olarak bıraksaydık o zaman klasörde bulunan tüm dosyaları işleme alacaktık.
- `grep uysal serkan.txt | sort -n -r` *Sorting*: **Grep** komutu ile işlediğimiz girdilerimizi sıralarız. *-n* parametresi numerik olarak sıralarken *-r* parametresi ise bu işlemi ters çevirir. (Daha fazla parametre ve anlamları için **man sort**)
- `grep uysal serkan.txt | sort -n -r | uniq - ` *Unique*: Bir satırın birden fazla işleme alınmamasını sağlayan komut parçasıdır. (Daha fazla parametre ve anlamaları için **man uniq**)
- `cut -d ; -f 2-5 serkan.csv | grep UYSAL > uysals.csv`: Pipe yaparak oluşturduğumuz çıktılarımızı tek bir dosyaya yazabiliriz.

## Batch Processing

- `HOME`, `PWD`, `SHELL`, `USER`, ... *Environment variables*: Diğer programlar gibi shell'de değişkenleri saklayabilir.
- `echo $USER`: `$` işareti ile değişkenlerimize terminal üzerinden erişebiliriz.
- Dosya yollarını değişkenlere atayabilir ve başka bir yerde çağırabiliriz.

```bash
    serkan=dosya/serkan.txt
    echo $serkan
```

- Terminal üzerinden döngü oluşturabiliriz. *Foor Loop*:

```bash
for variable in list; do echo $variable; done
```

ile `list` içerisinde bulunan her satır `variable` değişkenine atanıp `echo $variable` ile ekrana bastırıp, `done` komutu ile for döngüsü bitirilir.

- Asteriks operatörünü for döngüsü ile kombinleyebiliriz.

```bash
dosyalar=klasör/*.csv
for dosya in $dosyalar; do echo $dosya; done
```

- Bir çok işlemi pipe olarak for döngüsünde kullanabiliriz. *Pipe*

```bash
for file in *.txt; do head -n 25 $file | tail -n 5; done
```

```bash
for file in *.txt; do echo $file; head -n 25 $file | tail -n 5; done
```

- Eğer dosya veya klasör adlarında boşluk kullanırsak, bu dosyalara/klasörlere ulaşmak için `"Dosya adı"` olarak çift tırnak içlerinde yazmamız gerekmektedir.
- `$@` ile *shell script*imizin dışarıdan parametre almasını sağlayabiliriz. Burada `@` yerine `$1`, `$2` ile sırasını belirlyebiliriz. Örnek bir script;

```bash
for dosya in $@
do
    head -n 25 $dosya | tail -n 5
    tail -n 5 $dosya
done
```
