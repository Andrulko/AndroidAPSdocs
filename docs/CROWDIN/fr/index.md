# Bienvenue dans la documentation de AAPS

![image](./images/basic-outline-of-AAPS.png)

AAPS est une application open source pour les personnes vivant avec un diabète insulino-dépendant et qui agit comme un pancréas artificiel (APS) sur les smartphones Google Android. It uses an openAPS software algorithm which aims to do what a living pancreas does: keeping blood sugar levels within healthy limits by using automated insulin dosing (AID). Additionally, you need a supported and FDA/CE approved insulin pump, and a continuous glucose meter.

Interested? Read more about AAPS in the [introduction](introduction.md).

```{warning}
**AVIS DE SÉCURITÉ IMPORTANT**

La base des fonctions de sécurité d'AAPS présentée dans cette documentation s'appuie sur les fonctions de sécurité du matériel utilisé pour construire votre système. Il est extrêmement important que vous utilisiez uniquement une pompe à insuline et un capteur de MGC approuvés FDA/CE pour mettre en oeuvre une boucle fermée d'administration automatique d'insuline. Les modifications matérielles ou logicielles de ces composants peuvent entraîner un dosage incorrect de l'insuline, causant un risque significatif pour l'utilisateur. Si vous trouvez ou recevez des pompes à insuline ou des récepteurs MGC cassés, modifiés ou fabriqués par vos soins, *ne les utilisez pas* pour créer un système AAPS.

De plus, il est également important d'utiliser uniquement des fournitures d'origine telles que serteurs, canules et réservoirs d'insuline approuvés par le fabricant pour une utilisation avec votre pompe ou votre MGC. L'utilisation de consommables non testés ou modifiés peut entraîner une imprécision du MGC et des erreurs de dosage de l'insuline. L'insuline est très dangereuse lorsqu'elle est mal dosée - veuillez ne pas jouer avec votre vie en piratant avec vos fournitures.

Enfin et surtout, vous ne devez pas prendre d'inhibiteurs du SGLT-2 (gliflozines), car ils abaissent de façon incalculable la glycémie.  La combinaison avec un système qui réduit les débits de base pour augmenter la glycémie est particulièrement dangereuse car en raison de la gliflozine, cette augmentation de glycémie pourrait ne pas se produire et un état dangereux d'absence d'insuline peut se produire.
```

```{note}
**Disclaimer and Warning**

- All information, thought, and code described here is intended for informational and educational purposes only. Nightscout ne fait actuellement aucune tentative de conformité à la confidentialité HIPAA. Utilisez Nightscout et AAPS à vos propres risques et n'utilisez pas les informations ni le code pour prendre des décisions médicales.
- L'utilisation du code de github.com est sans garantie ni support formel d'aucune sorte. Veuillez consulter la LICENCE de ce référentiel pour plus de détails.
- Tous les noms de produits et de sociétés, marques commerciales, marques de service, marques déposées,  sont la propriété de leurs détenteurs respectifs. Leur utilisation est à titre informatif et n'implique aucune affiliation avec eux ni aucune approbation de leur part.

Please note - this project has no association with and is not endorsed by: [SOOIL](http://www.sooil.com/eng/), [Dexcom](https://www.dexcom.com/), [Accu-Chek, Roche Diabetes Care](https://www.accu-chek.com/), [Insulet](https://www.insulet.com/) or [Medtronic](https://www.medtronic.com/).
```

## Comment lire la documentation ?

Nous avons rédigé ce paragraphe de la documentation en particulier pour ceux qui sont nouveaux dans le concept du Do-It-Yourself-APS (Système de Pancreas Artificiel fait soi même) afin de mieux vous montrer comment faire connaissance avec les informations que nous considérons comme les plus importantes, surtout en ce qui concerne la compréhension des raisons qui justifient les "limites" mises en place lorsque vous commencez votre premier voyage AAPS. Ces limites de sécurité ont été développées au cours de plusieurs années par les observations des erreurs involontaires que les nouveaux utilisateurs sont les plus susceptibles de commettre lors de la première mise en place, construit, et enfin lorsqu'ils ont réussi avec succès à boucler avec AAPS - comme le plus souvent ces erreurs se produisent simplement parce que l'utilisateur était tellement excité de commencer à utiliser le système qu'ils ont peut-être oublié de s'asseoir et de consacrer le temps nécessaire pour comprendre de façon approfondie l'ensemble des informations présentes dans cette documentation. Nous sommes tous passés par là!

Certes, l'approche "tout lire" a du mérite et est certainement bonne. Cependant, Il n’est pas rare que les nouveaux arrivants soient rapidement submergés par le volume et la variété des informations qu’ils sont censés comprendre en même temps! Ainsi, ces prochains paragraphes sont destinés à mettre en place les fondations les plus importantes de la connaissance nécessaire pour gérer avec succès votre configuration personnelle le plus facilement possible. Les nouveaux utilisateurs peuvent se référer à ce guide lorsqu'ils rencontrent des aspects du système avec lesquels ils ne sont pas encore familiers; et pour se rappeler où aller dans la documentation afin de trouver des informations plus détaillées si nécessaire. Il est également important de mettre en perspective les capacités d'AAPS au démarrage, car il peut parfois être décevant de découvrir en cours de lecture que certains outils nécessaires ne sont pas disponibles pour le moment (à cause des contraintes sur les pompes à insuline, capteurs MGC disponibles dans certains pays et par rapport à  d'autres pays, etc.) ou tout simplement parce que les fonctionnalités moins importantes ou différentes de celles imaginées au départ. Enfin, il est important d'admettre que de nombreux points liés aux retours d'expérience dans cette documentation ne deviennent pertinents que lorsque vous commencerez à utiliser AAPS en temps réel. Tout comme il est quasiment impossible d'apprendre à pratiquer un sport uniquement en lisant les règles, il faut combiner un apprentissage préalable des fondations et des règles pour utiliser AAPS en toute sécurité et ensuite consacrer du temps pour apprendre comment appliquer au mieux ces règles pendant que vous naviguez à travers les étapes de la boucle avec AAPS.

La section [Pour commencer](Getting-Started/Safety-first.md) doit obligatoirement être lue pour comprendre ce qu'un système de pancréas artificiel est conçu pour faire; et est particulièrement pertinente pour les utilisateurs d'AAPS.

La section [De quoi ai-je besoin?](Module/module.md) spécifie les MGC (Mesure de Glycémie en Continu) et les pompes à insuline qui sont compatibles avec AAPS. Cette section est importante à comprendre pour que votre système AAPS puisse être assemblé et construit correctement la première fois et qu'elle fonctionne bien dans les situations du monde réel.

La section [Où chercher de l'aide ?](Where-To-Go-For-Help/Connect-with-other-users.html) devrait vous aider à vous orienter vers les meilleurs endroits pour aller chercher de l'aide en fonction de votre expérience avec AAPS. C'est très important pour que vous ne vous sentiez jamais seuls, surtout au début, et pour que vous puissiez entrer en contact avec d'autres utilisateurs aussi rapidement que possible, clarifier les questions et résoudre les écueils habituels le plus vite possible. L'expérience montre que beaucoup de gens utilisent déjà AAPS avec succès, mais tout le monde a une question à un moment qu'il ne sait pas résoudre seul. Ce qui est bien, c'est qu'en raison du grand nombre d'utilisateurs, les temps de réponse aux questions sont généralement très rapides, de l'ordre de quelques heures. N'ayez pas peur de demander de l’aide, car il n’y a pas de question stupide! Nous encourageons les utilisateurs, quelque soit leur niveau, à poser autant de questions qu’ils jugent nécessaire pour les aider à fonctionner en toute sécurité. Il suffit juste d'essayez.

Dans la section [Glossaire](Getting-Started/Glossary.md) nous avons compilé une liste des acronymes (ou abbréviations) utilisés dans AAPS. Par exemple, pour savoir ce que signifie les termes SI ou CT, parmi les termes les plus courrants.

Pour les parents qui veulent construire AAPS pour leurs enfants, nous recommandons la section [AAPS pour les enfants](Children/Children.md) , car vous y trouverez des informations plus avancées pour apprendre les étapes supplémentaires nécessaires au contrôle à distance de l'application AAPS de votre enfant ainsi qu'un profil de sécurité plus complet comparé aux adultes. Vous devez être en mesure de soutenir vos enfants et de comprendre tous les concepts avancés qu'AAPS propose pour vous aider à réussir.

Maintenant que vous avez une bonne compréhension des concepts qu'AAPS utilise, savoir où aller pour trouver les outils nécessaires pour construire votre APS et savoir où obtenir de l'aide en cas d'urgence, c'est le bon moment pour commencer à construire l'application ! La section [Comment installer AAPS ?](Installing-AAPS/Building-APK.md) vous montre cela en détail. Étant donné que les exigences sont très différentes de celles que vous avez pu mettre en place dans le passé, nous vous recommandons de suivre vraiment toutes les instructions, pas à pas, les premières fois que vous construisez l'application, afin que vous ayez une meilleure idée de la façon dont le processus de construction de l'application est censé se comporter lorsque toutes les étapes sont suivies exactement. N'oubliez pas de prendre votre temps. Plus tard, cela ira très rapidement lorsque vous devrez reconstruire l'application pour une nouvelle version. De cette façon, vous aurez plus de chances de voir quand quelque chose ne va pas comme prévu avant que trop d'étapes ne soient effectuées. Il est important de sauvegarder votre fichier de clés (fichier .jks utilisé pour signer votre application) dans un endroit sûr, afin que vous puissiez toujours utiliser le même fichier de clés et le même mot de passe chaque fois qu'on vous demande de créer une nouvelle mise à jour d'AAPS, car c"est ve fichier qui garanti que chaque nouvelle version de l'application « se souviendra » de toutes les informations que vous lui avez fournies dans les versions précédentes de l'application et ainsi de permettre que les mises à jour se dérouleront aussi facilement que possible. En moyenne, vous pouvez considérer qu'il y aura une nouvelle version et 2 à 3 mises à jour par an. Ce nombre est basé sur le retour d'expérience et peut changer à l'avenir. Mais nous voulons au moins vous donner une estimation sur ce à quoi vous pouvez vous attendre. Lorsque vous aurez plus d'expérience pour créer les "build" de mises à jour d'AAPS, toutes les étapes nécessaires pour une mise à jour ne prendront que 15 à 30 minutes. en moyenne. Cependant, au début, il peut y avoir une période d'apprentissage assez difficile, car ces étapes ne sont pas toujours considérées comme intuitives par les nouveaux utilisateurs! Donc, ne soyez pas frustré si vous trouvez qu'il vous faut une demi-journée ou une journée entière avec l'aide de la communauté avant d'arriver à faire vos premières mise à jour. Si vous trouvez que vous devenez très frustré, prenez juste des courtes pauses et régulièrement; après un tour du pâté de maisons ou deux, vous trouverez que vous serez plus à même d'aborder le problème à nouveau. Nous avons également compilé une liste de questions et de réponses à la plupart des erreurs typiques qui sont susceptibles de se produire lors des premières mises à jour dans la section Questions Fréquentes; ainsi que dans « Comment installer AAPS ? » qui fournit des renseignements supplémentaires dans la section « Dépannage ».

La section [Configuration des composants](Configuration/BG-Source.md) explique comment intégrer correctement chacun des composants dans AAPS, ainsi que la façon de les configurer pour les faire fonctionner aussi facilement que possible ensemble. Tous les composants sont listés dans les sections séparées : MGC/MGF, Paramètres xDrip, Pompes, Téléphones, Configuration Nightscout et Smartwatches. Les valeurs du capteur (Gly) et le contrôle de la pompe à insuline sont des informations particulièrement importantes à comprendre. La sous-section [Configuration](Configuration/BG-Source.md) décrit les meilleures configurations de pompe à utiliser dans AAPS.

Ceci est suivi d'une sous-section particulièrement importante [Utilisation AAPS](Getting-Started/Screenshots.md), dans laquelle vous êtes pas à pas initié à l'utilisation complète de tout ce que AAPS peut vous offrir via un processus progressif, sécurisé et soigneusement calibré, conçu pour vous assurer que vous/votre enfant sont parfaitement familiers et à l'aise pour naviguer dans les différents niveaux et configurations de menu avant de passer à la phase suivante, chacun étant communément appelé Objectif suivant, jusqu'à ce que vous ayez assez d'expérience pour commencer à utiliser les options les plus avancées disponibles dans l'application. Ces objectifs sont spécialement conçus de manière à débloquer progressivement plus de possibilités d'AAPS et à passer de la boucle ouverte à la boucle fermée.

Après cela, il y a une sous-section [Conseils Généraux](Usage/Timezone-traveling.md) avec par ex. des renseignements sur la façon de gérer les passages des fuseaux horaires ou encore savoir ce qu'il faut faire lors des changements d'heure du printemps - retour arrière de l'automne, changements qui se produiront deux fois par an en utilisant AAPS.

Cette page est destinée [aux professionels de santé](Resources/clinician-guide-to-AAPS.md) qui ont exprimé leur intérêt pour la technologie du pancréas artificiel en open source comme AAPS, ou pour les patients qui veulent partager ces informations avec leur équipe médicale.

Enfin, dans la sous-section [Comment aider ?](make-a-PR.md) nous aimerions vous fournir des informations afin que vous puissiez suggérer de petites ou grandes modifications à la documentation et travailler avec nous sur la documentation. Nous avons également besoin d'aide pour [la traduction de la documentation](translations.md). Par ailleurs, c'est également très utile pour tout le monde si vous pouviez fournir les liens vers la documentation correspondante (ou des captures d'écran des liens dans la documentation si vous n'êtes pas familier avec la façon d'envoyer un lien) lorsque vous répondez aux questions d'autres utilisateurs. De cette façon, les informations correctes peuvent facilement être retrouvées si d'autres utilisateurs cherchent les réponses aux mêmes types de questions à l'avenir.

```{toctree}
:caption: Changer de langue

Changer de langue <./changelanguage.md>

```

```{toctree}
:caption: Home

Introduction <./introduction.md>

```

```{toctree}
:caption: Getting started

Preparing <preparing.md>

Docs updates & changes <./Getting-Started/WikiUpdate.md>

```

```{toctree}
:caption: Setting up AAPS

Setting up the reporting server <./Installing-AndroidAPS/setting-up-the-reporting-server.md>
Building AAPS <./Installing-AndroidAPS/building-AAPS.md>
Transferring and Installing AAPS <./Installing-AndroidAPS/Transferring-and-installing-AAPS.md>
Setup Wizard<./Installing-AndroidAPS/setup-wizard.md>
Change AAPS configuration<./Installing-AndroidAPS/change-configuration.md>
Completing the objectives <./Usage/completing-the-objectives.md>
```

```{toctree}
:caption: Remote control and following

Remote control <remote-control.md>
Following-only <following-only.md>

```

```{toctree}
:caption: Advanced Setting up APPS

Release notes <./Installing-AndroidAPS/Releasenotes.md>

Update to a new version or branch <./Installing-AndroidAPS/Update-to-new-version.md>

Dev branch <./Installing-AndroidAPS/Dev_branch.md>

Dedicated Google account for AAPS (optional)<./Installing-AndroidAPS/Dedicated-Google-account-for-AAPS.md>

```

```{toctree}
:caption: Boucle Fermée complète

Boucle Fermée complète <./Usage/FullClosedLoop.md>

```

(index-component-setup)=

```{toctree}
:caption: Component Setup

CGM/FGM <./Configuration/BG-Source.md>

xDrip Settings <./Configuration/xdrip.md>

Pump choices <./Getting-Started/Pump-Choices.md>

Phones <./Hardware/Phoneconfig.md>

Smartwatch  <./Hardware/Smartwatch.md>

```

```{toctree}
:caption: AAPS Usage

AAPS screens <./Getting-Started/Screenshots.md>

OpenAPS features <./Usage/Open-APS-features.md>

Dynamic ISF <./Usage/DynamicISF.md>

COB calculation <./Usage/COB-calculation.md>

Sensitivity detection <./Configuration/Sensitivity-detection-and-COB.md>

Profile switch <./Usage/Profiles.md>

Temp-targets <./Usage/temptarget.md>

Extended carbs <./Usage/Extended-Carbs.md>

Automation <./Usage/Automation.md>

Autotune (dev only) <./Usage/autotune.md>

Careportal (discontinued) <./Usage/CPbefore26.md>

Open Humans Uploader <./Configuration/OpenHumans.md>

Automation with 3rd party apps <./Usage/automationwithapp.md>

Android auto <./Usage/Android-auto.md>

Custom Watchface reference document <./Usage/Custom_Watchface_Reference.md>

Exchange Site Custom Watchfaces <./ExchangeSiteCustomWatchfaces/index.md>

```

```{toctree}
:caption: "Conseils généraux"

Fuseaux horaires <./Usage/Timezone-traveling.md>

Acces aux fichiers journaux <./Usage/Accessing-logfiles.md>

Conseils d'utilisation de l'Accu-Chek Combo <./Usage/Accu-Chek-Combo-Tips-for-Basic-usage.md>

Export/Import des paramètres <./Usage/ExportImportSettings.md>

Mode ingénierie xDrip <./Usage/Enabling-Engineering-Mode-in-xDrip.md>

```

```{toctree}
:caption: Dépannage

Dépannage <./Usage/troubleshooting.md>

Client Nightscout <./Usage/Troubleshooting-NSClient.md>

```

```{toctree}
:caption: FAQ

FAQ <./Getting-Started/FAQ.md>
```

```{toctree}
:caption: Glossaire

Glossaire <./Getting-Started/Glossary.md>
```

```{toctree}
:caption: Où chercher de l'aide

Ressources utiles à lire avant de commencer <./Where-To-Go-For-Help/Background-reading.md>

Où chercher de l'aide <./Where-To-Go-For-Help/Connect-with-other-users.md>

Wiki mises à jour et modifications <./Getting-Started/WikiUpdate.md>

```

```{toctree}
:caption: Pour les professionnels de santé

Pour les professionnels de santé <./Ressources/clinician-guide-to-AndroidAPS.md>
```

```{toctree}
:caption: How to help

How to help <./Getting-Started/How-can-I-help.md>

How to translate the app and docs <./translations.md>

How to edit the docs <./make-a-PR.md>

State of translations <./Administration/stateTranslations.md>

```

```{toctree}
:caption: Legacy

Hints and Checks after update to AAPS 3.0<./Installing-AndroidAPS/update3_0.md>

Checks after update to AAPS 2.7 <./Installing-AndroidAPS/update2_7.md>

```

```{toctree}
:caption: Sandbox

Sandbox <./Sandbox/sandbox1.md>
Crowdin Test <./Sandbox/crowdintest.md>
Image Scaling <./Sandbox/imagescaling.md>

```

```{note}
**Avertissement**

- Toutes les informations, pensées et codes décrits ici sont destinés à des fins d'information et d'éducation uniquement. Nightscout ne fait actuellement aucune tentative de conformité à la confidentialité HIPAA. Utilisez Nightscout et AAPS à vos propres risques et n'utilisez pas les informations ni le code pour prendre des décisions médicales.
- L'utilisation du code de github.com est sans garantie ni support formel d'aucune sorte. Veuillez consulter la LICENCE de ce référentiel pour plus de détails.
- Tous les noms de produits et de sociétés, marques commerciales, marques de service, marques déposées,  sont la propriété de leurs détenteurs respectifs. Leur utilisation est à titre informatif et n'implique aucune affiliation avec eux ni aucune approbation de leur part.

A noter - ce projet n'a aucun lien avec, et n'est pas approuvé par : [SOOIL](<https://www.sooil.com/eng/>), [Dexcom](<https://www.dexcom.com/>), [Accu-Chek, Roche Diabetes Care](<https://www.accu-chek.com/>) ou [Medtronic](<https://www.medtronic.com/>)

```
