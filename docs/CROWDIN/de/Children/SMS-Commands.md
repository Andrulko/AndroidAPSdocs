# SMS-Befehle

## Sicherheitshinweise

- AAPS allows you to control a child's phone remotely via text message. Wenn Du diesen SMS-Kommunikator aktivierst, denke immer daran, dass das Telefon, das für Remote-Befehle eingerichtet ist, gestohlen werden kann. Schütze dieses mit einem zumindest mit einem sicheren PIN-Code. Es wird ein starkes Passwort oder biometrischer Schutz empfohlen.
- Außerdem ist es empfehlenswert, eine [zweite Telefonnummer](SMS-Commands-authorized-phone-numbers) für SMS Kommandos einzurichten. Dann kannst Du die zweite Nummer nutzen, um den SMS-Kommunikator [vorübergehend zu deaktivieren](SMS-Commands-other), falls Dein Smartphone verloren geht oder gestohlen wird.
- AAPS will also inform you by text message if your remote commands, such as a bolus or a profile change, have been carried out. Es ist ratsam, dies so einzustellen, dass Bestätigungstexte an mindestens zwei verschiedene Telefonnummern gesendet werden, falls eines der Empfangstelefone gestohlen wird.
- **If you bolus through SMS Commands you must enter carbs through Nightscout (AAPSClient, Website...)!** If you fail to do so IOB would be correct with too low COB potentially leading to not performed correction bolus as AAPS assumes that you have too much active insulin.
- As of AAPS version 2.7 an authenticator app with a time-based one-time password must be used to increase safety when using SMS commands.

## SMS-Kommandos einrichten

```{image} ../images/SMSCommandsSetup.png
:alt: SMS-Kommandos einrichten
```

- Most of the adjustments of temp targets, following AAPS etc. can be done on [AAPSClient app](../Children/Children.md) on an Android phone with an internet connection.
- Boli können nicht über Nightscout abgegeben werden, aber Du kannst dafür SMS-Kommandos verwenden.
- If you use an iPhone as a follower and therefore cannot use AAPSClient app, there are additional SMS commands available.
- Gehe dazu in den Systemeinstellungen deines Android-Telefons zu Apps > AndroidAPS > Berechtigungen und aktiviere dort SMS.

(SMS-Commands-authorized-phone-numbers)=

### Erlaubte Telefonnummern

- In AAPS go to **Preferences > SMS Communicator** and enter the phone number(s) that you will allow SMS commands to come from (separated by semicolons - i.e. +6412345678;+6412345679)

- Note that the "+" in front of the number may or may not be required based on your location. To determine this send a sample text which will show the received format in the SMS Communicator tab.

- Aktiviere 'Erlaube Fernsteuerung per SMS zulassen'.

- Wenn Du mehr als eine Nummer verwenden möchtest:

  - Gib nur eine der Telefonnummern ein.

  - Führe ein SMS-Kommando aus um sicher zu stellen, dass die Kommandos mit dieser Telefonnummer funktionieren.

  - Gib die zusätzliche(n) Telefonnummer(n) getrennt durch Semikolon ohne Leerzeichen ein.

    ```{image} ../images/SMSCommandsSetupSpace2.png
    :alt: SMS-Kommandos Setup mehrerer Nummern
    ```

### Minuten zwischen Bolus-Kommandos

- Du kannst den minimalen Zeitabstand zwischen zwei über SMS durchgeführte Boli definieren.
- Aus Sicherheitsgründen musst Du mindestens zwei erlaubte Telefonnummern hinzufügen, um diesen Wert zu bearbeiten.

### Zusätzliche obligatorische PIN am Token-Ende

- Aus Sicherheitsgründen muss dem Antwortcode eine PIN folgen.

- PIN-Regeln:

  - 3 bis 6 Ziffern
  - nicht dieselben Ziffern (z.B. 1111)
  - keine Ziffernfolge (z.B. 1234)

### Konfiguration der Authenticator App

- Zwei-Faktor-Authentifizierung wird zur Verbesserung der Sicherheit verwendet.

- Du kannst jede Authentifizierungs-App, die RFC 6238 TOTP-Token unterstützt, verwenden. Beliebte kostenlose Apps sind:

  - [Authy](https://authy.com/download/)
  - Google Authenticator - [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) / [iOS](https://apps.apple.com/de/app/google-authenticator/id388497605)
  - [LastPass Authenticator](https://lastpass.com/auth/)
  - [FreeOTP Authenticator](https://freeotp.github.io/)

- Installiere die Authentifizierungs-App Deiner Wahl auf Deinem Follower-Smartphone und scanne den in AAPS angezeigten QR-Code.

- Teste das Einmal-Passwort, indem Du den in Deiner Authentifizierungs-App angezeigte Token und die PIN, die Du gerade in AAPS eingerichtet hast, eingibst. Beispiel:

  - Deine zwingend erforderliche PIN ist 2020
  - TOTP Token von der Authentifizierungs-App ist 457051
  - Trage 4570512020 ein

- Der rote Text "WRONG PIN" ändert sich **automatisch** in den grünen Text "OK", wenn das Einmal-Passwort korrekt ist. **Es gibt keine Taste, die Du drücken kannst!**

- Die Zeit auf beiden Telefonen muss synchron sein. Am einfachsten erfolgt dies direkt über das Mobilfunknetz. Zeitunterschiede können zu Authentifizierungsproblemen führen.

- Verwende die Schaltfläche "AUTHENTIKATORS ZURÜCKSETZEN", wenn Du bereits eingerichtete Berechtigungen entfernen möchten.  (Durch das Zurücksetzen des Authentikators werden ALLE erteilten Berechtigungen ungültig. Du musst sie alle neu einrichten.)

## SMS-Kommandos verwenden

- Send a SMS to the phone with AAPS running from your approved phone number(s) using any of the [commands](SMS-Commands-commands) below.

- Das AAPS-Smartphone wird antworten, um sich die Durchführung des übermittelten Kommandos bestätigen zu lassen oder um den angeforderten Status zu übermitteln.

- Bestätige falls erforderlich die Durchführung des übermittelten Kommandos, indem Du den angegebenen Code zurücksendest. Beispiel:

  - Deine zwingend erforderliche PIN ist 2020
  - TOTP Token von der Authentifizierungs-App ist 457051
  - Trage 4570512020 ein

**Hinweis**: Eine SMS-Flat auf beiden Telefonen kann nützlich sein, da u.U. viele SMS hin und her gesandt werden.

(SMS-Commands-commands)=
## Kommandos

Commands must be sent in English, the response will be in your local language if the response string is already [translated](translations-translate-strings-for-AAPS-app).

```{image} ../images/SMSCommands.png
:alt: Beispiele für SMS-Kommandos
```

### Loop

- LOOP STOP/DISABLE \* Antwort: Loop wurde deaktiviert.

- LOOP START/ENABLE \* Antwort: Loop wurde aktiviert

- LOOP-STATUS

  - Antwort hängt vom aktuellen Status ab

    - Loop ist deaktiviert.
    - Loop ist aktiviert.
    - Pausiert (%1$d min)

- LOOP SUSPEND 20 \* Antwort: Loop unterbrochen für 20 Minuten

- LOOP RESUME \* Antwort: Loop wurde fortgesetzt

### CGM-Daten

- BG \* Antwort: Letzter BZ: 5.6 4min her, Delta: -0,2 mmol, IOB: 0.20U (Bolus: 0.10U Basal: 0.10U)
- CAL 5.6 \* Antwort: Um die Kalibrierung 5.6 zu senden, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN. \* Antwort, nachdem der korrekte Code von AAPS empfangen wurde: Kalibrierung gesendet (**Falls xDrip installiert ist. In xDrip+ muss "Kalibrierungen akzeptieren" aktiviert sein.**)

### Basal

- BASAL STOP/CANCEL \* Antwort: Antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN, um die temporäre Basalrate zu beenden.
- BASAL 0.3 \* Antwort: Um eine Basalrate von 0.3IE/h für 30 Minuten zu setzen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- BASAL 0.3 20 Antwort: Um eine Basalrate von 0.3IE/h für 20 Minuten zu setzen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- BASAL 30% \* Antwort: Um die Basalrate von 30% für 30 Minuten zu setzen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- BASAL 30% 50 \* Antwort: Um die Basalrate von 30% für 50 Minuten zu setzen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.

### Bolus

Ein Bolus via SMS ist innerhalb von 15 Minuten nach der letzten Bolusgabe in AAPS oder nach dem letzten SMS-Kommando nicht möglich. Den Wert kannst Du nur anpassen, wenn mind. zwei Rufnummern eingetragen sind. Die Antwort hängt daher davon ab, wann der letzte Bolus abgegeben wurde.

- BOLUS 1.2 \* Antwort A: Um einen Bolus von 1,2 IE abzugeben, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN. \* Antwort B: Bolusabgabe aus der Ferne nicht verfügbar. Versuch es später nochmal.
- BOLUS 0.60 MEAL \* Mit dem optionalen Parameter MEAL wird ein Mahlzeiten TT gesetzt (Standardwerte sind 90 mg/dL / 5.0 mmol/L für 45 Minuten). \* Antwort A: Um einen Bolus von 0,6 IE abzugeben, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- CARBS 5 \* Antwort: Um 5g Kohlenhydrate um 12:45 einzugeben, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- CARBS 5 17:35/5:35PM \* Antwort: Um 5g Kohlenhydrate um 17:35 einzugeben, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- EXTENDED STOP/CANCEL \* Antwort: Antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN, um den erweiterten Bolus zu beenden.
- EXTENDED 2 120 \* Antwort: Um den erweiterten Bolus 2 IE für 120 Minuten abzugeben, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.

### Profile

- PROFILE STATUS \* Antwort: Profil1
- PROFILE LIST \* Antwort: 1. \` Profil1 \` 2. \` Profil2 \`
- PROFILE 1 \* Antwort: Um zum Profil 1 mit 100% zu wechseln, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- PROFILE 2 30 \* Antwort: Um zum Profil 2 mit 30% zu wechseln, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.

(SMS-Commands-other)=

### Andere

- TREATMENTS REFRESH \* Antwort: Behandlungen von NS aktualisieren
- AAPSClient RESTART \* Response: AAPSClient RESTART 1 receivers
- PUMP \* Antwort: Letzte Verbindung: vor 1 Min. Temp: 0.00E/h @11:38 5/30min IOB: 0.5E Reserv: 34E Batt: 100
- PUMP CONNECT \* Antwort: Pumpe erneut verbunden
- PUMP DISCONNECT *30* \* Um die Pumpe für *30* Minuten zu trennen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- SMS DISABLE/STOP \* Antwort: Um den SMS Remote Service zu deaktivieren, antworte mit dem Code Any. Beachte, dass Du die Fernsteuerung nur am AAPS Master-Smartphone wieder aktivieren kannst.
- TARGET MEAL/ACTIVITY/HYPO \* Antwort: Um ein MEAL/ACTIVITY/HYPO TT zu setzen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- TARGET STOP/CANCEL \* Antwort: Um das temporäre Ziel zu stoppen, antworte mit dem Code der Authenticator-App gefolgt von Deinem PIN.
- HELP \* Antwort: BG, LOOP, TREATMENTS, .....
- HELP BOLUS \* Antwort: BOLUS 1.2 BOLUS 1.2 MEAL

(SMS-Commands-troubleshooting)=
## Problembehandlung

### Mehrfach-SMS

Wenn Du die gleiche SMS immer und immer wieder empfängst (z.B. Profilwechsel), hast Du wahrscheinlich eine Endlosschleife mit einer anderen App eingerichtet. Das könnte zum Beispiel xDrip+ sein. Falls dies der Fall ist, stelle sicher, dass xDrip+ (oder eine andere App, die mit Nightscout verbunden ist), keine Behandlungsdaten hochlädt.

Wenn die andere App auf mehreren Smartphones installiert ist, musst Du den Upload auf allen deaktivieren.

### SMS-Kommandos funktionieren nicht auf Samsung-Smartphones

Es gab einen Hinweis, dass nach einem Update die SMS Kommandos auf einem Galaxy S10 nicht mehr funktioniert haben. Dies konnte durch Abschalten der Option 'als Chat Message senden' behoben werden.

```{image} ../images/SMSdisableChat.png
:alt: SMS als Chatnachricht deaktivieren
```
### Android Messages App

If you are having issues sending or receiving SMS commands with the Android Messages app disable end-to-end ecryption on both caregiver and child's phones.
 - open the specific SMS conversation in Messages
 - Select the options ellipisis in the top right corner
 - select "Details"
 - Activate "Only send SMS and MMS messages"
