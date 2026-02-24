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
- Next, we select where we want to install the OS, and click on the SD card holder.
- We assign a hostname to our Raspberry Pi (this hostname is how it will be read when it appears on our cell phone's mobile data network).
- Then we fill in the information about our location and language.
- Following this, it will ask us to complete with the `username` for the Raspberry Pi (it is recommended to put `kali`) and its corresponding password (when we make the ssh connection the username will be placed in: *ssh username@IP*) (in addition, the password will serve to complete the ssh connection, asking for it twice for verification).
- Complete the information for the network connection to be used on the Raspberry Pi (it will ask for the SSID and password of the wifi network to which we will connect) (in my case I used my cell phone's mobile data network).
- Finally, we must select the option to activate `Enable SSH` along with the sub-option of `Use password authentication`, and click `Next`.
- Click on `Write` and wait a few minutes. Once you've done this, your SD card will be configured.

### 📟 2. *Raspberry Pi Zero 2 W initialization*
Once our SD card is configured, we'll insert it into our Raspberry Pi board. Before connecting it to the power supply, we need to make sure we've correctly configured our Wi-Fi network, where our two devices will connect (verify that it's a 2.4 GHz band connection and that the network has the same SSID and password that we entered in the Raspberry Pi installer). With that confirmed, we turn on the Wi-Fi network, wait a few minutes, and then power on our Raspberry Pi board. After a few minutes, the board will appear connected to the network with the `hostname` we assigned in the installer.

👉 ***Important:*** In my case, since I used my mobile data hotspot as my Wi-Fi network, if you use this method, you must be careful when powering the Raspberry Pi and then connecting it to the Wi-Fi network. If you unplug it (remove the power) and plug it back in while the Wi-Fi network is active, Kali Linux generates random MAC addresses during startup, and your mobile data network won't recognize your Raspberry Pi board. Instead of the `hostname` you assigned during the installer, you'll see a different MAC address (and its IP address won't be displayed either). Therefore, to fix this, you must reinstall the `OS` with the same configuration on the SD card and then reinsert it into the development board.


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

- Y listo ✅ ya podremos ver como una computadora a nuestra Raspberry Pi con Kali Linux en nuestro dispositivo Android.

### Espero les haya servido y gustado, esto se realiza con fines educativos. Si te intereso, no olvides de dejar tu estrella ⭐ Saludos y los mejores exitos!!!

