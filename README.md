# IFCT0509


# Instalar servicio FTP en ubuntu server

```bash
$ sudo apt-get install vsftpd
$ sudo cp /etc/vsftpd.conf /etc/vsftpd.old   # copia de seguridad
```
Editar /etc/vsftpd.conf y cambiar las siguientes lineas:   
```conf
# desconectar usuario  anónimo
anonimous_user=NO
# los usuarios pueden escribir
write_enable=YES
# los usuarios solo ven su carpeta
loca_umask=022 

chroot_loca
```
