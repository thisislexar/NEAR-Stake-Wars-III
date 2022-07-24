# <h1 align="center">NEAR Stake Wars III</h1>

<h1 align="center">NEAR Stake Wars III için Validator Kurulum Rehberine hoşgeldiniz. Kuruluma geçmeden önce NEAR Stake Wars hakkında bilgi vermek istiyorum. </h1>  

![stakewars3-social](https://user-images.githubusercontent.com/101462877/180663821-187214c4-7ac5-4b15-8c5a-0ca6a8d21dd9.png)


## NEAR Stake Wars challenge'larını tamamlayarak 4.5 milyon NEAR'dan pay kazanma şansı yakalayabilirsiniz. Ayrıca, görevleri tamamlayan validatörlerin 1 yıl kilitli olmak üzere 50 bin adete kadar NEAR coin kazanma şansı var. 

NEAR Stake Wars, NEAR ağında güncel olarak bulunan 100 adet aktif validatör sayısını 300'den fazla validatör sayısına çıkarmak için oluşturulmuştur. Bu sayede NEAR ağının daha merkeziyetsiz ve daha güvenli olması hedeflenmektedir. 

Daha fazla detay için [NEAR Stake Wars](https://near.org/stakewars/) websitesine göz atabilirsiniz. Ayrıca [Discord](https://discord.gg/kPcvwVtp) kanallarına katılmanızı öneririm, kurulum sırasında takıldığınız yerlerde diğer validatörler size yardımcı olabilir.

![NEAR-Protocol](https://user-images.githubusercontent.com/101462877/180665840-8c59f322-6163-4c15-8468-3d7c83745488.jpg)




## Bu makalede bahsedeceğim NEAR Stake Wars III görevleri için son tarih [11 Ağustos](https://github.com/near/stakewars-iii/blob/main/challenges/challenge-summary.md). Bunun için, makaleyi gördüğünüz andan itibaren en erken tarihte başlamanızı öneririm.

# Kurulumda 4 başlık altında ilerleyeceğiz. Bunlar; 

-Shardnet cüzdanı oluşturma ve NEAR CLI'yi yükleme

-Sunucu kurulumunu yapma ve validatör node'u aktive etme

-Staking pool oluşturma ve delege/stake etme işlemleri 

-Node durumunu görüntülemek için ayarlamalar


# Shardnet cüzdanı oluşturma ve NEAR CLI'yi yükleme

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

Bu noktada sunucumuza root olarak bağlanmak için bir şifre belirliyoruz. Bir şifre belirleyin ve kenara kaydedin. Makalenin ilerisinde sunucumuza WinSCP ile bağlanmamız gerekecek, bunun için root şifresi bize lazım.

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

![image](https://user-images.githubusercontent.com/101462877/180668809-7a1b406a-0084-4154-9ceb-db1ff222f765.png)

Eğer node -v kodunu denediğinizde böyle bir çıktı alıyorsanız, `apt install nodejs` kodunu girip tekrar deneyin.



# Sunucumuzun NEAR Stake Wars node kurulumu için yeterli olup olmadığına bakmak isterseniz bu kodu girebilirsiniz, girmenizi tavsiye ederim:
```
lscpu | grep -P '(?=.*avx )(?=.*sse4.2 )(?=.*cx16 )(?=.*popcnt )' > /dev/null \
  && echo "Supported" \
  || echo "Not supported"
```

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
Node'un çalışması için bir çalışma dizini ve konfigürasyon dosyaları gerekir. Bunlar için aşağıdaki kodu çalıştırıyoruzç
```
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
```
![image](https://user-images.githubusercontent.com/101462877/180668443-c48b5a71-6958-4b8e-accf-3a6514b23474.png)

Burada bu tür bir çıktı ile karşılaşacaksınız, karşılaşmadıysanız sorun var demektir.

