# IFCT0509


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
chroot_local_user=YES
```
