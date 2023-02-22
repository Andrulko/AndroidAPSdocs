# AAPS na chytrých hodinkách se systémem Wear OS

Aplikaci AndroidAPS lze nainstalovat na chytré hodinky se systémem **Wear OS**. AAPS na hodinkách umožňuje:

* **zobrazovat různé informace**: pomocí [vlastních ciferníků](#aaps-watchfaces) nebo standardních ciferníků s možností používat různé [komplikace](#complications)
* **ovládat AAPS na telefonu z hodinek**: vydání bolusu, nastavení dočasného cíle atd.

### Dříve než si koupíte hodinky…

* Některé funkce, jako např. *komplikace*, vyžadují Wear OS verze 2.0 nebo vyšší
* Google od verze 2.x přejmenoval *Android Wear 1.x* na *Wear OS*, takže pokud bude někde uvedeno *Android Wear*, zřejmě se jedná o starší verzi systému 1.x
* Jestliže je v popisu hodinek uvedeno, že jsou kompatibilní se systémy *Android* a *iOS*, **neznamená to**, že hodinky používají systém *Wear OS* - stejně tak se může jednat o nějaký jiný typ OS upraveného daným výrobcem, **který není kompatibilní s aplikací AAPS pro hodinky!**
* Check [list of tested phones and watches](../Getting-Started/Phones.md#list-of-tested-phones) and [ask community](../Where-To-Go-For-Help/Connect-with-other-users.md) if in doubt if your watch will be supported

### Sestavení verze AAPS pro Wear OS

The Wear OS App of AAPS has been seperated from the AAPS build for the Android mobile. Therefore you have to generate a second signed APK. Select as module "AndroidAPS.wear" and as build variant "fullRelease" and a second apk file for the Wear OS clock is generated when [building the APK](../Installing-AndroidAPS/Building-APK.md) (or "pumpcontrolRelease" which will allow you to just remote control the pump without looping).

Od března 2021 již není možné AAPS pro hodinky stáhnout z Google Play Store. Můžete to obejít pomocí [Wear instalátoru](https://youtu.be/8HsfWPTFGQI), který je potřeba nainstalovat do telefonu i hodinek. The Wear Installer app can be downloaded from the Google Play Store. The linked video from Malcolm Bryant the developer of Wear Installer gives you detailed instructions to a) download the apk to your mobile b) setup the Android Debugger on the wear c) use Wear Installer on mobile and wear to sideload the AAPS wear app to the mobile. Jakmile vyberete AndroidAPS jako aplikaci k nahrání na hodinky, budete moct použít ciferník, komplikace a ovládání AAPS.

### Nastavení na telefonu

Within AndroidAPS, in the ConfigBuilder you need to [enable Wear plugin](../Configuration/Config-Builder.md#wear).

## Ovládání AAPS z hodinek

AndroidAPS je navržený, aby ho bylo možné *ovládat* hodinkami Android Wear. Chcete-li z hodinek zadávat bolus atd., musíte v „Nastavení wear“ aktivovat volbu „Ovládání z hodinek“.

Z hodinek lze ovládat následující funkce:

* nastavovat dočasné cíle
* use the bolus calculator (calculation variables can be defined in [settings](../Configuration/Config-Builder.md#wear) on the phone)
* zadávat eSacharidy
* podávat bolus (inzulín + sacharidy)
* měnit nastavení hodinek
* monitorovat stav 
    * kontrolovat stav pumpy
    * kontrolovat stav smyčky
    * kontrolovat a měnit profil, CPP (Circadian Percentage Profile = posun času + procentní změna)
    * zobrazit TDD (celková denní dávka = bolus + bazál za den)

## Ciferníky AAPS

Lze si vybrat z několika ciferníků (watchfaces), které zobrazují průměrnou hodnotu delta, IOB, aktuálně aktivní bazál a bazální profil + graf hodnot glykémie z CGM.

Ujistěte se, že nemáte zakázané oznámení AndroidAPS na hodinkách. Potvrzování akcí (např. bolusu, dočasného cíle) se objeví jako notifikace, které je nutné odsunout a potvrdit klepnutím.

Chcete-li se rychleji dostat do nabídky AAPS, dvakrát klepněte na hodnotu glykémie. Dvojitým klepnutím na graf glykémie změníte časový rozsah grafu.

## Dostupné ciferníky

![Dostupné ciferníky](../images/Watchface_Types.png)

(new-watchface-as-of-androidaps-2-8)=

### Nový watchface od AndroidAPS 2.8

![Watchface Digital Style](../images/Watchface_DigitalStyle.png)

* Barvy, čáry a kruhy lze konfigurovat v nabídce nastavení pod ozubeným kolečkem v nabídce pro výběr ciferníku.

## Ciferník AAPSv2 – Popis

![Legend AndroidAPSv2 watchface](../images/Watchface_Legend.png)

A - time since last loop run

B - CGM reading

C - minutes since last CGM reading

D - change compared to last CGM reading (in mmol or mg/dl)

E - average change CGM reading last 15 minutes

F - phone battery

G - basal rate (shown in U/h during standard rate and in % during TBR)

H - BGI (blood glucose interaction) -> the degree to which BG “should” be rising or falling based on insulin activity alone.

I - carbs (carbs on board | e-carbs in the future)

J - insulin on board (from bolus | from basal)

## Vstup do hlavní nabídky AAPS

To access main menu of AAPS you can use on of following options:

* poklepejte na hodnotu glykémie
* vyberte ikonu AAPS v nabídce aplikací na hodinách
* klepněte na komplikaci AAPS (je-li nastavena tak, aby umožňovala vstup do nabídky)

## Nastavení (na hodinkách)

To access to the watchface settings, enter AAPS main menu, slide up and select "Settings".

Filled star is for enabled state (**On**), and hollow star icon indicates that setting is disabled (**Off**):

![Settings on/off](../images/Watchface_Settings_On_Off.png)

### Doplňkové parametry AAPS

* **Vibrovat při bolusu** (výchozí hodnota `Zap`):
* **Jednotky pro Akce** (výchozí hodnota `mg/dl`): jestliže je tato možnost **Zap**, jednotka pro akce je `mg/dl`, je-li možnost **Vyp**, jednotka je `mmol/l`. Používá se při nastavování dočasných cílů z hodinek.

### Nastavení ciferníku

* **Zobrazovat datum** (výchozí hodnota `Vyp`): poznámka: datum není k dispozici na všech cifernících
* **Zobrazovat IOB** (výchozí hodnota `Zap`): Možnost zobrazit hodnotu IOB (podrobnější nastavení viz sekce Wear v nastavení AAPS na telefonu)
* **Zobrazovat COB** (výchozí hodnota `Zap`): Možnost zobrazit hodnotu COB
* **Zobrazovat Deltu** (výchozí hodnota `Zap`): Možnost zobrazit rozdíl glykémií za posledních 5 minut
* **Zobrazovat prům. Deltu** (výchozí hodnota `Zap`): Možnost zobrazit průměrný rozdíl glykémií za posledních 15 minut
* **Zobrazovat baterii telefonu** (výchozí hodnota `Zap`): Nabití baterie telefonu v %. Při poklesu pod 30 % se zobrazuje červeně.
* **Zobrazovat baterii Rigu** (výchozí hodnota `Vyp`): Baterie Rigu je souhrnný údaj vyjadřující stav baterie telefonu, pumpy a senzoru (obecně tu nejnižší z těchto 3 hodnot)
* **Zobrazovat bazály** (výchozí hodnota `Zap`): Možnost zobrazit aktuální bazální dávku (v U/h nebo v %, je-li aktivní TBR)
* **Zobrazovat stav smyčky** (výchozí hodnota `Zap`): Zobrazuje, kolik minut uběhlo od posledního spuštění smyčky (šipky kolem hodnoty se změní na červené, pokud uběhlo více než 15 min).
* **Zobrazovat glykémii** (výchozí hodnota `Zap`): Možnost zobrazit hodnotu glykémie
* **Zobrazovat trendovou šipku** (výchozí hodnota `Zap`): Možnost zobrazit šipku trendu glykémie
* **Zobrazovat stáří glykémie** (výchozí hodnota `Zap`): Zobrazuje, kolik minut oběhlo od posledního odečtu glykémie.
* **Tmavé pozadí** (výchozí hodnota `Zap`): Můžete přepnout z tmavého pozadí na bílé (kromě ciferníků Cockpit a Steampunk)
* **Zvýraznit bazály** (výchozí hodnota `Vyp`): Zlepšuje viditelnost bazálů a dočasných bazálních dávek
* **Skrýt oddělovač** (výchozí hodnota `Vyp`): Pro ciferníky AAPS, AAPSv2 a AAPS(Large), zobrazuje oddělovač s kontrastním pozadím (**Vyp**), nebo se stejnou barvou, jakou má pozadí (**Zap**)
* **Rozlišení grafu** (výchozí hodnota `3 hodiny`): V podnabídce můžete vybrat max. časové rozlišení grafu v rozmezí 1–5 hodin.

### Nastavení uživatelského rozhraní

* **Metoda zadávání**: Pomocí tohoto parametru můžete zvolit pozici tlačítek "+" a "-" při zadávání hodnot pro AAPS (dočasný cíl, inzulin, sacharidy...)

![Input design options](../images/Watchface_InputDesign.png)

### Parametry konkrétních ciferníků

#### Ciferník Steampunk

* **Podrobnost Delty** (výchozí hodnota `Střední`)

![Steampunk_gauge](../images/Watchface_Steampunk_Gauge.png)

#### Ciferník Circle

* **Velká čísla** (výchozí hodnota `Vyp`): Zvětšená velikost textu kvůli lepší čitelnosti
* **Kruh historie** (výchozí hodnota `Vyp`): Grafické zobrazení historie glykémie pomocí šedých kruhů uvnitř zeleného hodinového kruhu
* **Světlý kruh historie** (výchozí hodnota `Zap`): Decentnější kruh historie s tmavší šedou
* **Animace** (výchozí hodnota `Zap`): Je-li tato možnost povolena, bude kruhový ciferník animovaný, jestliže je tato funkcemi hodinkami podporována a hodinky nejsou v úsporném režimu s nízkým rozlišením

### Nastavení příkazů

* **Kalkulačka v nabídce** (výchozí hodnota `Zap`): Možnost povolit rozhraní bolusové kalkulačky v hlavní nabídce pro zadávání sacharidů a posílání bolusů z hodinek
* **Plnění v nabídce** (výchozí hodnota `Vyp`): Možnost provádět Plnění/Doplňování z hodinek
* **Jedna cíl. hodnota** (výchozí hodnota `Zap`):
    
    * `Zap`: pro dočasný cíl lze nastavit jedinou hodnotu
    * `Vyp`: pro dočasný cíl lze nastavit nízkou a vysokou hodnotu

* **Procento z kalkulace** (výchozí hodnota `Vyp`): Umožňuje upravit velikost bolusu vypočteného kalkulačkou (hodnota v procentech zadaná před potvrzením oznámení)

(complications)=

## Komplikace

*Complication* is a term from traditional watchmaking, where it describes addition to the main watchface - as another small window or sub-dial (with date, day of the week, moon phase, etc.). Wear OS 2.0 brings that metaphor to allow custom data providers, like weather, notifications, fitness counters and more - to be added to any watchfaces that support complications.

AndroidAPS Wear OS app supports complications since build `2.6`, and allow any third party watchface that supports complications to be configured to display AAPS related data (BG with the trend, IOB, COB, etc.).

Complications also serve as **shortcut** to AAPS functions. By tapping them you can open AAPS related menus and dialogs (depending on complication type and configuration).

![Complications_On_Watchfaces](../images/Watchface_Complications_On_Watchfaces.png)

### Typy komplikací

AAPS Wear OS app provides only raw data, according to predefined formats. It is up to third-party watchface to decide where and how to render complications, including its layout, border, color, and font. From many Wear OS complication types available, AAPS uses:

* `SHORT TEXT` - Obsahuje dva řádky textu, každý o délce 7 znaků, někdy se označuje jako hodnota a popisek. Obvykle se vykreslí uvnitř kroužku nebo malého ováleného pole – pod sebou nebo vedle sebe. Je to prostorově velmi omezená komplikace. AAPS se snaží odstranit zbytečné znaky tak, aby se do zobrazení vešly: zaokrouhlením hodnot, odstraněním úvodních a koncových nul z hodnot atd.
* ` DLOUHÝ TEXT `-Obsahuje dva řádky textu, každý o 20 znacích. Obvykle se vykreslují uvnitř obdélníku nebo dlouhého oválného pole pod sebou. Používá se pro další podrobnosti a text.
* ` HODNOTA ROZSAHU `-Používá se pro hodnoty z předem definovaného rozsahu, například procento. Obsahuje ikonu, popisek a je obvykle vykreslen jako kruhový ukazatel průběhu.
* ` VELKÝ OBRÁZEK `-Vlastní obrázek na pozadí, který lze použít (je-li podporován watchfacem) jako pozadí.

### Nastavení komplikací

To add complication to watchface, configure it by long press and clicking the gear icon below. Depending on how specific watchface configures them - either click on placeholders or enter the watchface setup menu for complications. AAPS complications are grouped under the AAPS menu entry.

When configuring complications on watchface, Wear OS will present and filter the list of complications that can be fit into selected complication place on watchface. If specific complications cannot be found on the list, it is probably due to its type that cannot be used for the given place.

### Komplikace AAPS

AndroidAPS provides following complications:

![AAPS_Complications_List](../images/Watchface_Complications_List.png)

* **BR, CoB & IoB** (`KRÁTKÝ TEXT`, otevře *Menu*): zobrazuje *hodnotu bazálu* na prvním řádku a *aktuální množství sacharidů* a *aktivní množství inzulínu* na druhém řádku.
* **Glykémie** (`KRÁTKÝ TEXT`, otevře *Menu*): znázorňuje *glykémii* , *trendovou* šipku na prvním řádku a *čas odečtu* a *hodnotu změny glykémie* na druhém řádku.
* **CoB & IoB** (`KRÁTKÝ TEXT`, otevře *Menu*): zobrazuje *aktivní sacharidy* na prvním řádku *aktivní inzulín* na druhém řádku.
* **Detailní CoB** (`KRÁTKÝ TEXT`, otevře *Wizard*): zobrazuje aktuálně aktivní sacharidy *aktivní sacharidy* na prvním řádku a plánované (budoucí, eCarbs) sacharidy na druhém řádku.
* **Ikona CoB** (`KRÁTKÝ TEXT`, otevře *Wizard*): Zobrazuje *aktivní sacharidy* pomocí statické ikony.
* **Úplný stav** (`DLOUHÝ TEXT`, otevře *Menu*): Zobrazí většinu údajů dohromady: *glykémii* a *trendovou* šipku, *hodnotu změny glykémie* a *čas odečtu* na prvním řádku. Na druhém řádku * aktivní sacharidy *, * aktivní inzulín * a * hodnotu bazálu *.
* **Úplný stav (převrácené)** (`DLOUHÝ TEXT`, otevře *Menu*): Stejné hodnoty jako standardní *Úplný stav*, ale řádky jsou převrácené. Může být použit pro ciferníky, které ignorují jeden ze dvou řádků v `DLOUHÝ TEXT`
* **Detailní IoB** (`KRÁTKÝ TEXT`, otevře *Bolus*): Zobrazuje celkové množství *aktivního inzulínu* na prvním řádku a celkové *IoB* z *bolusu* a *bazálu* na druhém řádku.
* **Ikona IoB** (`KRÁTKÝ TEXT`, otevře *Bolus*): Zobrazuje *aktivní inzulín* jako statickou ikonu.
* **Baterie Uploaderu/Telefonu** (`HODNOTA ROZSAHU`, otevře *Status*): Znázorňuje nabití baterie v procentech na AAPS telefonu (uploader), jak je uvedeno v AAPS. Zobrazí se jako jako procentuální ukazatel s ikonou baterie znázorňující hodnotu. Toto není zobrazováno v reálném čase, ale když se změní jiné důležité hodnoty AAPS (obvykle: každých ~5 minut s novým odečtem </em>glykémie</0> ).

Additionally, there are three complications of `LARGE IMAGE` kind: **Dark Wallpaper**, **Gray Wallpaper** and **Light Wallpaper**, displaying static AAPS wallpaper.

### Nastavení související s komplikacemi

* **Akce po klepnutí na komplikaci** (výchozí `Výchozí`): Rozhodne, které dialogové okno se otevře, když uživatel poklepe na komplikaci: 
    * *Výchozí*: specifické akce pro typ kompilace *(viz seznam výše)*
    * *Menu*: Hlavní nabídka AAPS
    * *Wizard*: bolusový průvodce – bolusová kalkulačka
    * *Bolus*: přímé zadávání bolusu
    * *eCarb*: dialogové okno konfigurace eCarb
    * *Status*: dílčí nabídka stavu
    * *None*: Zakáže akci klepnutím na komplikace AAPS
* **Unicode v komplikacích** (výchozí hodnota `On`): Pokud je`On`, komplikace bude používat Unicode znaky pro symboly jako `Δ` Delta, `⁞` vertikální oddělovač teček nebo `⎍` symbol hodnoty bazálu. Vykreslování závisí na typu písma, které může být u každého ciferníku jiné. Tato volba umožňuje symboly Unicode `Vypnout` v případě potřeby – pokud písmo používané vlastním ciferníkem tyto symboly nepodporuje – aby se zabránilo chybám v zobrazení grafiky.

## Wear OS Tiles

Wear OS Tiles provide easy access to users' information and actions to get things done. The tiles are only available on Android smartwatches running on Wear Os version 2.0 and higher.

Tiles allow you to quickly access actions on the AAPS application without going through the watch face menu. The tiles are optional and can be added and configured by the user.

The tiles are used "next to" any watch face. To access a tile, when enabled, swipe right to left on your watch face to show them.

Please note; that the tiles do not hold the actual state of the AAPS phone app and will only make a request, which has to be confirmed on the watch before it is applied.

## How to add Tiles

Before using the tiles, you have to switch on "Control from Watch" in the "Wear OS" settings of Android APS.

![Wear phone preferences enabled](../images/wear_phone_preferences.jpg)

Depending on your Wear OS version, brand and smartphone there are two ways of enabling the tiles:

1. On your watch, from your watch face; 
    * Swipe right to left till you reach the "+ Add tiles" 
    * Select one of the tiles.
2. On your phone open the companion app for your watch. 
    * For Samsung open "Galaxy Wearable", or for other brands "Wear OS"
    * In the click on the section "Tiles", followed by "+ Add" button
    * Find the AAPS tile you like to add by selecting it. ![Wear phone add tile](../images/wear_companion_app_add_tile.png) The order of the tiles can be changed by dragging and dropping

The content of the tiles can be customized by long-pressing a tile and clicking the "Edit" or "gear icon" button.

### APS(Actions) Tile

The action tile can hold 1 to 4 user-defined action buttons. To configure, long-press the tile, which will show the configuration options. Similar actions are also available through the standard watch menu.

Actions supported in the Action tile can request the AAPS phone app for:

* **Calc**; do a bolus calculation, based on carb input and optional a percentage [1]
* **Insulin**; request insulin delivery by entering the unit of insulin
* **Treatment**; request both insulin delivery and add carbs
* **Carbs**; add (extended) carbs
* **TempT**; set a custom temporary target and duration

![Wear action tile, sample calculator](../images/wear_actions.png)

[1] Via, the Wear OS menu, set the "Calculator Percentage" option to "ON" to show the percentage input in the bolus calculator. The default percentage is based on the phone settings in the"Overview" section ["Deliver this part of the bolus wizard result %"](Config-Builder.html#advanced-settings) When the user does not provide a percentage, the default value from the phone is used. Configure the other parameters for the bolus calculator in the phone app via "Preferences" "Wizard Settings".

### AAPS(Temp Target) Tile

The Temp Target Tile can request a temporary target based on AAPS phone presets. Configure preset time and targets through the phone app setting by going to "Preferences", "Overview", ["Default Temp-Targets"](Config-Builder.html#default-temp-targets) and set the duration and targets for each preset. Configure the visible actions on the tile through the tile settings. Long press the tile to show the configuration options and select 1 to 4 options:

* **Activity**; for sport
* **Hypo**; to raise the target during hypo treatment
* **Eating soon**; to lower the target to raise the insulin on board
* **Manual**; set a custom temporary target and duration
* **Cancel**; to stop the current temporary target

![Wear actions tile edit](../images/wear_tile_tempt_edit.png)

### AAPS(QuickWizard)Tile

The QuickWizard tile can hold 1 to 4 quick wizard action buttons, defined with the phone app[2]. See [QuickWizard](Config-Builder.html#quickwizard-settings). You can set standard meals (carbs and calculation method for the bolus) to be displayed on the tile depending on the time of the day. Ideal for the most common meals/snacks you eat during the day. You can specify if the quick wizard buttons will show on the phone, watch, or both. Please note that the phone can show only one quick wizard button at a time. The quick wizard setup also can specify a custom percentage of the insulin for the bolus. The custom percentage enables you to vary, for example, snack at 120%, slow absorbing breakfast 80% and hypo treatment sugar snack at 0%

![Wear actions tile and phone configuration](../images/quickwizard_watch_phone.png)

[2] Wear OS limits tiles update frequency to only once every 30 seconds. When you notice that the changes on your phone are not reflected on the tile, consider; waiting 30 seconds, using the "Resend all data" button from the Wear OS section of AAPS, or removing the tile and adding it again. To change the order of the QuickWizard buttons dragging an item up or down.

## Always on

Long battery life for Android Wear OS smartwatches is a challenge. Some smartwatches get as much as 30 hours before recharging. The display should be switched off for optimal power saving when not in use. Most watches support the “Always on” display.

Since AAPS version 3, we can use a “Simplify UI” during always-on-mode. This UI only contains the blood glucose, direction, and time. This UI is power-optimized with less frequent updates, showing less information and lightening fewer pixels to save power on OLED displays.

The simplified UI mode is available for the watch-faces: AAPS, AAPS V2, Home Big, Digital Style, Steampunk, and Cockpit. The simplified UI is optional and is configured through the watch face settings. (log press the watch face and click “edit” or the gear icon) Select the configuration “Simplify UI" and set it to “Always on” or “Always on and charging”.

### Night-time mode

While charging, it would be helpful if the display could stay “always-on” and show your blood glucose during the night. However, the standard watch-faces are too bright and have too much information, and the details are hard to read with sleepy eyes. Therefore, we added an option for the watch-face to simplify the UI only during charging when set in the configuration.

The simplified UI mode is available for the watch-faces: AAPS, AAPS V2, Home Big, Digital Style, Steampunk, and Cockpit. The simplified UI is optional and is configured through the watch face settings. (log press the watch face and click “edit” or the gear icon) Select the configuration “Simplify UI" and set it to “During charging” or “Always on and charging”

The Android developer options enable your watch to stay awake during charging. To make the developer options available, see https://developer.android.com/training/wearables/get-started/debugging. Set the “Stay awake when charging” to “on” in the developer options”.

Note: not all displays can handle always-on very well. It can cause screen burn-in, especially on the older OLED displays. The watches will generally dim the display to prevent burn-in; please check your owner’s manual, the manufacturing, or the internet for advice.

![Watchface Nightstand](../images/Watchface_nightstand.jpg)

![Simplified UI](../images/Watchface_simplified_ui.png)

### Tipy pro lepší chod a delší výdrž baterie

Wear OS watches are very power-constrained devices. The size of the watch case limits the capacity of the included battery. Even with recent advancements both on hardware and software side, Wear OS watches still require daily charging.

If an experienced battery span is shorter than a day (from dusk to dawn), here are some tips to troubleshoot the issues.

Main battery-demanding areas are:

* Aktivní displej se zapnutým podsvícením (LED), nebo max. intenzita (OLED)
* Vykreslování na obrazovce
* Bezdrátová komunikace přes Bluetooth

Since we cannot compromise on communication (we need up-to-date data) and want to have the most recent data rendered, most of the optimizations can be done in *display time* area:

* Originální ciferník je obvykle lépe optimalizován než vlastní, stažený z obchodu.
* Je lepší použít ciferníky, které omezují množství přenesených dat v režimu neaktivní/ztlumený režim.
* Uvědomte si, že při používaní dalších komplikací, jako jsou widgety počasí třetích stran nebo jiné, využíváte data z externích zdrojů.
* Začněte s jednoduššími ciferníky. Přidejte pouze jednu komplikaci a sledujte, jaký má vliv na výdrž baterie.
* Zkuste pro ciferník AAPS použít motiv **Tmavý** a také [**Odpovídající oddělovač**](#watchface-settings). Na zařízeních s OLED to omezí počet zapnutých pixelů a omezí vypalování.
* Zkuste, co lépe funguje na vašich hodinkách: Originální ciferník AAPS nebo jiný s AAPS komplikací.
* Sledujte několik dní, s různými profily aktivit. Většina hodinek aktivuje obrazovku při pohledu na ně, pohybu a dalších spouštěčích souvisejících s užíváním.
* Zkontrolujte globální nastavení systému, které ovlivňuje výkon: oznámení, časový limit podsvícení/aktivní zobrazení, je-li aktivována služba GPS apod.
* Check [list of tested phones and watches](../Getting-Started/Phones.md#list-of-tested-phones) and [ask community](../Where-To-Go-For-Help/Connect-with-other-users.md) for other users experiences and reported battery lifetime.
* **Nemůžeme garantovat, že data zobrazena na ciferníku nebo komplikaci jsou aktuální**. Konečné rozhodnutí o tom, kdy aktualizovat ciferník nebo komplikaci, je na operačním systému. I když se aplikace AAPS aktualizují, systém se může rozhodnout odložit nebo ignorovat aktualizace v zájmu úspory baterie. V případě pochybností nebo vybité baterie – vždy zkontrolujte hlavní AAPS v telefonu.

(troubleshooting-the-wear-app)=

## Řešení problémů s wear aplikací:

* Někdy pomůže znovu sesynchronizovat aplikace do hodinek, i když to ručně může být poněkud zdlouhavé: Android wear > Ikona ozubeného kola > Název hodinek > Synchronizovat aplikace.
* Povolte ADB ladění ve vývojářských možnostech (na hodinkách), připojte hodinky k počítači přes USB a spusťte Wear aplikaci, až budete mít na počítači otevřené Android Studio.
* Pokud se komplikace neaktualizují – nejdříve zkontrolujte, zda vůbec AAPS ciferník funguje.

### Sony Smartwatch 3

* Sony Smartwach 3 patří k nejoblíbenějším hodinkám používaným s AAPS.
* Společnost Google od podzimu 2020 již bohužel nepodporuje zařízení s OS 1.5. To vede k problémům při používání hodinek Sony SW3 s AndroidAPS 2.7 a vyšší.
* A possible workaround can be found on this [troubleshooting page](../Usage/SonySW3.md).

## Zobrazení dat z Nightscoutu

If you are using another looping system and want to *view* your looping detail on an Android Wear watch, or want to watch your child's looping, then you can build/download just the NSClient APK. To do this follow the [build APK instructions](../Installing-AndroidAPS/Building-APK.md) selecting the build variant "NSClientRelease". Lze si vybrat z několika ciferníků (watchfaces), které zobrazují průměrnou hodnotu delta, IOB, aktuálně aktivní bazál a bazální profil + graf hodnot glykémie z CGM.

# Pebble

Pebble users can use the [Urchin watchface](https://github.com/mddub/urchin-cgm) to *view* looping data (if uploaded to Nightscout), but you will not be able to interact with AndroidAPS through the watch. You can choose fields to display such as IOB and currently active temp basal rate and predictions. If open looping you can use [IFTTT](https://ifttt.com/) to create an applet that says if Notification received from AndroidAPS then send either SMS or pushover notification.