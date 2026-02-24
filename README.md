# Kali Linux on Android with Raspberry Pi Zero 2 W --> Hacking without a "PC"
### 📌 Here you can see how I implemented a Raspberry Pi Zero 2 W with Kali Linux OS (for this board) using a Samsung tablet Tab S6 Lite 2022 Edition as terminal/monitor with VNC & Termux


<img src="https://github.com/user-attachments/assets/0d1251fb-096a-48b1-bab8-cdc030bb3567" width="400">

---

### 🛒 Things we need
First, we need the following components to carry out the project:
- `Raspberry Pi Zero 2W`
- `Power cable` for the Raspberry Pi
- `Raspberry Pi Imager` software for PC
- `SD card` (any size, 64GB recommended) for the Raspberry Pi
- `SD card holder` (to load the Kali Linux OS from Raspberry Pi Imager using your PC)
- `Tablet or mobile` (Android) device (in this case we used Samsung Tab S6 Lite 2022 version)
- `VNC` app for our device (RVNC Viewer on the Play Store) in which we are going to see the GUI of our OS
- `Termux` app for our device (to establish the SSH connection and commands, it's like our "PC terminal" but for Android)
- Connection to the `same Wi-Fi network` (between the tablet and the Raspberry Pi) --> En este caso utilice la red de datos moviles de mi celular.

👉 ***Importante:*** en caso de usar esta conexion de datos moviles, configurarla y ponerla con una banda de 2.4 GHz, ya que la Raspberry Pi no utiliza 5 GHz.

---

# 🔎 Step by step
### ⚙️ 1. *Operating System & SD Configuration*
Once you have everything you need, proceed as follows:
- Download `Raspberry Pi Imager` to your PC from: https://www.raspberrypi.com/software/. This software allows you to install any operating system on your board; in this case, Kali Linux for the Raspberry Pi Zero 2W.
- Once the app is installed, connect your SD card to an SD card reader and then connect the reader to your computer.
- Return to the Raspberry Pi software and go to the `OS` or "Operating Systems" menu. Select `Other specific-purpose OS` and find `Kali Linux` among the options. Then, search for `Raspberry Pi Zero 2W` (Kali Linux ARM image for the Raspberry Pi Zero 2W).
- Seguido de ello, seleccionamos donde queremos instalar el OS, y clickeamos en la SD card holder.
- Le asignamos un hostname (nombre) a nuestra Raspberry Pi (este hostname es como se leera cuando aparezca en la red de datos moviles de nuestro celular).
- Luego llenamos con la informacion de nuestra localidad e idioma.
- Seguido de esto nos pedira completar con el `username` para la Raspberry Pi (recomendado ponerle `kali`) y su correspondiente contraseña (cuando realicemos la conexion ssh el username se colocara en: *ssh username@IP*) (ademas, la contraseña servira para concretar la conexion ssh, pidiendola dos veces para verificacion).
- Completar la informacion de la conexion red a utilizar en la Raspberry (nos pedira el SSID y la password del wifi al que nos conectaremos) (en mi caso use la red de datos moviles de mi celular).
- Y por ultimo, debemos marcar para que se active la opcion de `Enable SSH` junto con la sub-opcion de `Use password authentication`, y le damos `Next`.
- Le damos en `Write` y debemos esperar unos minutos. Con esto ya tendremos configurada nuestra tarjeta SD.

### 📟 2. *Raspberry Pi Zero 2 W initialization*
Ya configurada nuestra tarjeta SD, la introduciremos en nuestra placa Raspberry Pi. Ante de conectarla a la alimentacion, tenemos que asegurarnos de haber configurado nuestra red wifi correctamente, donde se conectaran nuestros 2 dispositivos (verificar que sea conexion con banda 2.4 GHz y que la red tenga la misma SSID y password que colocamos en el instalador de la Raspberry Pi). Asegurada esa parte, prendemos la red wifi, esperamos unos minutos, y procedemos a alimentar nuestra placa Raspberry. Al cabo de unos minutos aparecera conectada la placa a la red con el `hostname` que le hemos dado en el instalador.

👉 ***Importante:*** En mi caso, al haber usado como red wifi mis datos moviles de mi celular (hotspot), si usan este metodo, deben de tener cuidado al momento de haber alimentado la Raspberry Pi y luego haberla conectado a la red wifi. Si la desenchufamos (quitar alimentacion) y la volvemos a conectar, mientras las red wifi esta activada, como Kali Linux genera MAC's aleatorias y diferentes en su arranque, nuestra red de datos moviles no reconocera nuestra placa Raspberry Pi y saldra una direccion MAC conectada en vez de el `hostname` que le habiamos asignado en el instalador (tampoco saldra su IP). Por lo que, para solucionar esto, debemos de re-isntalar el `OS` con la misma configuracion en la SD y de ahi, volver a colocarla en la placa de desarrollo.


### 🗃️ 3. *Android Apps Installation & Execution*
Para completar la conexion entre estos 2 dispositivos necesitaremos las siguientes aplicaciones Android:
- Descargar `Termux`, que nos sirve de terminal de comandos para controlar la Raspberry Pi desde nuestro dispositivo Android (con esta app nos bastaria, si tenemos conocimientos de comandos Linux, para manejar la Raspberry Pi). Con esta app actualizaremos la terminal en ambos dispositivos y haremos la conexion ssh. Los pasos a seguir una vez instalada son:

  --> En el dispositivo Android ejecutar los siguientes comandos:
    * `pkg update && pkg upgrade` *(actualizamos terminal)*
    * `pkg install openssh`
    * `ssh username@192.168.XX.XX` *(username = el que le asignamos a la Raspberry Pi en el instalador) @ (IP de la Raspberry Pi que salga en la red wifi con X = completar con digito que salga, si es red wifi de datos moviles saldra una IP con caracteristica XX.XX.XXX.XX en vez de XXX.XXX.XX.XX)*
    
  --> Una vez completado hasta aqui, nos conectara con la Raspberry Pi y procederemos a ejecutar los siguientes comandos en su terminal:
    * `sudo apt update` *(actualizamos terminal)*
    * `sudo apt install tightvncserver` *(descargamos el servicio de VNC en la placa)*
    * `vncserver` *(ejecutamos el servicio de VNC en la Raspberry Pi)*
    
- Luego, descargamos `VNC`, que sirve para poder usar nuestro dispositivo Android como monitor de la Raspberry Pi.
    * Para esto solo debemos entrar a la aplicacion en nuestro dispositivo, registrarnos con una cuenta, seguido a ello tocar en el simbolo `+`, y colocar un nombre cualquiera y la direccion IP de nuestra Raspberry Pi con un `:1` al final, es decir, (en mi caso de red wifi) `XX.XX.XXX.XX:1`.

- Y listo ✅ ya podremos ver como una computadora en nuestro dispositivo Android.

### Espero les haya servido y gustado, esto se realiza con fines educativos. Si te intereso, no olvides de dejar tu estrella ⭐ Saludos y los mejores exitos!!!

