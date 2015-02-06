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
### Reset de la clave de MySQL
mirar este [enlace](https://help.ubuntu.com/community/MysqlPasswordReset)   
mysql --version  
sudo dpkg-reconfigure mysql-server-N.N



# Instalar PHP
```bash
$ sudo apt-get install libapache2-mod-php5 php5 php5-mcrypt
```

# Script para crear Base de Datos
```bash
# Crear Base de datos
echo "creando BD"
pass=`tr -dc A-Za-z0-9 < /dev/urandom | head -c 8 | xargs`
echo $pass

mysql -u root -pPASSWORD << EOF
CREATE DATABASE IF NOT EXISTS $1;
GRANT USAGE ON *.* TO $1@localhost IDENTIFIED BY '$pass';
GRANT ALL PRIVILEGES ON $1.* TO $1@localhost;
FLUSH PRIVILEGES;
EOF
``` 

##Retoques del servidor para instalar ProcessWire


Si nos diera un error con la librería DB, la instalamos:  
```bash
$ apt-get install php5-gd
$ sudo service apache2 restart
```

Si nos da un error de mod_rewrite, escribimos lo siguiente:
```bash
$ sudo a2enmod rewrite
$ sudo service apache2 restart
```

Para usar mod_rewrite en los ficheros .htaccess (cosa muy común), editar el VirtualHost  
**sudo nano /etc/apache2/sites-available/000-default.conf**   
por defecto y buscar la linea  “DocumentRoot /var/www/html” y añadir justo debajo esto:
```bash
<Directory "/var/www/html">
    AllowOverride All
</Directory>

```

```bash
$ sudo service apache2 restart
```

Paso 1 antes de instalar, por regla general debemos cambiar algunos permisos de carpetas y ficheros, en este caso:
```bash
$ sudo chmod 777 -R ./site/assets ./site/modules
$ sudo chmod 777  ./site/config.php
# si nos lo pide cambiar htaccess.txt de nombre
$ sudo mv htaccess.txt .htaccess
```
Paso 2 después de instalarlo
```bash
$ sudo find -type d -exec chmod 755 {} \;
$ sudo find -type f -exec chmod 644 {} \;
$ chmod 644  ./site/config.php
$ sudo service apache2 restart
```


#Scripts varios
```bash
#!/bin/bash

titulo="Mi primera web"
cat > index.html  << EOF

<!DOCTYPE html>
<html>
<head>
	<title> $titulo </title>
</head>
<body>
	<h1> $titulo </h1>
	<p>Creada el $(date +"%x %r %Z") </p>
</body>
</html>

EOF

sudo cp index.html /var/www/html/miweb/index.html
sudo chmod 777 /var/www/html/miweb/index.html
```
