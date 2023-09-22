# Gelecekteki (olası) Pompa Sürücüleri

Burada üretimde olan bazı pompaların listesi ve herhangi bir döngü sistemindeki destek durumu ile AAPS'deki durumu anlatılmaya çalışılacaktır. Bölüm sonunda bir pompanın "Döngü özellikli" olması için gerekli olan bazı bilgiler vardır.

## Döngü yapılabilen Pompalar

* * *

### EOPatch2 ([Ana sayfa](http://www.eoflow.com/eng/main/main.html))

** Döngü durumu: ** Yeni bir döngü adayıdır. Kullandıkları uzaktan kumanda aslında değiştirilmiş Android cihazıdır. (Pompa şu anda yalnızca Kore'de mevcuttur). Söz vermiyoruz ancak AAPS 3.2'ye bakabilirsiniz.

**AAPS için donanım gereksinimi:** Muhtemelen yok. BT etkin görünüyor.

* * *

### Ypsomed Pompası ([Pompa ana sayfası](https://www.ypsomed.com/en/diabetes-care-mylife.html))

**Döngü durumu:** Sürüm 1 - 1.5 (2018/2Ç) döngü adayı değildir. BT iletişimine sahip olsalar da, iletişim çok sınırlı ve tek yönlüdür: Pompa->Uygulama. Haziran 2022'de (Almanya'da) şirket, uygulamalarından bolus ve GBO ayarlamaya olanak tanıyan DOSE (1.6) adlı yeni sürümünü yayınladı. Kendi Döngülerini uygulama planları iptal edildi ve CamAPS (destek zaten uygulandı) ile ortak olmaya ve döngü çözümlerini kullanmaya karar verdiler. Daha fazla bilgi için bu [sayfaya](https://www.mylife-diabetescare.com/en/loop-program.html) bakın

**AAPS için donanım gereksinimi:** Yok. It's BT enabled.

**Yorumlar:** Pompanın doz sürümüne çok ağır şifreleme eklenmiştir. Bu nedenle bu pompa yakın gelecekte (veya hiçbir zaman) büyük bir olasılıkla AAPS tarafından desteklenmeyecektir. Ypsomed ile çalışan ve tıbbi denemelere yardımcı olan geliştiricimiz vardı, bu yüzden belki onun sürücüsünün yayınlanmasına izin verilir, ancak bu küçük bir olasılıktır. Hakkında daha fazla bilgiyi discord "ypsopump-talk" kanalında bulabilirsiniz.

* * *

### Kaleido ([Ana Sayfa](https://www.hellokaleido.com/))

**Loop status:** Currently not supported by any of loop system. Pump is a Loop candidate, but since protocol is unknown at the time, I am not seeing this pump supported very soon.

**AAPS için donanım gereksinimi:** Muhtemelen yok. It's BT enabled.

* * *

### Equil (pump from Aidex/GlucoRx/MicroTechMD) ([Homepage](https://www.glucorx.ie/glucorx-equil/))

**Loop status:** Is a Loop candidate.

**AAPS için donanım gereksinimi:** Yok. BT etkin görünüyor.

**Comment:** Some people started looking into supporting pump in AAPS, but this is still in beginning phases. You can find more information on our discord in channel "equil".

* * *

### Accu-Chek Solo ([Homepage](https://www.roche.com/media/releases/med-cor-2018-07-23.htm))

**Loop status:** Is a Loop candidate.

**AAPS için donanım gereksinimi:** Yok. BT etkin görünüyor.

**Comments:** There are some developers looking into decoding the protocol, but so far this is only in preliminary phases.

* * *

### Tandem: t:slim X2 ([Homepage](https://www.tandemdiabetes.com/))

**Loop status:** Not yet loopable.

While in the past company has decided not to allow their pumps to be controlled by external devices, it seems that last few years have been a game changer. Company decided to upgrade their t:slim X2 pump to be able to be controlled remotely (via t:connect app), which means that avenues are opened that we might be able to look forward to have control of pump via AAPS in the future. New pump firmware is planned to be released soon (this or next year, before their tubeless pump t:sport comes out). There are no details yet, what operations will be possible from t:connect (Bolus definitely, everything else unknown).

**AAPS için donanım gereksinimi:** Yok. BT etkin görünüyor.

* * *

### Tandem: t:Mobi & t:slim X3 & t:Mobi Tubeless ([Homepage](https://www.tandemdiabetes.com/about-us/pipeline))

**Loop status:** All 3 pumps will be Loop candidates.

They plan to release t:Mobi first (previously called t:sport) at end of 2022 or in 2023. Afterwards they will release t:slim X3 (2023 maybe) and after that t:Mobi Tubeless. t:mobi's will be controlable only over phone app, while X3 will look similar as X2, with some new nifty features (remote update of firmware, remote control over phone app, etc).

**AAPS için donanım gereksinimi:** Yok. BT etkin görünüyor.

* * *

### Medtronic Bluetooth

**Comments:** This is pump that will come out in next few years and is planned to be supported in Tidepool Loop software ([see this article](https://www.tidepool.org/blog/tidepool-loop-medtronic-collaboration).

### Willcare Insulin pump ([Homepage](http://shinmyungmedi.com/en/))

**Loop status:** At the moment its not Loop candidate, but we were contacted by their staff and they interested in extending their pump to be loopable (at the moment I think its missing only get/set profile commands).

**AAPS için donanım gereksinimi:** Yok. BT etkin görünüyor.

**Comments:** Since company is interested in integration with AAPS, they might do implementation themselves.

* * *

## Pompalar artık satılmıyor (şirketler artık çalışmıyor)

### Cellnovo Pump ([see businesswire.com](https://www.businesswire.com/news/home/20190328005829/en/Cellnovo-Stops-Manufacturing-and-Commercial-Operations))

**Loop status:** Currently not supported by any of loop system. Pump is a Loop candidate, but since protocol is unknown at the time, I am not seeing this pump supported very soon.

**AAPS için donanım gereksinimi:** Muhtemelen yok. It's BT enabled.

**Note about product:** It seems that company decided to exit the Pump Business. You can see more in this [article](https://diabetogenic.wordpress.com/2019/04/01/and-then-cellnovo-disappeared/?fbclid=IwAR12Ow6gVbEOuD1zw7aNjBwqj5_aPkPipteHY1VHBvT3mchlH2y7Us6ZeAU)

## Döngü yapılamayan pompalar

### Animas Vibe

**Loop status:** Not loopable. No remote control possibility. **Note:** Pump is not being sold anymore. Company stopped working in Pump business (J&J).

* * *

### Animas Ping

**Loop status:** Not loopable. It has bolus possibility, but no TBR one. **Note** Stopped being sold when Vibe came out.

## Döngü yapılabilecek pompalar için gereksinimler

**Prerequisite**

- Pompanın bir çeşit uzaktan kumandayı desteklemesi gerekir. (BT, Radyo frekansı, vb)
- Saldırıya uğramış/dokümante edilmiş/vb. protokeller.

**Minimal requirement**

- Geçici Bazal Oranı Ayarla
- Durum Al
- Geçici Bazal Oranı İptal Et

**For oref1(SMB) or Bolusing:**

- Bolusu Ayarla

**Good to have**

- Bolus iptal Etme
- Bazal Profili Alma (ne zaman gerekirse)
- Bazal Profili Ayarlama (olması güzel)
- Geçmişi Okuma 

**Other (not required but good to have)**

- Yayma Bolusu Ayarlama
- Yayma Bolusu iptal etme
- Geçmişi Okuma
- GTD'yi okuma

* * *

### Other pumps support

If you have any other pumps you would like to see status on, please contact us on discord.