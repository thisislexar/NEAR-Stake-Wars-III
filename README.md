# <h1 align="center">NEAR Stake Wars III</h1>

<h1 align="center">NEAR Stake Wars III için Validatör Kurulum Rehberine hoşgeldiniz. Kuruluma geçmeden önce NEAR Stake Wars hakkında bilgi vermek istiyorum. </h1>  

![stakewars3-social](https://user-images.githubusercontent.com/101462877/180663821-187214c4-7ac5-4b15-8c5a-0ca6a8d21dd9.png)


## NEAR Stake Wars challenge'larını tamamlayarak 4.5 milyon NEAR'dan pay kazanma şansı yakalayabilirsiniz. Ayrıca, görevleri tamamlayan validatörlerin 1 yıl kilitli olmak üzere 50 bin adete kadar NEAR coin kazanma şansı var. 

NEAR Stake Wars, NEAR ağında güncel olarak bulunan 100 adet aktif validatör sayısını 300'den fazla validatör sayısına çıkarmak için oluşturulmuştur. Bu sayede NEAR ağının daha merkeziyetsiz ve daha güvenli olması hedeflenmektedir. 

Daha fazla detay için [NEAR Stake Wars](https://near.org/stakewars/) websitesine göz atabilirsiniz. Ayrıca [Discord](https://discord.gg/kPcvwVtp) kanallarına katılmanızı öneririm, kurulum sırasında takıldığınız yerlerde diğer validatörler size yardımcı olabilir.

![NEAR-Protocol](https://user-images.githubusercontent.com/101462877/180665840-8c59f322-6163-4c15-8468-3d7c83745488.jpg)




## Bu makalede bahsedeceğim NEAR Stake Wars III görevleri için son tarih [11 Ağustos](https://github.com/near/stakewars-iii/blob/main/challenges/challenge-summary.md). Bunun için, makaleyi gördüğünüz andan itibaren en erken tarihte başlamanızı öneririm.

## Bu dokümanı sağ üstten forklayıp yıldızlamayı unutmayın, GitHub hesabınızda bulunması yararınıza olur. Ayrıca kurulumu yaparken lütfen okuyup anlayarak yapmaya çalışın, gördüğünüz her kodu yapıştırarak ilerlemenizi tavsiye etmem. Ne yaptığınızı bilerek ilerlemeniz sizin açınızdan çok daha sağlıklı olacaktır.

# Kurulumda 4 başlık altında ilerleyeceğiz. Bunlar; 

- 1) Shardnet cüzdanı oluşturma ve NEAR CLI'yi yükleme

- 2) Sunucu kurulumunu yapma ve validatör node'u aktive etme

- 3) Staking pool oluşturma ve delege/stake etme işlemleri 

- 4) Node durumunu görüntülemek için ayarlamalar


# 1) Shardnet cüzdanı oluşturma ve NEAR CLI'yi yükleme

## Kaynak olarak GitHub'ı kullanacağım, göz atmak isterseniz: [Stake Wars: Episode III. Challenge 001](https://github.com/near/stakewars-iii/blob/main/challenges/001.md#stake-wars-episode-iii-challenge-001)

Shardnet cüzdan oluşturma ile başlıyoruz. Öncelikle https://wallet.shardnet.near.org/ adresine gidiyoruz. 

![image](https://user-images.githubusercontent.com/101462877/180664884-fef0c64f-2cfd-49a6-a2ac-3d3498ad7d47.png)

Hesap oluştur'a tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180665024-0f3e9bad-e15c-427b-9158-8f8e6b86fe24.png)

Burada hesap kimliğimizi oluşturuyoruz. Örneğin, "nearciyim" hesap kimliği kullanılabilir durumda. Hesap Kimliği Oluştur'a tıklıyoruz ve hesabımızı oluşturuyoruz. Makalenin geri kalanında nearciyim hesap kimliğiyle devam edeceğim. Siz orada ne yazdıysanız ona göre gerekli yerleri değiştirirsiniz.

![image](https://user-images.githubusercontent.com/101462877/180665063-c48f8274-ea21-4f18-8774-a467bc71ef3a.png)

Bu noktada güvenliği nasıl sağlayacağımızı soruyor. Ben genelde güvenlik için anahtar kelimeyi seçiyorum ve onu mutlaka bir yere not alıyorum. Eğer dilerseniz Ledger Donanım Cüzdanı, E-posta ya da Telefon numarası gibi farklı güvenlik önlemlerini de seçebilirsiniz. Anahtar Kelimeyi Güvene Al'ı seçiyoruz ve aşağıdaki mavi Devam Et butonuna tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180665244-367ef49d-3640-426c-8e45-a998e88bb3e1.png)

Bu noktada bize verilen kelimeleri mutlaka bir yere kaydediyoruz ve Devam butonuna basıyoruz, bu sadece Shardnet için değil bütün cüzdanlarınız için geçerli. Herhangi bir şifre unutma, telefon bilgisayar kaybetme durumlarında bu kelimeler olmadan cüzdanınıza erişmeniz imkansız.

![image](https://user-images.githubusercontent.com/101462877/180665328-509f1146-bb89-4fa7-8110-1dfc8b2668e6.png)

Burada size kenara not aldığınız kelimelerden rastgele bir tanesini soruyor, doğru cevabı yazıp Doğrula & Tamamla'ya tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180665396-23cb60d5-6b2e-4801-ac45-bfb2edd2607d.png)

Cüzdan kurulduğunda bizi böyle bir sayfa karşılıyor, buradaki coinler gerçek değil test coini para kazanmadınız :) Coinlerimizi 3. aşamada kendi validatörümüze stake ederken kullanacağız. 

## NEAR Shardnet cüzdanımızı oluşturduk, şimdi bir sunucu kiralayıp node'umuzu kurmaya başlayabiliriz.

![image](https://user-images.githubusercontent.com/101462877/180665919-4512eb09-b4d3-455c-8a24-8295ef1034e3.png) ![image](https://user-images.githubusercontent.com/101462877/180665955-0a94b559-dea5-49a8-82f1-74084c7f8578.png)



NEAR Stake Wars III için sistem gereksinimleri bu şekilde belirlenmiş. Bizim de buna göre bir sunucu kiralayıp işlemlerimizi bu sunucu üzerinde yapmamız gerekiyor. Ayrıca sunucu temin ettiğimiz şirketin de sağ tarafta listeli olanlardan olmasına dikkat edelim.

## Ben bu makale için Digital Ocean üzerinden sunucu kiralayacağım. 2 ay için 100$ ücretsiz sunucu kiralama hakkı veriyor. Linkini buraya bırakıyorum: https://try.digitalocean.com/freetrialoffer/

Yukarıda verdiğim linke gidiyoruz. Mail ve şifremizle kaydoluyoruz.

![image](https://user-images.githubusercontent.com/101462877/180666565-b9bea560-d9eb-4076-b007-16b9ba78895c.png)

Kaydolduktan sonra bu noktada bizden kredi kartı ve adres bilgileri istiyor. Burayı doğru bir şekilde dolduruyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667131-e9d4e20f-2350-4108-858c-57583b2e49bb.png)

Bizi bu sayfa karşılıyor, Kontrol Panelimizi Keşfedin'e tıklıyoruz ve Kontrol Paneline gidiyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667181-85d4fcc5-efb9-482e-8240-a2c9b9eebf61.png) ![image](https://user-images.githubusercontent.com/101462877/180667192-3fbe6a40-cc4a-4810-a219-3c9c68ac115c.png)

Görselde görüldüğü gibi 100$ kredimiz aktive oluyor, create diyoruz ve droplet'e tıklıyoruz.
 
![image](https://user-images.githubusercontent.com/101462877/180667233-81e11209-147c-43ff-93ec-58f5b3376ef2.png) 
 
Görseldeki gibi işletim sistemi olarak Ubuntu 20.04 (LTS) x64 seçiyoruz. Aşağı doğru iniyoruz, sunucunun donanımını seçeceğiz.

![image](https://user-images.githubusercontent.com/101462877/180667303-7aed5f20-6ad6-48ea-abc0-698fab60df52.png) ![image](https://user-images.githubusercontent.com/101462877/180667356-6baa8154-41a4-421c-8d79-f7a24ed5851d.png)

Soldaki görselde gördüğünüz gibi Regular with SSD'ye tıklıyoz, 48$ olan sunucuyu seçiyoruz ve sistem gereksinimlerinde bulunan 500 GB SSD'yi karşılayabilmek için Add Block Storage'a tıklıyoruz. Açılan kısımda 500 GB'yi seçiyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667387-b2b035cb-1b62-4222-80bb-988edfb5dc1c.png)

Bu kısımlar seçili olduğu şekilde kalabilir, değiştirmenize gerek yok. Dilerseniz sunucunuzun konumunu değiştirebilirsiniz tabi. Aşağı iniyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667431-4b2680ba-7a9b-4182-8a19-8d8fa7e65552.png)

Bu noktada sunucumuza root olarak bağlanmak için bir şifre belirliyoruz. Bir şifre belirleyin ve kenara not edin. Makalenin ilerisinde sunucumuza WinSCP ile bağlanmamız gerekecek, bunun için root şifresi bize lazım.

Yine aşağı devam ediyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667560-2dcd43d3-cfc0-42e3-9fef-d160b7afc7ee.png)

Bu noktada sunucumuza bir isim veriyoruz ve aşağıdaki mavi Create Droplet'e tıklıyoruz. Ardından açılan sayfada sunucumuzun oluşturulmasını bekliyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667648-6c72a811-b66e-44b1-88ad-50aac3261558.png) ![image](https://user-images.githubusercontent.com/101462877/180667690-5bd41e8f-1ac8-417b-8cba-04d8cad498d8.png)


Sunucumuz oluşturulduktan sonra üzerine tıklıyoruz, altta sunucumuzun özelliklerini gösteren bir kısım açılıyor. Sunucu ismine tekrar tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667721-d7f13392-c57e-4b19-b2c6-bf4b8f55bd0c.png)

Açılan sayfada Console'a tıklıyoruz ve yeni bir pencerede Terminalimiz açılıyor. Terminalin yüklenmesini bekliyoruz.

![image](https://user-images.githubusercontent.com/101462877/180667773-8c93400e-f320-4b21-839a-27a7339e93b4.png)

Terminalimiz yüklendikten sonra artık node'umuzu kurmaya başlayabiliriz.

## Kodları direkt buradan kopyaladıktan sonra terminalde sağ tıklayıp yapıştıra basarak yapıştırabilirsiniz. Sizin için daha kolay ve pratik olur. Bu noktada, ilk olarak NEAR-CLI kurulumu yapacağız. NEAR-CLI, NEAR blokzinciri ile uzaktan prosedür çağrıları (RPC) sayesinde iletişim kuran bir komut satırı arabirimidir. 

# İlk kodumuz sunucumuzu güncellemek için:
```
sudo apt update && sudo apt upgrade -y
```

# Node.js ve npm gibi geliştirici araçlarını yüklüyoruz:
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -  
sudo apt install build-essential nodejs
PATH="$PATH"
```
# Yüklediğimiz Node.js ve npm'nin versiyonlarını kontrol edelim, aldığınız çıktılar girdiğiniz kodun altındaki çıktı gibi olmalı:
```
node -v
```
> v18.x.x

![image](https://user-images.githubusercontent.com/101462877/180668871-ee294d54-9501-4ab2-91dc-fc29f102216c.png)

Örneğin, bu doğru bir çıktı.

```
npm -v
```
> 8.x.x

Eğer node -v kodunu denediğinizde aşağıdaki gibi bir çıktı alıyorsanız, `apt install nodejs` kodunu girip tekrar deneyin.

![image](https://user-images.githubusercontent.com/101462877/180668809-7a1b406a-0084-4154-9ceb-db1ff222f765.png)

# Şimdi NEAR-CLI'yi sunucumuza kurmamız gerekiyor. Dilerseniz NEAR-CLI için GitHub dokümanına şuradan ulaşabilirsiniz: https://github.com/near/near-cli
```
sudo npm install -g near-cli
```

## Validatör Durumları

Şuan için NEAR-CLI'yi sunucumuza kurduk. Aşağıdaki 3 başlık validatör durumunu kontrol etmek için CLI'yi test eden komutlar. Sıra sıra bunları girerek inceleyebilirsiniz. Fakat bundan önce validatör için Environment düzenlemesi yapmamız gerekiyor.

Environment düzenlemesi için her bir kabuk başlangıcında doğru ağı seçmemiz gerekir.

NEAR ağı için geçerli ağlar şunlardır:
- GuildNet
- TestNet
- MainNet
- **Shardnet** (biz NEAR Stake Wars için Shardnet'i kullanıyor olacağız)

# Başlıyoruz Environment düzenlemesine.
```
export NEAR_ENV=shardnet
```

# NEAR testnet Environment'ını kalıcı olarak ayarlamak için bu komutu da kullanabilirsiniz:
```
echo 'export NEAR_ENV=shardnet' >> ~/.bashrc
```

## Environment'ımızı ayarladık. Şimdi CLI'yi test edecek komutlara geçebiliriz.

# 1-Teklif

Validatör tarafından ağa katılım için bir teklif yapılır. Bu teklifin kabul edilmesi için stake edilen miktarın o ağ için geçerli olan minimum seat price'ın üzerinde olması gerekir. Shardnet için gerekli minimum seat price bilgisine [buradan](https://explorer.shardnet.near.org/nodes/validators) ulaşabilirsiniz. Ayrıca validatör listesinde en altlara indiğinizde ağa katılmak için bekleyen proposal (teklif) konumundaki validatörleri görebilirsiniz. Aynı verilere aşağıdaki komutu çalıştırarak da erişebilirsiniz.

```
near proposals
```

# 2-Güncel Validatörler

Aşağıdaki komut güncel dönemdeki ağdaki aktif validatörleri, üretilen toplam blok sayısını, beklenen blok sayısını ve çevrimiçi oranı göstermektedir. Bu komut, validatörlerin sorun yaşayıp yaşamadığını öğrenmek için kullanılır. Ayrıca yine [explorer](https://explorer.shardnet.near.org/nodes/validators)'a giderek de şuan ağdaki aktif görev yapan validatörlere göz atabilirsiniz.

```
near validators current
```
# 3- Next Validatörler

Bu komutla birlikte ağa katılmak için teklif yapmış ve teklifi onaylanmış validatörleri görebilirsiniz. Yine  [explorer](https://explorer.shardnet.near.org/nodes/validators)'a giderek validatör durumu `joining` olanlara bakabilirsiniz.

```
near validators next
```

## Şu ana kadar sunucumuzu güncelledik, bazı gerekli geliştirici ayarlarını yaptık, Shardnet ağındaki validatörümüz için Environment ayarlarını oluşturduk ve NEAR CLI içerisinde bulunan 3 tane görüntüleme komutuna göz attık. Buradan sonrasında node'umuzu kurmayla ve onu çalıştırmayla devam edeceğiz.

# Sunucu kurulumunu yapma ve validatör node'u aktive etme

Kaynak olarak: [Stake Wars: Episode III. Challenge 002](https://github.com/near/stakewars-iii/blob/main/challenges/002.md#stake-wars-episode-iii-challenge-002)

# Sunucumuzun NEAR Stake Wars node kurulumu için yeterli olup olmadığına bakmak isterseniz bu kodu girebilirsiniz, girmenizi tavsiye ederim:
```
lscpu | grep -P '(?=.*avx )(?=.*sse4.2 )(?=.*cx16 )(?=.*popcnt )' > /dev/null \
  && echo "Supported" \
  || echo "Not supported"
```
![image](https://user-images.githubusercontent.com/101462877/180748070-cb73ab5f-17bd-4f4c-8a1e-9a34d96bd5cb.png)



## Eğer "Supported" çıktısı alıyorsak sunucumuz yeterlidir, "Not Supported" alıyorsak daha yüksek özellikli bir sunucuya geçiş yapmalısınız.


# Geliştirici araçlarını yükleme:
```
sudo apt install -y git binutils-dev libcurl4-openssl-dev zlib1g-dev libdw-dev libiberty-dev cmake gcc g++ python docker.io protobuf-compiler libssl-dev pkg-config clang llvm cargo
```

# Python pip'i yükleme:
```
sudo apt install python3-pip
```

# Konfigürasyon ayarları yapma:
```
USER_BASE_BIN=$(python3 -m site --user-base)/bin
export PATH="$USER_BASE_BIN:$PATH"
```

# Building ve Environment yükleme:
```
sudo apt install clang build-essential make
```

# Rust ve Cargo yükleme:
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

![image](https://user-images.githubusercontent.com/101462877/180748697-d858bb63-4cf5-4c5c-9cdf-b9f19a944d29.png)

Böyle bir kod çıkarsa y'ye basıp enter'a basıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180668110-38e73f3a-7c97-4ac7-a0ea-3dd7b51cc0d0.png)

## Burada karşınıza böyle bir şey çıkacak, 1 yazıp enter'a basıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180668131-8c7ce2b1-9502-4d58-8329-c7f25a419c16.png)

## Bu yazıyı gördüyseniz olmuştur.

# Kodları girmeye devam ediyoruz:
```
source $HOME/.cargo/env
```

# Burada GitHub üzerinden `nearcore`'u klonlayacağız:
```
git clone https://github.com/near/nearcore
cd nearcore
git fetch
```

# Ardından bu kodla devam ediyoruz:
```
git checkout 0f81dca95a55f975b6e54fe6f311a71792e21698
```

# Şimdi ise klonladığımız `nearcore`'u çalıştıracağız, bu kodun çalışması biraz uzun sürebilir:
```
cargo build -p neard --release --features shardnet
```
## Bu kısımda eğer No such file tarzı bir uyarı veriyorsa yanlış klasördesinizdir, `cd nearcore` yazarak tekrar deneyin.

# Çalışma dizinini başlatıyoruz:
Node'un çalışması için bir çalışma dizini ve konfigürasyon dosyaları gerekir. Bunlar için aşağıdaki kodu çalıştırıyoruz.
```
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
```
![image](https://user-images.githubusercontent.com/101462877/180668443-c48b5a71-6958-4b8e-accf-3a6514b23474.png)

Burada bu tür bir çıktı ile karşılaşacaksınız, karşılaşmadıysanız sorun var demektir.

Yukarıdaki komutla `config.json`, `genesis.json`, ve `node_key.json`  dosyalarını oluşturduk. 

Bu dosyaların işlevlerini birkaç cümlede anlatmak istiyorum.

- `config.json` dosyası düğümün ağ üzerinde nasıl çalışacağı, eşlerle nasıl iletişim kurulacağı ve fikir birliğine nasıl ulaşılacağı hakkında gerekli bilgileri içeren dosyadır.

- `genesis.json` Ağın başlangıç aşamasında başlattığı verileri içeren dosyadır. Blokzincir üzerindeki ilk hesaplar, sözleşmeler, erişim anahtarları ve diğer kayıtlar bu dosyada depolanır.

- `node_key.json` Node'umuz için public ve private key'leri içeren dosyadır. Bunun yanında, validatör node'unu çalıştırmak için gerekli olan account_id parametresini de içerir.

- `data/` NEAR node'unun güncel durumunun içine yazıldığı klasördür.

## Bu noktada, oluşturduğumuz `config.json` dosyasını node'umuz için kullanılabilir hale getirmemiz gerekiyor. Bunun için şu 2 değişikliği yapmamız gerekiyor:

- `boot_nodes` Eğer başlatma sırasında kullanılacak önyükleme node'larını belirtmediysek oluşturulan `config.json` boş bir dizi gösterir. Bu nedenle `config.json`'u önyükleme node'larını belirten dolu bir diziyle değiştirmemiz gerekiyor. Bunun için de alttaki komutu kullanacağız.

- `tracked_shards` Oluşturduğumuz `config.json` dosyasında bu alan boş. Bunu `"tracked_shards": [0]` ile değiştirmemiz gerekecek. Yine bunun için de, alttaki komutu çalıştırmamız yeterli olacaktır.

```
rm ~/.near/config.json
wget -O ~/.near/config.json https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/config.json
```

# Güncel snapshot(anlık görüntü)'ı alma

## ÖNEMLİ! Bu komut, Shardnet üzerinde Hardfork 18/07/2022'de gerçekleştikten sonra zorunlu bir komut değil. Almasanız da olur. Ben yine de anlatacağım almak isteyenler için.

AWS Cli'yi yüklüyoruz:

```
sudo apt-get install awscli -y
```

Snapshot'u indiriyoruz `genesis.json` olarak:

```
cd ~/.near
wget https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/genesis.json
```

Yukarıdaki kod error verirse dağıtım havuzundaki AWS Cli'nin tarihi geçmiş olabilir. Alttaki komutu deneyip tekrar deneyebilirsiniz:

```
pip3 install awscli --upgrade
```

# Şimdi node'umuzu çalıştırmaya geçiyoruz, buradan itibaren dikkatli ilerleyin WinSCP gibi uygulamalar kullanacağız. Komut üzerinden de yapılabiliyor fakat WinSCP üzerinden dosyaları görerek yapmanızı tavsiye ederim, bu sayede hata payını düşürmüş olursunuz.

## Eğer bilgisayarınızda WinSCP yüklü değilse şuradan indirip kurabilirsiniz: https://winscp.net/

# Node'u çalıştırma komutunu giriyoruz:

```
cd ~/nearcore
./target/release/neard --home ~/.near run
```
![image](https://user-images.githubusercontent.com/101462877/180760174-cd28c2b1-0108-4125-acda-465dbf71c52e.png)

## Burada altını çizdiğim `Downloading headers` kısmı %100 olana kadar bekleyin. %100 olduğuna emin olduktan sonra Ctrl+C ile akışı durdurup tekrar komut girmeye devam edebilirsiniz.


# Node'umuzu oluşturduğumuz Shardnet cüzdanına bağlayarak aktive ediyoruz:

```
near login
```

![image](https://user-images.githubusercontent.com/101462877/180769443-8f72c20d-fe40-4182-8b2f-b2c293ccf603.png)

Böyle bir soru soruyor, "y" yazıp enter'a basıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180769643-aa9a3fbd-fd6c-413d-8184-981d6fa05134.png)

Burada `https://` ile başlayan ve `Please authorize`'a kadar olan yeri ( `Please authorize` hariç) kopyalıyoruz ve Shardnet cüzdanını oluşturduğunuz tarayıcıya (örneğin Google Chrome) yapıştırıp adrese gidiyoruz. 

![image](https://user-images.githubusercontent.com/101462877/180770279-dc64d945-cb58-4618-ac58-efb897aa3338.png)

Bizi böyle bir sayfa karşılıyor, mavi `Sonraki` butonuna tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180770342-f379fa8b-ea3f-4dd1-b7eb-51be01bb36d9.png)

Açılan sayfada `Bağlan`'a tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180770453-ad5e653e-5479-40a1-ab64-619635cfd66e.png)

Hesap kimliğimizi istiyor, görseldeki gibi hesap kimliğimizi yazıyoruz ve `Onayla`'ya tıklıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180771012-98229f3f-c7d5-4976-a295-3bc3f4cce393.png) ![image](https://user-images.githubusercontent.com/101462877/180771133-a1f66794-df4b-49e1-ac34-1ad7f72d9e44.png)

Onayladıktan sonra böyle bir sayfa çıkıyor, merak etmeyin herhangi bir şeyi yanlış yapmadınız. Hemen bir altındaki görselde görüldüğü gibi hesap kimliğinizi sunucuda komut olarak yazın ve enter'a basın.


## NOT: Komutu girip enter'a bastıktan sonra `successfully` yazması gerekiyor. Ben node'u kendim kurarken alttaki gibi bir hatayla karşılaştım arkadaşlar terminal ekranı dondu herhangi bir çıktı vermedi, eğer sizde de böyle olursa ilk olarak terminali kapatıp açıp `near login` kısmından itibaren tekrar deneyin eğer yine olmazsa farklı bir [cüzdan](https://wallet.shardnet.near.org/) açıp işlemleri tekrar yapın.

![image](https://user-images.githubusercontent.com/101462877/180774902-fd5f4e06-e4aa-46fe-bc69-8b103d62b53b.png)

Birkaç denemeden sonra alttaki gibi bir çıktı aldım, başarıyla cüzdanı node'a bağladım.

![image](https://user-images.githubusercontent.com/101462877/180866887-577c747e-c2a5-4c34-a172-2bb6043c3a3e.png)


# Şimdi `validator_key.json` dosyamızı kontrol ediyoruz:


```
cat ~/.near/validator_key.json
```

## Muhtemelen bu komutu girdikten sonra `No such file or directory` hatası alacaksınız, çünkü `validator_key.json` dosyamız daha oluşturulmadı. Şimdi onu oluşturalım. Aşağıdaki komutta `<pool_id>` kısmı sizin oluşturmak istediğiniz pool'un adını içeren `xx.factory.shardnet.near` oluyor. Buradaki `xx`, sizin oluşturmak istediğiniz pool'un adı. Burada pool adınızı cüzdan adınızla aynı yapmayı tavsiye ediyorum. Örneğin hesap adınız `spiderman.shardnet.near` ise <pool_id> kısmına `spiderman.factory.shardnet.near` yazın.

```
near generate-key <pool_id>
```
# Şimdi WinSCP'yi kullanma zamanımız geldi. WinSCP'yi açıyoruz:

![Screenshot_2](https://user-images.githubusercontent.com/101462877/180778874-a93325e1-3ad4-4db7-b11c-bf9edd91fb8f.png)

Bizi böyle bir sayfa karşılıyor.

![image](https://user-images.githubusercontent.com/101462877/180779164-af3fa997-e683-4252-8ba6-b7821d0c4b79.png)

Sunucu adına yukarıdaki [Digital Ocean kontrol paneli](https://cloud.digitalocean.com/projects/)'nde NEAR Stake Wars için oluşturduğumuz sunucunu IP'sini yazıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180779589-2b5cde24-06d4-4900-a0ba-a60679488424.png)

Kullanıcı adı'na root, parola kısmına ise droplet'i oluştururken kenara not ettiğimiz root şifremizi yazıyoruz ve Oturum Aç'a tıklıyoruz.


![image](https://user-images.githubusercontent.com/101462877/180779849-746b3945-ccad-4f0c-b526-5aacca880945.png)

Sağ tarafta böyle bir klasör göreceksiniz, eğer yazısı sönük olan dosyalar sizde görünmüyorsa Ctrl + Alt + H yaparak görünmesini sağlayın. Ve boş bir yere sağ tıklayıp Yenile'ye tıklayın.

![image](https://user-images.githubusercontent.com/101462877/180780288-ecb889bf-8202-46be-9105-b61b16dd7fe4.png)

`.near-credentials` bu dosyanın içine girin.

![image](https://user-images.githubusercontent.com/101462877/180780472-4664f4e1-0caf-4c5e-b12a-a7db107b2dcc.png)

`shardnet` klasörüne girin.

![image](https://user-images.githubusercontent.com/101462877/180780582-2cdebedb-20e8-4f0e-9a0f-61dadd8b5eb2.png)

Burada 2 farklı `.json` dosyası var. Bunlardan `xx.factory.shardnet.near` olana giriyoruz.

![Screenshot_3](https://user-images.githubusercontent.com/101462877/180781047-fb073b95-20d6-4d73-80cd-83aa0a717379.png)

Bizi böyle bir dosya karşılıyor. Bu dosyanın içeriğinin tamamını kopyalıyoruz ve dosyayı kapatıyoruz.

![image](https://user-images.githubusercontent.com/101462877/180781278-d509c883-b404-4fe9-8143-a308748fd480.png)

Şimdi yukarıdaki root yazısına tıklayarak ana dizine geliyoruz.

![image](https://user-images.githubusercontent.com/101462877/180781384-d451596c-5c3e-431e-866b-61ff7f68a52a.png)

Buradaki `.near` dosyasının içine giriyoruz.

![image](https://user-images.githubusercontent.com/101462877/180781469-59b8f273-ed60-4024-9074-b512b0bfbbe7.png)

Boş bir yere tıklayıp yeni dosya oluştur diyoruz.

![image](https://user-images.githubusercontent.com/101462877/180781602-960c2f01-bdc0-4236-965a-4e0ec87c4978.png)

Dosyamızın ismini `validator_key.json` yapıyoruz. Burası önemli dosya ismini doğru yazdığınızdan emin olun.

![image](https://user-images.githubusercontent.com/101462877/180781741-caa78799-8b71-4ef0-944d-f37ea09093c2.png)

Ardından bu şekilde boş bir `json` dosyası karşımıza çıkıyor. Az önce `xx.factory.shardnet.near` dosyasından kopyaladığımız içeriği buraya yapıştırıyoruz.

![Screenshot_4](https://user-images.githubusercontent.com/101462877/180782260-aba5e882-a1cb-4035-b276-45fd74972a13.png)

Yapıştırdığımız içeriğin en sonuna gidip `private_key` olan kısmı `secret_key` olarak değiştiriyoruz. Sadece bu değişikliği yapın başka hiçbir şey değiştirmeyin ya da silmeyin, validatörünüz çalışmaz. Değişikliği yaptıktan sonra Ctrl + S yapıp kaydediyoruz ve dosyayı kapatıyoruz. WinSCP'yi kapatmayın tekrar lazım olacak.

# Terminalimize geri dönüyoruz ve aşağıdaki komutu giriyoruz bu komutun sonuçlanması biraz uzun sürecektir:

```
target/release/neard run
```

![image](https://user-images.githubusercontent.com/101462877/180782985-2b0ade3d-d999-4882-94bb-496c632ef14e.png)

Eğer yukarıdaki komutu girerken `No such file or directory` hatası alırsanız `cd nearcore` komutunu girip tekrar deneyin.

![image](https://user-images.githubusercontent.com/101462877/180784554-a014a854-caea-489c-b892-36c4ce0084aa.png)

`Downloading blocks` kısmı %100 olana dek bekliyoruz. %100 olduktan sonra Ctrl + C yapıyoruz.

# Systemd ayarlarını yapıyoruz:

```
sudo vi /etc/systemd/system/neard.service
```

# Burada bir pencere açılacak, aşağıdaki kodu olduğu gibi yapıştırıyoruz:

```
[Unit]
Description=NEARd Daemon Service

[Service]
Type=simple
User=root
#Group=near
WorkingDirectory=/root/.near
ExecStart=/root/nearcore/target/release/neard run
Restart=on-failure
RestartSec=30
KillSignal=SIGINT
TimeoutStopSec=45
KillMode=mixed

[Install]
WantedBy=multi-user.target
```

## Ardından bu pencereden çıkmak için Shift + Z + Z yapıyoruz. Shift'ten elimizi çekmeden iki kere arka arkaya Z'ye basıyoruz.

# Sistemi enable hale getiriyoruz:

```
sudo systemctl enable neard
```

# Sistemi başlatıyoruz:

```
sudo systemctl start neard
```

# Bir hatadan dolayı servis üzerinde değişiklikler yaparsanız, aşağıdaki komutla reload etmeniz gerekir:

```
sudo systemctl reload neard
```

# Sistemimiz başlatıldı. Log çıktılarını izlemek isterseniz komut:

```
journalctl -n 100 -f -u neard
```

## Eğer aşağıdaki gibi `No journal files were found.` hatası alırsanız, `systemctl restart systemd-journald.service` kodunu girip tekrar deneyin. Sisteme ufak bir restart atmanız hatayı çözecektir.

![image](https://user-images.githubusercontent.com/101462877/180880044-decd45b8-5ae1-4473-b782-2170c5e92cdb.png)


# Logların görünümü için şu komutları girebilirsiniz. İlk komut logları düzenli ve renkli göstermek için gerekli aracı indirir, ikinci komut logları renkli yapar:

```
sudo apt install ccze
```

```
journalctl -n 100 -f -u neard | ccze -A
```

# Bir validatörün oluşması için:

- Node'umuzun tamamen senkronize olması,

- `validator_key.json` dosyamızın oluşturulması,

- `validator_key.json` dosyamızın içeriğindeki public_key ile sözleşmenin başlatılması,

- Staking pool sözleşme ID'sinin account_id'miz ile aynı olması,

- Minimum seat price'ın karşılanması, (Güncel seat price'a [buradan](https://explorer.shardnet.near.org/nodes/validators) bakabilirsiniz),

- Sözleşmeye ping atılarak teklif sunulması (birazdan geleceğiz ping konusuna),

- Teklif kabul edildikten sonra validatörün 2-3 epoch (dönem) bekleyip aktif validatör setine girmesi,

- Aktif validatör setine girildikten sonra imzalanan blok sayısının %90'ın üzerinde olması gereklidir.


## Bence kurulumun en zor kısmı olan bu kısımla birlikte özet olarak; 

- Sunucumuza gerekli geliştirici araçlarını yükledik (cargo, rust, python pip vb.), 

- Konfigürasyon ve Environment ayarlarını yaptık, 

- GitHub üzerinden node'umuzun çalışması için gerekli olan `nearcore`'u yükledik, 

- Yüklediğimiz `nearcore`'u çalıştırdık,
 
- NEAR Shardnet ağındaki ilk verileri içeren `genesis` dosyasını indirip çalıştırdık, 

- `config.json`, `genesis.json`, ve `node_key.json` dosyalarımızı oluşturduk, 

- Gerekli olmasa da isteyenler için en güncel snapshot(`genesis.json`)'u indirdik, 

- Kurduğumuz node'umuzu çalıştırdık,

- NEAR Shardnet cüzdanımızla node'umuzu eşleştirip validatör oluşturduk.


# 3) Staking pool oluşturma ve delege/stake etme işlemleri

Kaynak: [Stake Wars: Episode III. Challenge 003](https://github.com/near/stakewars-iii/blob/main/challenges/003.md#stake-wars-episode-iii-challenge-003)

NEAR, delegatörlerin fonlarının güvende kalmasını sağlamak için whitelist'e alınmış bir stake sözleşmesine sahip stake havuzu kullanır.

NEAR üzerinde bir validatör çalıştırmak için bir NEAR hesabında stake havuzu dağıtılmalı ve NEAR validatör node'una entegre edilmelidir. Stake havuzu, NEAR hesabına dağıtılmış olan bir akıllı sözleşmedir.

## Stake Havuzu Sözleşmesinin Dağıtımı

Aşağıdaki komut, stake havuzu factory'sini çağırır ve yeni bir stake havuzu oluşturur. Komutu doğrudan terminale YAPIŞTIRMAYIN. Değiştirmeniz gereken kısımları aşağıda belirttim, onları değiştirdikten sonra komutu çalıştırın.

```
near call factory.shardnet.near create_staking_pool '{"staking_pool_id": "<pool id>", "owner_id": "<accountId>", "stake_public_key": "<public key>", "reward_fee_fraction": {"numerator": 5, "denominator": 100}, "code_hash":"DD428g9eqLL8fWUxv8QSpVFzyHi1Qd16P8ephYCTmMSZ"}' --accountId="<accountId>" --amount=30 --gas=300000000000000
```

## Burada değiştirmeniz gereken kısımlar:

- `<pool id>`: Bu kısıma stake havuz adımızı giriyoruz. Örneğin, pool'umuzun adı `spiderman.factory.shardnet.near` ise bu komutu girerken `<pool id>` kısmına `spiderman` yazacağız.

- `<accountId>`: Bu kısıma hesap kimliğimizi giriyoruz. Örneğin, `spiderman.shardnet.near`

- `<public key>`: Bu kısım için WinSCP'yi tekrar açıyoruz. Nasıl bağlanacağınızı yukarıda anlatmıştım.

![image](https://user-images.githubusercontent.com/101462877/180886021-4659e678-986a-422e-8c6f-c906a7be82b3.png)

.near klasörüne giriyoruz.

![image](https://user-images.githubusercontent.com/101462877/180886090-1f075b87-8f6e-4d33-9ddc-ba2f5bc3187e.png)

`validator_key.json` dosyamızı buluyoruz ve açıyoruz. Eğer yukarıdaki adımları doğru bir şekilde takip etmenize rağmen bu dosyayı bulamazsanız klasör içerisinde boş bir yere sağ tıklayıp `Yenile` diyelim.

![image](https://user-images.githubusercontent.com/101462877/180886230-9cdbbb0a-e0df-4a90-b7a8-bde86618ef4f.png)

ed25519 ile başlayan `public.key` kısmını olduğu gibi kopyalıyoruz. Komut içerisindeki <public key> yerine yapıştırıyoruz.

- Reward_fee_fraction olarak belirtilen kısım varsayılan olarak %5 olarak belirtilmiş burada. İsterseniz değiştirebilirsiniz ama değiştirmenize gerek yok. Pool'a stake edenlerden alınacak fee'yi temsil ediyor.

- `<accountId>`: Bu kısıma yine hesap kimliğimizi giriyoruz. Örneğin, `spiderman.shardnet.near`

## Biraz karışık olduğu için ben kendi örnek node'umu oluştururken girdiğim komutu buraya bırakıyorum, buna bakarak kendinizinkini düzenleyin lütfen. Doğrudan yapıştırırsanız çalışmaz.
 
 ```
near call factory.shardnet.near create_staking_pool '{"staking_pool_id": "nearstakewars", "owner_id": "nearstakewars.shardnet.near", "stake_public_key": "ed25519:6UfGtVfCVg1hjiyR8nrrwL7A8vbFxxxxxxxxxxxxx", "reward_fee_fraction": {"numerator": 5, "denominator": 100}, "code_hash":"DD428g9eqLL8fWUxv8QSpVFzyHi1Qd16P8ephYCTmMSZ"}' --accountId="nearstakewars.shardnet.near" --amount=200 --gas=300000000000000
```
 
![image](https://user-images.githubusercontent.com/101462877/180963324-c88a7903-ce2e-4d3c-ad96-f868c8f25f93.png)
 
> Bu komutu girmeden önce Shardnet cüzdanınızda en az 30 NEAR olduğuna emin olun. 30 NEAR, stake havuzu oluşturabilmek için tek seferde stake etmeniz gereken minimum miktar.
 
## Yukarıdaki komutla birlikte Staking Havuzumuzu oluşturmuş olduk. Havuzunuzu [explorer]( https://explorer.shardnet.near.org/nodes/validators) üzerinden kontrol edebilirsiniz. Oluşturduğunuz an `proposal` kısmında bulunacaktır. Bir sonraki epoch'ta `joining` kısmında, eğer `kickout` olmazsanız da bir sonraki epoch'ta `active` kategorisine geçecektir.

Oluşturduğunuz havuzun parametrelerini değiştirmek isterseniz, örneğin stake fee değerini değiştirmek isterseniz aşağıda bıraktığım komutu kullanabilirsiniz:

```
near call <pool_name> update_reward_fee_fraction '{"reward_fee_fraction": {"numerator": 1, "denominator": 100}}' --accountId <account_id> --gas=300000000000000
```

![image](https://user-images.githubusercontent.com/101462877/180960238-f01ea3da-eabd-49f4-af1b-b9f7fd06cfd1.png)

Yukarıdaki gibi bir çıktı alırsanız değişmiş demektir.
 
# Pool için İşlem Rehberi
 
## NEAR'ları Deposit ve Stake Etme
 
Aşağıdaki komut ile NEAR'larınızı cüzdanınızdan havuzunuza aktarabilir ve stake edebilirsiniz:
 
```
near call <staking_pool_id> deposit_and_stake --amount <amount> --accountId <accountId> --gas=300000000000000
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<amount>`: stake etmek istediğiniz NEAR miktarı
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180963092-cb632825-44ae-4ca7-b844-b2837b1d70ea.png)

 
## NEAR'ları Havuzdan Unstake Etme
 
Aşağıdaki komut ile NEAR'larınızı havuzunuzdan unstake edebilirsiniz. Fakat bu NEAR'ları doğrudan cüzdanınıza çekmez, bunun için aşağıda bahsettiğim `withdraw` başlığına göz atmalısınız:
 
```
near call <staking_pool_id> unstake '{"amount": "<amount yoctoNEAR>"}' --accountId <accountId> --gas=300000000000000
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<amount yoctoNEAR>`: unstake etmek istediğiniz NEAR miktarı, yoctoNEAR cinsinden.
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180963448-e9da5bf3-3617-482c-84be-28d52e5cc082.png)
 
Eğer stake havuzundaki tüm NEAR'ları unstake etmek isterseniz de aşağıdaki komutu kullanın:
 
```
near call <staking_pool_id> unstake_all --accountId <accountId> --gas=300000000000000
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180963706-2d1ad732-e410-4966-8b14-d72d666b3c35.png)


## NEAR'ları Cüzdana Çekme
 
Bu işlemi yapabilmek için öncelikle yukarıdan unstake yapmanız gerekir. Unstake periyodu yaklaşık 2-3 epoch içerisinde tamamlanır. Unstake periyodunun ardından YoctoNEAR'larınızı havuzdan cüzdana çekebilirsiniz.
 
Cüzdana çekme için komut:

```
near call <staking_pool_id> withdraw '{"amount": "<amount yoctoNEAR>"}' --accountId <accountId> --gas=300000000000000
```

- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<amount yoctoNEAR>`: cüzdana çekmek istediğiniz NEAR miktarı, yoctoNEAR cinsinden.
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 

Unstake edilmiş tüm NEAR'larınızı cüzdana çekmek isterseniz komut:
 
```
near call <staking_pool_id> withdraw_all --accountId <accountId> --gas=300000000000000
```

- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
## Ping İşlemi
 
Ping işlemi, yeni bir teklif yayınlar ve delegatörleriniz için staking bakiyelerini günceller. Staking havuzu sayesinde kazandığınız ödülleri güncel tutmak için her epoch içerisinde en az bir ping gönderilmelidir.

Ping komutu:

```
near call <staking_pool_id> ping '{}' --accountId <accountId> --gas=300000000000000
```

- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180966647-1fde183a-9089-4723-8891-8c1057c1eb3d.png)
 
Toplam bakiyenizi görüntülemek için komut:
 
```
near view <staking_pool_id> get_account_total_balance '{"account_id": "<accountId>"}'
```

- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180966760-405f1882-d29f-43fd-82c2-3bf323e6cb3e.png)

Buradaki o uzun yeşil 2500000xxx şeklinde devam eden sayı 250 NEAR demek oluyor.
 
 
## Stake Edilmiş Bakiye
 
Aşağıdaki komut sayesinde stake edilmiş toplam bakiyenizi öğrenebilirsiniz.
 
Komut:

```
near view <staking_pool_id> get_account_staked_balance '{"account_id": "<accountId>"}'
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180967381-908f10e5-c407-4c42-a1a9-c661e37b6c5a.png)
 
## Unstake Edilmiş Bakiye
 
Aşağıdaki komut sayesinde unstake edilmiş toplam bakiyenizi öğrenebilirsiniz.
 
Komut:

```
near view <staking_pool_id> get_account_unstaked_balance '{"account_id": "<accountId>"}'
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180967606-ef703190-0b39-4307-bf2d-97ce2b85150b.png)

## Cüzdana Geri Çekilebilir Durumda Olan Bakiye
 
Aşağıdaki komut sayesinde unstake edilmiş ve cüzdana geri çekebileceğiniz NEAR miktarını öğrenebilirsiniz. Unutmayın, sadece unlocked olmuş NEAR'ları cüzdanınıza geri çekebilirsiniz, unlocked olması için de unstake edildikten sonra 2-3 epoch beklemeniz gerekir.
 
Komut:

```
near view <staking_pool_id> is_account_unstaked_balance_available '{"account_id": "<accountId>"}'
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180968189-7be6e4c3-02e0-4027-9db2-e5c9938fff79.png)

Burada NEAR'larımı yeni unstake ettiğim ve 2-3 epoch geçmediği için NEAR'larım Withdraw için hazır değil, bu yüzden `false` çıktısı verdi. `True` çıktısı verdiğinde NEAR'larımızı cüzdana çekebiliriz.
 
## Staking'i Durdurmak / Tekrar Başlatmak
 
Aşağıdaki komut sayesinde staking işleminizi durdurabilirsiniz.
 
###### Durdurmak
 
Komut:

```
near call <staking_pool_id> pause_staking '{}' --accountId <accountId>
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
Aşağıdaki komut sayesinde staking işleminizi tekrar başlatabilirsiniz.
 
###### Tekrar Başlatmak
 
Komut:

```
near call <staking_pool_id> resume_staking '{}' --accountId <accountId>
```
 
- `<staking_pool_id>`: xx.factory.shardnet.near
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near

 
## Bu kısmın bitişiyle birlikte özet olarak; 

- NEAR Shardnet ağı üzerinde staking havuzu açtık, 

- Açtğımız staking havuzuna cüzdanımızdan NEAR deposit ettik ve bu NEAR'ları havuzumuza stake ettik, 

- Havuzumuza stake ettiğimiz NEAR'ları unstake ettik, 

- Unstake ettiğimiz NEAR'ları cüzdanımıza geri çektik (2-3 epoch bekledikten sonra),
 
- NEAR Shardnet ağında delegator olarak ping gönderdik, 

- Staking havuzumuzdaki toplam NEAR bakiyemizi öğrendik, 

- Staking havuzumuzdaki toplam stake / unstake edilmiş NEAR bakiyemizi öğrendik, 

- Staking havuzumuzda stake işlemlerini durdurduk ve tekrar başlattık.


# 4) Node durumunu görüntülemek için ayarlamalar
 
Kaynak: [Stake Wars: Episode III. Challenge 004](https://github.com/near/stakewars-iii/blob/main/challenges/004.md#stake-wars-episode-iii-challenge-004)
 
## Bu bölümde kurduğumuz node'un durumunu gözlemlemek için kullanacağımız araçlara göz atacağız. Node'u çalışır durumda tutabilmek adına RPC'nin 3030 numaralı port noktasına kurulması ve kullanılması gerekir. 
 
#### Log Dosyaları
 
Log dosyaları kurulumu nereye yaptığınıza bağlı olarak `~/.nearup/logs` dizininde ya da `systemd`'de depolanır.
 
 
 Systemd Komutu:
 
 ```
journalctl -n 100 -f -u neard | ccze -A
```
 
Bu komut sayesinde akan logların örneğine ve bu örneğin ne ifade ettiğine aşağıdan bakabilirsiniz.
 
 ```
INFO stats: # 1368392 JAH2UK8ahcAhW859jyMk7NNFVn6bqSAuYNtkcYrZj2o7 Validator | 100 validators 34 peers ⬇ 430 kB/s ⬆ 478 kB/s 0.19 bps 274 Tgas/s CPU: 148%, Mem: 4.88 GB
```
 
- `Validator`: Bu kısım sizin aktif bir validatör olduğunuzu gösterir.
 
- `100 Validators`: Bu kısım ağdaki toplam validatör sayısını belirtir.
 
- `34 peers`: Bu kısım sizin bağlandığınız eşlerin sayısını gösterir. Consensus'a erişmek ve doğrulamaya başlayabilmek için en az 3 eşe ihtiyacınız vardır.
 
- `# 1368392`: Bu kısım güncel bloğun nerede olduğunu gösterir.
 
 
## RPC

Ağdaki node'lar, port'u güvenlik duvarında açık olduğu sürece 3030 portu üzerinde RPC hizmetleri sunar. NEAR-CLI, RPC çağrılarını kullanır. RPC'nin genel kullanım alanları validatör istatistiklerini, node versiyonunu, delegatör stake'ini kontrol etmektir. Ayrıca bunun yanında RPC; blokzincir, hesaplar ve sözleşmeler ile etkileşime girmek için de kulanılabilmektedir.
 
Aşağıda RPC servislerini nasıl kullanacağınızla ilgili birkaç komut bulunuyor, detaylı araştırmak isterseniz buraya göz atabilirsiniz: https://docs.near.org/docs/api/rpc
 
# Bu komutumuz gerekli dosyaları indirir:

 ```
sudo apt install curl jq
```
 
![image](https://user-images.githubusercontent.com/101462877/180996701-ff5f8eee-8f34-47c0-a3ab-f10c81ce6915.png)

Buradaki gibi devam etmeyi isteyip istemediğimizi soracaktır, Y yazıp enter'a basıyoruz.
 
# Bu komut ile node'unuzun versiyonunu kontrol edebilirsiniz:

 ```
curl -s http://127.0.0.1:3030/status | jq .version
```
 
![image](https://user-images.githubusercontent.com/101462877/180997001-ee6bfc10-841c-4b07-87dd-5283b35631a2.png)

Bu tür bir çıktı gelecektir.
 
# Bu komut sayesinde stake havuzundaki delegatörleri ve stake ettikleri miktari öğrenebilirsiniz:

 ```
near view <your pool>.factory.shardnet.near get_accounts '{"from_index": 0, "limit": 10}' --accountId <accountId>.shardnet.near
```
 
- `<your pool>`: xx.factory.shardnet.near kısmındaki xx'i gireceksiniz
 
- `<accountId>`: cüzdan hesap kimliğiniz, xx.shardnet.near
 
![image](https://user-images.githubusercontent.com/101462877/180998067-d0b21bae-e378-4f8f-a114-ebd9777b1d94.png)

Bu tür bir çıktıya sahip olursunuz.
 
# Bu komut eğer ağdan atıldıysak çalışır, ağdan neden atıldığımızı gösterir. Ayrıca bu komutu ağdan atıldıktan hemen bir sonraki epoch içerisinde girmemiz gerekir, diğer epoch'larda çalışmayacaktır:

 ```
curl -s -d '{"jsonrpc": "2.0", "method": "validators", "id": "dontcare", "params": [null]}' -H 'Content-Type: application/json' 127.0.0.1:3030 | jq -c '.result.prev_epoch_kickout[] | select(.account_id | contains ("<POOL_ID>"))' | jq .reason
```
 
- `<POOL_ID>`: xx.factory.shardnet.near
 

 # Bu komut sayesinde ağ üzerinde kaç blok ürettiğinizi ve expected blok sayısını görebilirsiniz:

 ```
curl -s -d '{"jsonrpc": "2.0", "method": "validators", "id": "dontcare", "params": [null]}' -H 'Content-Type: application/json' 127.0.0.1:3030 | jq -c '.result.current_validators[] | select(.account_id | contains ("POOL_ID"))'
```
 
- `<POOL_ID>`: xx.factory.shardnet.near

![image](https://user-images.githubusercontent.com/101462877/180998490-ed22b9e1-ba16-48d4-bed8-401c6cc41e17.png)

Stake havuzunu yeni açtıysanız ve daha henüz aktif validatör değilseniz herhangi bir çıktı almazsınız.
 
![image](https://user-images.githubusercontent.com/101462877/180998697-8f361c1f-3fd5-416f-b18f-6c2cb00d1871.png)

Aktif bir validatöre sahip iseniz bu tür bir çıktı alırsınız. Göründüğü gibi "num_produced_blocks" kısmı 0 görünüyor. Çünkü aktif sette olsanız bile sadece ilk 100 aktif validatör blok üretir. Diğer aktif validatörlerin ürettiği bloklar ise chunk-only olarak adlandırılıyor.
 
 
 # NORMAL ŞARTLARDA BURAYA KADAR OLAN KISMIN CHALLENGE 5 İÇİN YETERLİ OLMASI GEREKİYOR, ANCAK BEN CHALLENGE 6, 8 VE 9 İÇİN DE REHBER OLUŞTURMAYA KARAR VERDİM. BURAYA KADAR GELEN NEAR AĞI TOPLULUĞU ÜYELERİ 6,8 VE 9. CHALLENGE'LARININ ÖDÜLLERİNDEN GERİ KALMASIN İSTEDİM.
 
# PEKİ CHALLENGE 7 NERDE DİYE SORACAK OLURSANIZ, CHALLENGE 7 İÇİN HERHANGİ BİR KOD KOMUT İŞLEMİ YOK. SİZİN KENDİ ÇABALARINIZLA YAPMANIZ GEREKEN BİR DATA SCIENCE GÖREVİ. BU YÜZDEN CHALLENGE 6-8 VE 9 İLE DEVAM EDECEĞİZ. CHALLENGE'LAR HAKKINDA DETAYLI BİLGİ İÇİN: https://github.com/near/stakewars-iii/tree/main/challenges



# CHALLENGE 6: PİNG GÖREVİ

Node validatöründe ağa otomatik olarak ping gönderen bir cron görevi oluşturacağız. Bu görev sayesinde, belirlediğimiz periyot süresiyle ağa otomatik olarak ping gönderilecektir. Gönderilen ping, NEAR ağı ve node'umuz arasındaki bağlantıyı güncellemeye yarar.

WinSCP'ye tekrar giriyoruz.

![image](https://user-images.githubusercontent.com/101462877/181223928-d65f331a-3fa9-47db-95d9-5960d5c86582.png)

Root dizininde sağ tıklayıp yeni klasör oluştur diyoruz.

![image](https://user-images.githubusercontent.com/101462877/181224048-d3de3414-3f91-45a6-8640-54cfcaf5d800.png)

Klasörün adı `logs` olacak.

![image](https://user-images.githubusercontent.com/101462877/181224129-6e4fedf3-d51a-457d-aa61-315e0b5cc76a.png)

Oluşturduğumuz klasörün içine giriyoruz.

![image](https://user-images.githubusercontent.com/101462877/181224195-c94323e8-463d-49e6-bba8-e6e2cb4e1eed.png)

Boş bir klasör bizi karşılıyor, sağ tıklayıp bu sefer dosya oluştur diyoruz.

![image](https://user-images.githubusercontent.com/101462877/181229724-0e3e75d9-d0e5-477d-a440-a29a5a096b44.png)

Dosyanın adı `all.log` olacak şekilde oluşturuyoruz.

![image](https://user-images.githubusercontent.com/101462877/181230035-f2d2940e-ab87-4b9d-8a2c-4ae598048766.png)


Boş dosya karşımıza geliyor, rastgele herhangi bir şeyler yazıyoruz ki dosyayı oluşturabilelim. Ctrl + S yapıp kaydediyoruz ve `all.log` dosyasını kapatıyoruz.

![image](https://user-images.githubusercontent.com/101462877/181230473-a2f69dc0-f5bf-4e98-ba87-234b938a5e0c.png)


Göründüğü gibi dosyamız burada oluştu, şimdi içine tekrar girip yazdığımız rastgele şeyi silip tekrar Ctrl + S yapıyoruz.

![image](https://user-images.githubusercontent.com/101462877/181225532-15a742ce-3f66-47e8-824d-5ed399de28fc.png)

Son durumda oluşturduğumuz dosyanın var olması ve içinin boş olması gerekiyor, yazdığınız rastgele şeyin hala dosyada kayıtlı olmadığına emin olun ve öyle devam edin. `all.log` dosyamızı kapatıyoruz.

![image](https://user-images.githubusercontent.com/101462877/181230288-a8f20baf-4432-48a3-974c-325251d32c2b.png)

Buradaki `root` yazısına tıklayarak root dizinimize geri dönüyoruz.

![image](https://user-images.githubusercontent.com/101462877/181226262-373baafa-20af-4775-b5ea-877ca33aaa91.png)

`nearcore` dosyamızın içine giriyoruz.

![image](https://user-images.githubusercontent.com/101462877/181226346-d22ea131-c73a-4f63-8088-16913b06d414.png)

`nearcore` klasörümüzün içinde `scripts` klasörünü bulup içine giriyoruz.

![image](https://user-images.githubusercontent.com/101462877/181226485-8645f66e-a3f2-4c82-bace-606f2ce0b2d0.png)

Klasörümüzün içinde boş bir yere sağ tıklayıp dosya oluştur diyoruz.

![image](https://user-images.githubusercontent.com/101462877/181226675-7e8a7a67-140c-46e2-af6b-b4c9af221b01.png)

Dosya adını görseldeki gibi dikkatli bir şekilde `ping.sh` yapıp tamam diyoruz.

Açılan boş dosyanın içine aşağıdaki kodu olduğu gibi yapıştırıyoruz, fakat üzerinde değişiklik yapacağınız birkaç yer var onları kodun altına bırakıyorum.

 ```
#!/bin/sh
# Ping call to renew Proposal added to crontab

export NEAR_ENV=shardnet
export LOGS=/root/logs
export POOLID=<pool_id>
export ACCOUNTID=<account_id>

echo "---" >> $LOGS/all.log
date >> $LOGS/all.log
near call $POOLID.factory.shardnet.near ping '{}' --accountId $ACCOUNTID.shardnet.near --gas=300000000000000 >> $LOGS/all.log
near proposals | grep $POOLID >> $LOGS/all.log
near validators current | grep $POOLID >> $LOGS/all.log
near validators next | grep $POOLID >> $LOGS/all.log
 ```

- `<pool_id>`: xx.factory.shardnet.near kısmındaki xx'i gireceksiniz
 
- `<account_id>`: xx.shardnet.near kısmındaki xx'i gireceksiniz


Değişiklikleri yaptıktan sonra Ctrl + S yaparak dosyayı kaydediyoruz ve kapatıyoruz.

# Şimdi terminalimize geri dönüyoruz ve aşağıdaki kodu yapıştırıyoruz:

 ```
crontab -e
 ```
 
![image](https://user-images.githubusercontent.com/101462877/181228098-03ca16f4-930c-4707-84d4-7bdc9bb45e0e.png)

Böyle bir ekran açılıyor, Shift + Enter yaparak yorum kısımlarını aşağıya ittiriyoruz ve aşağıdaki kodu buraya yapıştırıyoruz. Bu kod sayesinde node'umuz NEAR Shardnet Ağı'na her 2 saatte bir ping gönderecektir.

 ```
0 */2 * * * sh /root/nearcore/scripts/ping.sh
 ```
 
 ![image](https://user-images.githubusercontent.com/101462877/181228338-0843c12e-1417-4376-a4e2-022004c93f9c.png)

Bu şekilde göründüğüne emin olduktan sonra Ctrl + X yapıyoruz. Kaydetmek isteyip istemediğimizi soruyor, Y diyoruz. Dosya adını soruyor, Enter basıyoruz.

Ardından aşağıdaki kodu girip doğru şekilde kaydedip kaydetmediğimize bakabiliriz:

 ```
crontab -l
 ```
 
 ![image](https://user-images.githubusercontent.com/101462877/181228869-de67afdd-5562-4212-8c54-093e7d878c09.png)

Böyle bir çıktı alırsanız doğru yapmışsınızdır, devam edebilirsiniz. Böyle bir çıktı almadıysanız `crontab -e` kodundan itibaren işlemleri tekrar yapın.

Loglarımızı kontrol etmek için aşağıdaki kodu giriyoruz:

```
cat /root/logs/all.log
 ```
 
 ![image](https://user-images.githubusercontent.com/101462877/181230711-151079db-7eb5-4f83-a235-e73a6671be0e.png)

İlk oluşturduğunuz zaman dosyanın için hala boşsa panik yapmayın, ping periyodunu 2 saat yaptığımız için veriler buraya 2 saatte bir düşecektir. Oluşturduktan en az 2 saat sonra üstteki komutu denediğinizde boş bir çıktı almayacaksınız.

Örneğin:

![image](https://user-images.githubusercontent.com/101462877/181234896-c9ccc7e7-32b0-4e12-992a-d36502f6acd8.png)


# ÖNEMLİ!

# BU GÖREVİ YAPTIKTAN SONRA YOLLAMANIZ GEREKEN BİR FORM VAR. DETAYLARINA https://github.com/thisislexar/stakewars-iii/blob/main/challenges/006.md LİNKİNE GİDEREK AŞAĞIDAKİ ACCEPTANCE CRITERIA'DAN ULAŞABİLİRSİNİZ. YAPMANIZ GEREKEN ŞEY [EXPLORER](https://explorer.shardnet.near.org/nodes/validators) 'A GİDEREK ARAMA KISMINA `XX.FACTORY.SHARDNET.NEAR` STAKING HAVUZ ID'NİZİ YAZMAK. BİRAZ AŞAĞI İNDİĞİNİZDE AŞAĞIDAKİ GİBİ TRANSACTION'LAR GÖRECEKSİNİZ. 

![image](https://user-images.githubusercontent.com/101462877/181235376-cbec34d4-b83c-49c2-ac30-7d9a2683b3d0.png)

BU PING TRANSACTION'LARINDAN 3-4 TANE OLDUKTAN SONRA FORM'A BURAYI SS ALIP SUBMITLİYORUZ. AYRICA EXPLORER LİNK'İMİZİ DE SUBMITLEMEMİZ GEREKİYOR. AŞAĞIYA FORM'U BIRAKIYORUM, GİRİP BAKTIĞINIZDA ANLARSINIZ ZATEN.

FORM: https://docs.google.com/forms/d/e/1FAIpQLScp9JEtpk1Fe2P9XMaS9Gl6kl9gcGVEp3A5vPdEgxkHx3ABjg/viewform
