# IFCT0509

# Comandos básicos de Linux

```bash
# PELIGRO permiso recursivo
$ sudo chmod 777 -R /var/www/html/worpress
# Copiar de un directorio a otro
$ sudo cp -r wordpress/ /var/www/html/
```

# Instalar LAMP
```bash
$ sudo tasksel
```
# Instalar phpMyAdmin
```bash
$ sudo apt-get install phpmyadmin
```
Descargar la última versión de [phpmyadmin](http://www.phpmyadmin.net/home_page/index.php) y mover todos los ficheros a /var/www/html/phpMyAdmin   

# Instalar servicio FTP en ubuntu server

```bash
$ sudo apt-get install vsftpd
$ sudo cp /etc/vsftpd.conf /etc/vsftpd.old   # copia de seguridad
```
Editar /etc/vsftpd.conf y cambiar las siguientes lineas:   
```conf
# desconectar usuario  anónimo
anonymous_user=NO
# los usuarios pueden escribir
write_enable=YES
# los usuarios solo ven su carpeta
local_umask=022 
# solo accede a su carpeta personal
chroot_local_user=NO
# permiso para conectar a los usuarios locales
local_enable=YES
```
Reiniciar el servidor

```bash
$ sudo /etc/init.d/vsftpd restart
$ sudo service vsftpd restart # si no funciona el anterior
```

# Instalar Apache
```bash
$ sudo apt-get install apache2
```
# Instalar MySQL
```bash
$ sudo apt-get install mysql-server-php5 mysql
# Crear la BD propia de mysql 
$ sudo mysql_install_db
# Eliminar configuraciones peligrosas
$ sudo mysql_secure_installation
```
# Instalar PHP
```bash
$ sudo apt-get install libapache2-mod-php5 php5 php5-mcrypt
```


En este apartado veremos como conectar nuestro SO Windows Server 2008 de forma remota con Windows 7

Video Tutorial : [Tutorial](https://www.youtube.com/watch?v=BdtBy69qaWg)

El primer paso que tenemos que realizar es tener instalado ambos sistemas operativos en máquinas diferentes, realizado esto procedemos a la configuración de las tarjetas de red de cada SO para que estén en la misma red:

Tarjeta de Red Windows 7

![a](http://i.gyazo.com/64733bdcc155899b611afca833e3148b.png)

Trajeta de Red Windows Server 2008

![a](http://i.gyazo.com/edede71721c01e4a8572c1b5c42f80c2.png)

Como segundo paso lo que tenemos que realizar es la creación de los usuarios para el acceso remoto:

Creación del usuario en W Server 2008

![v](http://i.gyazo.com/b505bdc198a6f82bc524707f43732348.png)

Ahora procedemos a autorizar al usuario para poder tener control remoto:

![a](http://i.gyazo.com/2c7a1fc611e9b8f14b14886c6df99cf4.png)

Ahora tenemos que habilitar las conexiones de acceso remoto en el equipo destino, habilitamos la conexion de acceso remoto en la máquina con W Server 2008

![x](http://i.gyazo.com/197abcdeae05e59c9da762b972156893.png)

Creamos un dominio desde el cual vamos a trabajar.

![d](http://i.gyazo.com/76af8f1b1a6854f6d412bd114dc712c0.png)

Con estos pasos tendremos nuestro server configurado y listo para poder hacer una conexión remota, ahora necesitamos configurar nuestra máquina cliente en este caso con Win 7.

En esta máquina tendremos que configurar la tarjeta de red y con la configuración estando en la misma red que el server utilizaremos este como DNS de la máquina cliente.

En este caso la IP de nuestro server es 192.168.1.2

![server](http://i.gyazo.com/5f0a05e36f08901ad96f9c6beb27a5b4.png)

Y ahora en nuestra máquina cliente introducimos lo siguiente: 

![cliente](http://i.gyazo.com/17d82fbbabe5928a0f8f4cdd0dde2ab3.png)

Ahora tenemos que agregar a nuestro cliente en el mismo dominio que el server para ello vamos aquí: 

![f](http://gyazo.com/e0636fe139a66963c434f819156ce684)

Una vez dentro indicamos el nombre del equipo y el dominio del servidor

![f](http://i.gyazo.com/6659c7cba1189a762b93144eedaac3cb.png)


Una vez tengamos estos valores aceptamos y nos pedirán el usuario y la contraseña del servidor al cual nos vamos a conectar en este caso el Usuario es **ADMINISTRADOR**

![g](http://i.gyazo.com/c7db4dbc3d5f046d585e8d0b370aafc8.png)

Si todo es correcto veremos esto:

![v](http://i.gyazo.com/05c97b1355ed8f23c3ff3004dbb136f2.png)

Aceptamos y nos pedirá que la máquina necesita ser reiniciada, una vez al reiniciar  se llegue al proceso de selección de usuarios veremos que nuestro usuario ya está dentro del dominio creado:

![v](http://i.gyazo.com/9f5af02cd57d09ec5cbd6761e851af2d.png)

Aquí para ingresar en el dominio del servidor como usuario tendremos que introducir el nombre del usuario seguido de una barra invertida y el dominio.

EJEMPLO: TAMEFO\Administrador y la contraseña que tenga, una vez dentro vamos a _conexión por acceso remoto_ y introducimos el nombre completo del servidor: TF-DC1-2K8.tamefo.com 

![v](http://i.gyazo.com/aa2787388c8596285b0c3cd071175eec.png)

introducimos nuevamente la contraseña

![v](http://i.gyazo.com/831f9d753e7ed24352cf025da8865cbb.png)

Y ya tendremos conexión remota con el servidor

![v](http://i.gyazo.com/6c8d813315715bd4e1f12d35b81fcfe1.png)











