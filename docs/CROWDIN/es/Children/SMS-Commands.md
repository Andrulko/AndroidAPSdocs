# Comandos SMS

## La seguridad primero

- AndroidAPS te permite controlar el teléfono de un niño de forma remota mediante mensajes de texto. Si activas esta función "SMS Communicator", recuerda siempre que el teléfono configurado para dar comandos remotos podría ser robado. Por lo que protege siempre el móvil con código PIN. Se recomienda usar una contraseña compleja o usar datos biométricos.
- Además, se recomienda permitir a un [segundo número de teléfono](SMS-Commands-authorized-phone-numbers) para comandos SMS. Por lo que puedes utilizar el segundo número para [desactivar temporalmente](SMS-Commands-other) los comandos SMS en caso de que que pierdas o te roben el teléfono principal.
- AndroidAPS también te avisará por mensaje de texto si tus comandos remotos, tales como bolos o cambios de perfil, se han llevado a cabo. Es aconsejable, por seguridad, configurar esta función para que los textos de confirmación se envíen al menos a dos números de teléfono diferentes, así si falla (o ha sido robado) uno, quedará el otro.
- **If you bolus through SMS Commands you must enter carbs through Nightscout (AAPSClient, Website...)!** If you fail to do so IOB would be correct with too low COB potentially leading to not performed correction bolus as AAPS assumes that you have too much active insulin.
- Desde la versión 2.7 de AndroidAPS se debe utilizar una aplicación de autenticación por contraseña de un sólo uso, para mejorar la seguridad al usar la opción de comandos SMS.

## Configurar comandos SMS

```{image} ../images/SMSCommandsSetup.png
:alt: Configuración de comandos SMS
```

- Most of the adjustments of temp targets, following AAPS etc. can be done on [AAPSClient app](../Children/Children.md) on an Android phone with an internet connection.
- Los bolos no pueden poner mediante Nightscout, pero se pueden usar los comandos SMS.
- If you use an iPhone as a follower and therefore cannot use AAPSClient app, there are additional SMS commands available.
- En los ajustes de tu teléfono Android, ve a aplicaciones > AAPS > Permisos y activa el de SMS

(SMS-Commands-authorized-phone-numbers)=

### Números de teléfono permitidos

- En AndroidAPS ir a Tabla de configuraciones > Comunicador SMS \*\* y añadir el número(s) de teléfono que deseas habilitar para enviar comandos SMS (separados por punto y coma - p.ej. +3412345678;+3412345679)

- Ten en cuenta que el signo "+" delante del número puede o no ser necesario según tu ubicación. Para determinarlo, envía un texto de muestra que muestre el formato recibido en la pestaña de Comunicador de SMS.

- Habilitar 'Permitir comandos remotos vía SMS'.

- Si quieres utilizar más de un número:

  - Añade sólo un número.

  - Asegúrate de que ese número funciona enviando y confirmando comandos SMS.

  - Añade número/os adicionales separados por punto y coma, sin espacios.

    ```{image} ../images/SMSCommandsSetupSpace2.png
    :alt: Configurar Comandos SMS usando múltiples números
    ```

### Minutos entre los comandos de bolos

- Puedes definir un retraso mínimo entre dos bolos enviados mediante SMS.
- Por razones de seguridad, hay que añadir al menos dos números de teléfono autorizados para editar este valor.

### Es obligatorio añadir el PIN al final del token

- Por razones de seguridad, el código de respuesta tiene que ir seguido de un PIN.

- Reglas del PIN:

  - De 3 a 6 dígitos
  - No puede ser los mismos dígitos (p.ej. 1111)
  - No pueden ser números consecutivos (p.ej. 1234)

### Configuración de la aplicación de autenticación

- Se utiliza una doble autenticación, para mejorar la seguridad.

- Puedes utilizar cualquier aplicación de autenticación que soporte tokens RFC 6238 TOTP. Las aplicaciones más comunes gratuitas son las siguientes:

  - [Authy](https://authy.com/download/)
  - Google Authenticator - [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) / [iOS](https://apps.apple.com/de/app/google-authenticator/id388497605)
  - [LastPass Authenticator](https://lastpass.com/auth/)
  - [FreeOTP Authenticator](https://freeotp.github.io/)

- Instala en tu teléfono la aplicación de autenticación preferida y escanea el código QR mostrado en AAPS.

- Prueba la contraseña de un solo uso introduciendo el token mostrado en tu aplicación de autenticación y el PIN que has configurado en AAPS. Example:

  - El PIN obligatorio es 2020
  - El token generado por la aplicación de autenticación TOTP es 457051
  - Añade 4570512020

- El texto rojo "PIN INCORRECTO" cambiará **automáticamente** a verde "OK" si lo has añadido correctamente. **¡No hay que pulsar ningún botón!**

- La hora en ambos teléfonos tiene que estar sincronizada. La mejor práctica es configurarla de forma automática desde la red. Las diferencias de tiempo pueden causar problemas de autenticación.

- Usa el botón "REINICIAR AUTENTICADORES" si quieres eliminar los autenticadores aprovisionados.  (Al restablecer el autenticador se invalidan TODOS los autenticadores ya aprovisionados. Tendrás que volver a configurarlos)

## Uso de comandos SMS

- Envía un SMS al teléfono que ejecuta AAPS desde alguno de tus teléfonos autorizados, utilizando cualquiera de los [comandos](SMS-Commands-commands) siguientes.

- El teléfono que ejecuta AAPS responderá para confirmar el éxito del comando o del estado solicitado.

- Confirma el comando enviando el código donde sea necesario. Example:

  - El PIN obligatorio es 2020
  - El token generado por la aplicación de autenticación TOTP es 457051
  - Añade 4570512020

**Sugerencia**: Puede ser útil tener SMS ilimitados en tu plan de teléfono (para cada teléfono utilizado), si se van a enviar muchos SMS.

(SMS-Commands-commands)=
## Comandos

Los comandos deben enviarse en inglés, la respuesta será en tu idioma local si la cadena de respuesta ya está [traducida](translations-translate-strings-for-AAPS-app).

```{image} ../images/SMSCommands.png
:alt: Ejemplo de Comandos SMS
```

### Loop

- LOOP STOP/DISABLE \* Respuesta: El lazo ha sido desactivado

- LOOP START/ENABLE \* Respuesta: El lazo ha sido activado

- LOOP STATUS

  - La respuesta depende del estado actual

    - El lazo está desactivado
    - El lazo está activado
    - Suspendido (10 min)

- LOOP SUSPEND 20 \* Respuesta: El lazo se ha suspendido durante 20 minutos

- LOOP RESUME \* Respuesta: El lazo se ha reanudado

### Datos del MCG

- BG \* Respuesta: Última BG: 5.6 hace 4min, Delta: -0,2 mmol, IOB: 0.20U (Bolo: 0.10U Basal: 0.10U)
- CAL 5.6 \* Respuesta: Para enviar la calibración 5.6, responde con el código de la aplicación Authenticator para el Usuario seguido del PIN. \* Respuesta después de recibir el código correcto: Calibración enviada (** Si xDrip está instalado. Debe habilitarse la aceptación de calibraciones en xDrip+**)

### Basal

- BASAL STOP/CANCEL \* Respuesta: Para detener la basal temporal, responde con el código de la aplicación de autenticación del usuario seguido del PIN
- BASAL 0.3 \* Respuesta: Para iniciar basal de 0,3U/h durante 30 minutos, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- BASAL 0.3 20 \* Respuesta: Para iniciar basal de 0,3U/h durante 20 minutos, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- BASAL 30% \* Respuesta: Para iniciar basal al 30% durante 30 minutos, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- BASAL 30% 50 \* Respuesta: Para iniciar basal al 30% durante 50 minutos, responda con el código de la aplicación de autenticación del usuario seguido del PIN

### Bolo

No se permite el bolo remoto en los próximos 15 minutos (este valor sólo es editable si se han agregado 2 números de teléfono) después del último comando de bolo o comandos remotos. Por lo tanto, la respuesta depende del momento en que se administró el último bolo.

- BOLUS 1.2 \* Respuesta A: Para administrar un bolo de 1.2U, responda con el código de la aplicación de autenticación del usuario seguido del PIN. \* Respuesta B: Bolo remoto no disponible. Inténtelo de nuevo más tarde.
- BOLUS 0,60 MEAL \* Si especifica el parámetro opcional MEAL, esto establece el Objetivo Temporal para COMIDA (los valores predeterminados son: 90 mg/dL, 5.0 mmol/l durante 45 minutos). \* Respuesta A: Para administrar un bolo para la comida de 0,60U, responda con el código de la aplicación de autenticación del usuario seguido del PIN \* Respuesta B: Bolos remotos no disponibles.
- CARBS 5 \* Respuesta: Para ingresar 5 gramos a las 12:45, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- CARBS 5 17:35/5:35PM \* Respuesta: Para ingresar 5 gramos a las 17:35, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- EXTENDED STOP/CANCEL \* Respuesta: Para detener el bolo extendido, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- EXTENDED 2 120 \* Respuesta: Para iniciar un bolo extendido de 2U durante 120 minutos, responda con el código de la aplicación de autenticación del usuario seguido del PIN

### Perfil

- PROFILE STATUS \* Respuesta: Perfil1
- PROFILE LIST \* Respuesta: 1.\`Perfil1\` 2.\`Perfil2\`
- PERFIL 1 \* Respuesta: Para cambiar al perfil Perfil1 al 100%, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- PROFILE 2 30 \* Respuesta: Para cambiar al perfil Perfil2 al 30%, responda con el código de la aplicación de autenticación del usuario seguido del PIN

(SMS-Commands-other)=

### Otros

- TREATMENTS REFRESH \* Respuesta: Actualizar tratamientos desde NS
- AAPSClient RESTART \* Response: AAPSClient RESTART 1 receivers
- PUMP \* Respuesta: Última conexión: hace 1 minuto. Temp: 0,00U/h @11:38. 5/30 min. IOB: 0,5 U. Reservorio: 34 U. Batería: 100%
- PUMP CONNECT \* Respuesta: Bomba reconectada
- PUMP DISCONNECT *30* \* Respuesta: Para desconectar la bomba durante *30* minutos, responda con el código de la aplicación de autenticación del usuario seguido del PIN
- SMS DISABLE/STOP \* Respuesta: Para desactivar el Servicio Remoto de SMS, responda con el código "Any". Recuerda que solo podrás activarlo de nuevo desde el teléfono principal de AAPS.
- TARGET MEAL/ACTIVITY/HYPO \* Respuesta: Para configurar el Objetivo Temporal COMIDA/ACTIVIDAD/HIPO, responde con el código de la aplicación de autenticación del usuario seguido del PIN
- TARGET STOP/CANCEL \* Respuesta: Para cancelar el Objetivo Temporal, responde con el código de la aplicación de autenticación del usuario seguido del PIN
- HELP \* Respuesta: Glucemia, Lazo, Tratamientos, ...
- HELP BOLUS \* Respuesta: BOLO 1.2, BOLO 1.2 COMIDA

(SMS-Commands-troubleshooting)=
## Solución de problemas

### Múltiples SMS

Si recibes el mismo mensaje una y otra vez (por ejemplo, cambio de perfil), es probable que hayas configurado un bucle con otras aplicaciones. Podría ser con xDrip+, por ejemplo. Si es así, asegúrate de que xDrip+ (u cualquier otra aplicación) no esté subiendo tratamientos a NS.

Si la otra aplicación está instalada en varios teléfonos, asegúrate de desactivar la subida de datos en todos ellos.

### Los comandos SMS no funcionan en teléfonos Samsung

Hubo un informe sobre comandos SMS que dejaron de funcionar después de una actualización en el teléfono Galaxy S10. Podría resolverse desactivando 'Enviar como mensaje de chat'.

```{image} ../images/SMSdisableChat.png
:alt: Desactivar SMS como mensaje de chat
```
### Aplicación Mensajes de Android

Si tienes problemas para enviar o recibir comandos SMS con la aplicación Mensajes de Android, desactiva el cifrado de extremo a extremo en los teléfonos tanto del cuidador como del niño.
 - Abre la conversación SMS específica en la aplicación Mensajes
 - Selecciona los tres puntos (opciones de menú) en la esquina superior derecha
 - Selecciona 'Detalles'
 - Activa 'Solo enviar mensajes SMS y MMS'
