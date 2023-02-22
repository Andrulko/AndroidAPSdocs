# DanaRS and Dana-i Pump

*These instructions are for configuring the app and your pump if you have a DanaRS from 2017 onwards or the newer Dana-i. Visite [Bomba de insulina DanaR](./DanaR-Insulin-Pump) si en su lugar tiene una DanaR original.*

**El nuevo firmware de Dana RS v3 se puede utilizar desde AndroidAPS versión 2.7 en adelante.**

**New Dana-i can be used from AndroidAPS version 3.0 onwards.**

* In DanaRS/i pump "BASAL A" is used by the app. Existing data gets overwritten.

## Pairing pump

* On AndroidAPS homescreen click hamburger menu on the top left corner and go to Config Builder.
* In pump section select 'Dana-i/RS'.
* Click on gear wheel to get directly to the pump settings or return to homescreen.
    
    ![AAPS config builder Dana-i/RS](../images/DanaRS_i_ConfigB.png)

* Go to 'DANA-i/RS' tab.

* Select preferences menu by tapping the 3 dots in the top right. 
* Select 'Dana-i/RS Preferences'.
* Click on "Selected pump".
* In the pairing window click on the entry for your pump.
    
    ![AAPS pair Dana-i/RS](../images/DanaRS_i_Pairing.png)

* **You have to confirm the pairing on the pump!** That's just the way you are used to from other bluetooth pairings (i.e. smartphone and car audio).
    
    ![Dana RS confirmation pairing](../images/DanaRS_Pairing.png)

* Follow the pairing process based on the type and firmware of your pump:
    
    * For DanaRS v1 select pump password in preferences and set your password.
    * For DanaRS v3 you have to type 2 sequences of numbers and letters displayed on pump to AndroidAPS pairing dialog.
    * For Dana-i standard Android pairing dialog appear and you have to enter 6-digit number displayed on pump.

* Select Bolus Speed to change the default bolus speed used (12sec per 1u, 30sec per 1u or 60sec per 1u).

* Set basal step on pump to 0.01 U/h using Doctors menu (see pump user guide).
* Set bolus step on pump to 0.05 U/h using Doctors menu (see pump user guide).
* Habilitar bolos extendidos en bomba

(default-password)=

### Default password

* Para DanaRS con el firmware v1 y v2 la contraseña predeterminada es 1234.
* For DanaRS with firmware v3 or Dana-i the default password is a combination of production month and production date (i.e. month 01 and day 24).
    
    * Open main menu on pump > review > information. 
    * Number 3 is production date. 
    * For v3/i this password is used only for locking menu on pump. It's not used for communication and it's not necessary to enter it in AndroidAPS.

(change-password-on-pump)=

## Change password on pump

* Press OK button on pump
* In main menu select "OPTION" (move right by pressing arrow button several times)
    
    ![DanaRS Main Menu](../images/DanaRSPW_01_MainMenu.png)

* In options menu select "USER OPTION"
    
    ![DanaRS Option Menu](../images/DanaRSPW_02_OptionMenu.png)

* Use arrow button to scroll down to "11. password"
    
    ![DanaRS 11. Password](../images/DanaRSPW_03_11PW.png)

* Press OK to enter old password.

* Enter **old password** (Default password see [above](#default-password)) and press OK
    
    ![DanaRS Enter old password](../images/DanaRSPW_04_11PWenter.png)

* If wrong password is entered here there will be no message indicating failure!

* Set **new password** (Change numbers with + & - buttons / Move right with arrow button).
    
    ![DanaRS New password](../images/DanaRSPW_05_PWnew.png)

* Confirm with OK button.

* Save by pressing OK button again.
    
    ![DanaRS Save new password](../images/DanaRSPW_06_PWnewSave.png)

* Move down to "14. EXIT" and press OK button.
    
    ![DanaRS Exit](../images/DanaRSPW_07_Exit.png)

(dana-rs-specific-errors)=

## Errores específicos de Dana RS

### Error durante la administración de insulina

In case the connection between AAPS and Dana RS is lost during bolus insulin delivery (i.e. you walk away from phone while Dana RS is pumping insulin) you will see the following message and hear an alarm sound.

![Alarm insulin delivery](../images/DanaRS_Error_bolus.png)

* En la mayoría de los casos, se trata sólo de un problema de comunicación y se inyecta la cantidad correcta de insulina.
* Compruebe el historial de la bomba (ya sea en la bomba o a través de la pestaña Dana > historial de bomba > bolos) para ver si se ha administrado el bolo correctamente.
* Delete error entry in [treatments tab](../Getting-Started/Screenshots.md#carb-correction) if you wish.
* La cantidad real será leída y grabada en la siguiente conexión. Para forzar esto pulse el icono BT en la pestaña de dana o simplemente espere a la siguiente conexión.

## Nota especial al cambiar de teléfono

When switching to a new phone the following steps are necessary:

* [Export settings](../Usage/ExportImportSettings.md#export-settings) on your old phone
* Transfer settings from old to new phone

### DanaRS v1

* **Manually pair** Dana RS with the new phone
* As pump connection settings are also imported AAPS on your new phone will already "know" the pump and therefore not start a bluetooth scan. Therefore new phone and pump must be paired manually.
* Install AndroidAPS on the new phone.
* [Import settings](../Usage/ExportImportSettings.md#import-settings) on your new phone

### DanaRS v3, Dana-i

* Start pairing procedure like decribed [above](#pairing-pump).
* Sometimes it may be necessary to clear pairing information in AndroidAPS by long-click BT icon on Dana-i/RS tab.

## Cambio de zona horaria al viajar con la bomba Dana RS

For information on traveling across time zones see section [Timezone traveling with pumps](../Usage/Timezone-traveling.md#danarv2-danars).