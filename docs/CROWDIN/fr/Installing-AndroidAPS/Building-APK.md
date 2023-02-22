# Construire l'APK

## Construire vous-même au lieu de télécharger

**AndroidAPS n'est pas disponible en téléchargement en raison de la réglementation concernant les dispositifs médicaux. Il est légal de construire l'application pour votre usage personnel, mais vous ne devez en aucun cas donner une copie à d'autres personnes ! Voir la [page FAQ](../Getting-Started/FAQ.md) pour plus de détails.**

## Remarques importantes

* Utilisez **[Android Studio Version 2020.3.1](https://developer.android.com/studio/)** ou une version plus récente pour construire l'apk.
* [Windows 10 32-bit systems](../Installing-AndroidAPS/troubleshooting_androidstudio.md#unable-to-start-daemon-process) are not supported by Android Studio 2020.3.1

(recommended-specification-of-computer-for-building-apk-file)=

## Configuration recommandée de l'ordinateur pour construire un fichier apk

<table class="tg">
  
<thead>
  <tr>
    <th class="tg-baqh">OS (seulement 64 bits)</th>
    <th class="tg-baqh">Windows 8 ou supérieur</th>
    <th class="tg-baqh">Mac OS 10.14 ou supérieur</th>
    <th class="tg-baqh">N'importe quel Linux prend en charge Gnome, KDE, ou Unity DE;&nbsp;&nbsp;GNU C Library 2.31 ou ultérieure</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-baqh"><p align="center">CPU (seulement 64 bits)</td>
    <td class="tg-baqh">architecture processeur x86_64 ; Core Intel de 2ème génération ou plus récente, ou processeur AMD prenant en charge un <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-windows" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Hypervisor Windows</span></a></td>
    <td class="tg-baqh">Intel Core de 2ème génération ou plus récente, ou processeur AMD prenant en charge un <br><a href="https://developer.android.com/studio/run/emulator-acceleration#vm-mac" target="_blank" rel="noopener noreferrer"><span style="text-decoration:var(--devsite-link-text-decoration,none)">Hypervisor.Framework</span></a></td>
    <td class="tg-baqh">architecture du processeur x86_64, Intel Core de 2ème génération ou plus récent ou processeur AMD avec support pour la virtualisation AMD (AMD-V) et SSSE3</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">RAM</td>
    <td class="tg-baqh" colspan="3"><p align="center">8GB or more</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Disque</td>
    <td class="tg-baqh" colspan="3"><p align="center">Au moins 30 Go d'espace libre. Un SSD est recommandé.</td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Résolution</td>
    <td class="tg-baqh" colspan="3"><p align="center">Minimum 1280 x 800 <br></td>
  </tr>
  <tr>
    <td class="tg-baqh"><p align="center">Internet</td>
    <td class="tg-baqh" colspan="3"><p align="center">Haut débit</td>
  </tr>
</tbody>
</table>

Please be in mind that both **64 bit CPU and 64 bit OS are mandatory condition.** If your system DOES NOT meet this condition, you have to change affected hardware or software or the whole system. **It is strongly recommended to use SSD (Solid State Disk) instead of HDD (Hard Disk Drive) because it will take less time when you are building the APS installation apk file.** Recommended is just recommended and it is not a mandatory. However, you may still use a HDD when you are building apk file but note that the building process can take a long time to complete, although once started, you can leave it running unattended.

* * *

### Cet article est divisé en deux parties.

* La partie "aperçu" indique les étapes nécessaires pour construire le fichier APK.
* Dans la partie "pas à pas", vous trouverez les captures d'écran d'une installation complète. Les versions d'Android Studio - l'environnement de développement logiciel que nous utiliserons pour construire l'APK - changent très rapidement. Les exemples ne seront donc pas identiques à votre installation, mais cela devrait vous donner un bon point de départ. Android Studio fonctionne sous Windows, Mac OS X et Linux et il peut y avoir de petites différences entre chaque plateforme. Si vous trouvez que quelque chose d'important qui est incorrect ou manquant, merci d'informer le groupe facebook "utilisateurs AndroidAPS" ou dans les chats Discord [Android APS ou AndroidAPSwiki](https://discord.gg/4fQUWHZ4Mw) afin que nous puissions y remédier.

## Aperçu

In general, the steps necessary to build the APK file:

1. [Installer Git](../Installing-AndroidAPS/git-install.md)
2. [Installer Android Studio](../Installing-AndroidAPS/Building-APK.md#install-android-studio)
3. [Définir le chemin d’accès git dans Android Studio](../Installing-AndroidAPS/Building-APK.md#set-git-path-in-preferences)
4. [Télécharger le code AndroidAPS](../Installing-AndroidAPS/Building-APK.md#download-androidaps-code)
5. [Télécharger Android SDK](../Installing-AndroidAPS/Building-APK.md#download-android-sdk)
6. [Build the app](../Installing-AndroidAPS/Building-APK.md#generate-signed-apk) (generate signed apk)
7. [Transférer le fichier apk sur votre téléphone](../Installing-AndroidAPS/Building-APK.md#transfer-apk-to-smartphone)
8. [Identifier le récepteur si vous utilisez xDrip+](..//Configuration/xdrip.md#identify-receiver)

## Démarche pas à pas

Detailed description of the steps necessary to build the APK file.

## Installer git (si vous ne l'avez pas)

Follow the manual on the [git installation page](../Installing-AndroidAPS/git-install.md).

(install-android-studio)=

## Installer Android Studio

The following screenshots have been taken from Android Studio Version Arctic Fox | 2020.3.1. Screens can change in future versions of Android Studio. But you should be able to find your way through. [Help from the community](../Where-To-Go-For-Help/Connect-with-other-users.md) is provided.

One of the most important things when installing Android Studio: **Be patient!** During installation and setup Android Studio is downloading a lot of stuff which will take its time.

Download [Android Studio from here](https://developer.android.com/studio/install.html) and install it on your computer.

On first start you will find the setup wizard:

Select "Do not import settings" as you have not used it before.

![Do not import settings](../images/studioSetup/01_ImportSettings.png)

Decide whether you want to share data with Google or not.

![Share data with Google](../images/studioSetup/02_DataSharing.png)

On the following screen click "Next".

![Welcome screen](../images/studioSetup/03_Welcome.png)

Select "Standard" installation and click "Next".

![Standard installation](../images/studioSetup/04_InstallType.png)

Select the theme for the user interface you like. (In this manual we used "Light".) Then click "Next".

> ***Remarque :*** Ce n'est que le modèle de couleurs. Vous pouvez choisir n'importe quel type (par ex. "Darcula" pour le mode sombre). Cette sélection n'a aucune influence sur la construction de l'APK, mais les captures d'écran suivantes peuvent être différentes.

![UI color scheme](../images/studioSetup/05_UITheme.png)

Click "Finish" on the "Verify Settings" dialog.

![Verify settings](../images/studioSetup/06_Verify.png)

Wait while Android Studio downloads additional components and be patient. Once everything is downloaded button "Finish" turns blue. Click the button now.

![Downloading components](../images/studioSetup/07_Downloading.png)

(set-git-path-in-preferences)=

## Définir le chemin de git dans les préférences

Make sure [git is installed](../Installing-AndroidAPS/git-install.md) on your computer and you have restarted your computer after installing.

On the Android Studio welcome screen click "Customize" (1) on the left and then select the link "All settings..." (2):

![Android Studio settings from welcome screen](../images/studioSetup/10_WizardSettings.png)

### Windows

* As windows user, make sure you have restarted your computer after [installing Git](../Installing-AndroidAPS/git-install.md).

* Double-cliquez sur "Version Control" (1) pour ouvrir le sous-menu.

* Cliquez sur Git (2).
* Assurez-vous que la méthode de mise à jour "Merge" (3) est sélectionnée.
* Vérifiez si Android Studio peut localiser le chemin d'accès à git.exe automatiquement en cliquant sur le bouton "Test" (4).
    
    ![Paramètres Android Studio](../images/studioSetup/11_GitPath.png)

* Si la configuration automatique est réussie, la version de git s'affiche sous chemin d'accès.
    
    ![Git version displayed](../images/studioSetup/12_GitVersion.png)

* Éventuellement git.exe peut ne pas être trouvé automatiquement ou le test entraînera une erreur (1) :
    
    ![Git not found](../images/studioSetup/13_GitVersionError.png)
    
    Dans ce cas, cliquez sur l'icône de dossier (2).

* Utilisez la [fonction de recherche](https://www.tenforums.com/tutorials/94452-search-file-explorer-windows-10-a.html) dans l'explorateur windows pour trouver "git.exe" si vous n'êtes pas sûr de l'endroit ou il a été installé. Vous cherchez un fichier nommé "git.exe", situé dans le dossier **\bin**.

* Sélectionnez le chemin d'accès à git.exe et vérifiez que vous avez sélectionné le dossier ** \bin\ ** (3) et cliquez sur "OK" (4).
    
    ![Select git manually](../images/studioSetup/14_GitManualSelection.png)

* Vérifiez à nouveau votre chemin d'accès git sélectionné avec le bouton "Test" comme décrit ci-dessus.

* Lorsque la version de git est affichée sous le chemin (voir la capture d'écran ci-dessus), fermez la fenêtre de configuration en cliquant sur le bouton "OK" (5).

### Mac

* N’importe quelle version de git devrait fonctionner. Par exemple <https://git-scm.com/download/mac>.
* Utilisez homebrew pour installer git: ```$ brew install git```.
* Pour plus de détails sur l'installation de git, voir la [documentation officielle](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* Si vous installez git via homebrew, il n'est pas nécessaire de modifier les préférences. Juste au cas où : on peut y accéder ici : Android Studio - Preferences.

(download-androidaps-code)=

## Télécharger le code AndroidAPS

* Sur l'écran d'accueil d'Android Studio, sélectionnez "Projects" (1) à gauche, puis "Get from VCS" (2).
    
    ![Android Studio wizard](../images/studioSetup/20_ProjectVCS.png)
    
    * Si vous avez déjà ouvert Android Studio et que vous ne voyez plus l'écran d'accueil, sélectionnez File (1.) > New (2.) > Project from Version Control ... (3)
        
        ![Charger le projet à partir du contrôle de version dans Android Studio](../images/AndroidStudio_FileNew.PNG)
    
    * Nous allons maintenant indiquer à Android Studio d'où recevoir le code :
    
    * Assurez-vous d'avoir sélectionné "Repository URL" sur la gauche (1).
    
    * Vérifier si "Git" est sélectionné comme contrôle de version (2).
    * Copiez et collez l'URL ```https://github.com/nightscout/AndroidAPS``` dans le dépôt principal d'AndroidAPS dans la zone de texte d'URL (3).
    * Choisissez le répertoire dans lequel vous voulez enregistrer le code cloné (4).
        
        ![Clone Git](../images/studioSetup/21_CloneURL.png)

* Cliquez sur le bouton "Clone" (5).
    
    ![Cloner le répertoire](../images/studioSetup/22_Cloning.png)

* Ne cliquez pas sur "Background" pendant que le répertoire est cloné !

* Une fois que le dépôt a été cloné avec succès, Android Studio ouvrira le projet cloné.

* On vous demandera si vous voulez faire confiance au projet. Cliquez sur "Trust project" !
    
    ![Trust project](../images/studioSetup/23_TrustProject.png)

* Dans le coin inférieur droit, vous verrez l'information qu'Android Studio exécute les tâches d'arrière-plan.
    
    ![Tâches d'arrière-plan](../images/studioSetup/24_GradleSyncRunning.png)

* Accorder l'accès si votre pare-feu demande l'autorisation.
    
    ![Autorisation java dans le pare-feu](../images/AndroidStudio361_18.png)

* Une fois que les tâches de fond sont terminées, vous verrez probablement une erreur indiquant que des erreurs se sont produites (1) ou (2) ou (3).
    
    ![Licence SDK](../images/studioSetup/25_SyncFailed.png)
    
    Ne vous inquiétez pas, cela sera bientôt résolu!

(download-android-sdk)=

## Télécharger Android SDK

* Dans le menu, allez dans "File" (1) > "Settings" (2).
    
    ![Ouvrir les paramètres](../images/studioSetup/30_Settings.png)

* Double-cliquez sur "Appearance & Behaviour" pour ouvrir son sous-menu (1).

* Double-cliquez sur "System Settings" (2) et sélectionnez "Android SDK" (3).
* Cochez la case à gauche de "Android 9.0 (Pie)" (4.) (API niveau 28).
    
    ![Paramètres SDK](../images/studioSetup/31_AndroidSDK.png)

* Confirmez les modifications en cliquant sur OK.
    
    ![Confirmer les modifications SDK](../images/studioSetup/32_ConfirmSDK.png)

* Acceptez le contrat de licence (1) et cliquez sur « Next» (2).
    
    ![Accepter la licence SDK](../images/studioSetup/33_ConfirmLicense.png)

* Attendez que le téléchargement et l'installation du SDK soient terminés.
    
    ![Attendre lors de l'installation du SDK](../images/studioSetup/34_DownloadSDK.png)

* Lorsque l'installation du SDK est terminée, le bouton "Finish" devient bleu. Cliquez sur ce bouton.
    
    ![Terminer l'installation du SDK](../images/studioSetup/35_DownloadSDKfinished.png)

* Android Studio recommande de mettre à jour le "gradle system". **Ne jamais mettre à jour gradle !** Cela pourrait entraîner des difficultés !

* Si vous voyez une information sur le côté inférieur droit de votre fenêtre Android Studio qui indique que le plugin Android Gradle est prêt à mettre à jour, cliquez sur le texte "update" (1).
    
    ![No gradle update](../images/studioSetup/36_GradleUpdateRequest.png)

* Dans la boîte de dialogue sélectionnez "Don't remind me again for this project" (2).
    
    ![No gradle update](../images/studioSetup/37_GradleUpdateDeny.png)

* Redémarrez Android Studio avant de continuer.

(generate-signed-apk)=

## Générer un APK signé

Signing means that you indicate your app to be your own creation but in a digital way as a kind of digital fingerprint within the app itself. That is necessary because Android has a rule that it only accepts signed code to run for security reasons. For more information on this topic, follow [this link](https://developer.android.com/studio/publish/app-signing.html#generate-key).

* Après le démarrage d'Android Studio, attendez que toutes les tâches en arrière-plan soient terminées.
    
    ![Wait for background tasks](../images/studioSetup/40_BackgroundTasks.png)
    
    * ***Warning:*** If errors occur, do not continue with the following steps. \ Consult the [troubleshooting section](../Installing-AndroidAPS/troubleshooting_androidstudio) for known problems!
    
    ![Gradle Sync Error](../images/studioSetup/41_GradleSyncError.png)

* Click "Build" (1) in the menu bar and select "Generate Signed Bundle / APK..." (2).
    
    ![Génération de l'apk](../images/studioSetup/42_MenuBuild.png)

* Select "APK" (1) instead of "Android App Bundle" and click "Next" (2).
    
    ![APK au lieu du bundle](../images/studioSetup/43_Apk.png)

* Make sure that module is set to "AndroidAPS.app" (1).

* Click "Create new..." (2) to start creating your key store.
    
    ***Note:*** A key store in this case is nothing more than a file in which the information for signing is stored. Il est crypté et les informations sont sécurisées avec des mots de passe.
    
    ![Créer le fichier de clés](../images/studioSetup/44_KeystoreNew.png)

* Click the folder symbol to select a path on your computer for your key store.
    
    ![Créer le fichier de clés](../images/studioSetup/45_KeystoreDialog.png)

* Sélectionnez le répertoire dans lequel votre fichier de clés doit être sauvé (1).
    
    ![Créer le fichier de clés](../images/studioSetup/46_KeystorePath.png)
    
    ***Warning: Do not save in same folder as project. You must use a different directory!*** A good location would be your home folder.

* Type a file name for your key store (2) and confirm with "OK" (3).

* Enter (2) and confirm (3) the password for your key store. ![Select key store path](../images/studioSetup/47_KeystoreDialog.png)
    
    ***Note:*** Passwords for key store and key do not have to be very sophisticated. Assurez vous de bien vous en souvenir ou notez le dans un endroit sûr. In case you will not remember your passwords in the future, see [troubleshooting for lost key store](../Installing-AndroidAPS/troubleshooting_androidstudio.md#lost-keystore).

* Enter an alias (4) for your key. Choose whatever you like.

* Enter (5) and confirm (6) the password for your key

* Validity (7) is 25 years by default. Vous n'avez pas à modifier la valeur par défaut.

* Le prénom et le nom sont obligatoires (8). Toutes les autres informations sont facultatives.

* Click "OK" (9) when you are done.

* Assurez-vous que la case permettant de mémoriser les mots de passe est cochée (1). Ainsi vous n'aurez pas à les saisir à nouveau la prochaine fois que vous génèrerez le fichier apk (par ex. en faisant une mise à jour avec une nouvelle version d'AndroidAPS).

* Cliquez sur "Next" (2).
    
    ![Mémoriser les mots de passe](../images/studioSetup/48_KeystoreSave.png)

* Select build variant "fullRelease" (1) and press "Finish".
    
    ![Select build variant](../images/studioSetup/49_BuildVariant.png)

* Android Studio will show "Gradle Build running" at the bottom. This takes some time, depending on your computer and internet connection. **Be patient!**
    
    ![Gradle Running](../images/studioSetup/50_GradleRunning.png)

* Android Studio will display the information "Generate Signed APK" after build is finished.
    
    ![Build finished](../images/studioSetup/51_BuildFinished.png)

* Dans le cas ou la génération n'a pas réussie, référez vous à la [section dépannage](../Installing-AndroidAPS/troubleshooting_androidstudio).

* Click on the notification to expand it.

* Click on the link "locate".
    
    ![Locate build](../images/studioSetup/52_BuildLocate.png)
    
    * If the notification is gone, you can always open the "Event log" and select the same link there. ![Génération réussie - journal des événements](../images/studioSetup/53_EventLog.png)

* Your file manager/explorer will open. Navigate to the directory "full" (1) > "release" (2).
    
    ![Emplacement du fichier apk](../images/studioSetup/54_APKlocation.png)

* "app-full-release.apk" (3) is the file you are looking for!

(transfer-apk-to-smartphone)=

## Transférer le fichier APK sur le smartphone

Easiest way to transfer app-full-release.apk to your phone is via [USB cable or Google Drive](https://support.google.com/android/answer/9064445?hl=en). Please note that transfer by mail might cause difficulties and is not the preferred way.

On your phone you have to allow installation from unknown sources. Manuals how to do this can be found on the internet (i.e. [here](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) or [here](https://www.androidcentral.com/unknown-sources)).

## Résolution de problèmes

See separate page [troubleshooting Android Studio](../Installing-AndroidAPS/troubleshooting_androidstudio).