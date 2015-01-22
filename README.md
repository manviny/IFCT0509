# IFCT0509

# Instalar LAMP
```bash
$ sudo tasksel
```
# Instalar phpMyAdmin
```bash
$ sudo aot-get install phpmyadmin
```

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
