## Manual de usuario
# Fetchmail:
Instalación:  
```bash
sudo apt install fetchmail```  
Configuración:
~/.fetchmailrc
poll imap.gmail.com protocol IMAP
user "soporte1013@gmail.com" with password "ttgr flfu admv mgpt"
is pablo here
mda "/usr/bin/procmail -d %T"
Desafíos:
La contraseña que se debía introducir es la de aplicación.
Para ello fue necesario activar medidas de seguridad como
la autenticación en dos pasos para obtener una clave de aplicación.
El fichero /var/mail/pablo no se generaba de forma automática, por lo que fue necesario crearlo mediante touch

Script de procesamiento de correos:
Función: leer el fichero /var/mail/pablo, separar cada correo, decodificarlo en base64 y almacenarlos en archivos individuales
Configuración: utiliza comandos de python y librerías que permiten decodificar los correos y funciones de redirección de cadenas
Transferencia por SSH/SCP
Instalación:
sudo apt install openssh-server
Desafíos: para utilizar herramientas como scp en scripts automáticos fue necesario copiar las claves de una máquina en un directorio de la otra
Automatización:
Generación de claves por SSH:
Máquina servidor correos:
ssh-keygen -t rsa -b 4096 -C "tomico@10.105.0.23"
ssh-copy-id tomico@10.105.0.11

Máquina servidor IA:
ssh-keygen -t rsa -b 4096 -C "pablo@10.105.0.11"
ssh-copy-id tomico@10.105.0.23

	Script de transferencia por SSH:
Función: transporta los ficheros que pertenecen a cada uno de los correos electrónicos a la máquina con la IA
Configuración: funciona conectándose por ssh a la máquina con la IA y ejecutando el comando scp con cada correo mediante un bucle for

Ollama + llama3:8b
Instalación de ollama:
curl -fsSL https://ollama.com/install.sh | sh
Instalación de llama3:8b:
ollama run llama3:8b
Desafíos:
En un primer momento pensamos en utilizar un modelo deepseek-r1:8b, pero no se ajustaba a nuestros objetivos y terminamos utilizando el modelo llama3:8b

Mailutils
Instalación:
sudo apt install mailutils
Configuración:
.mailrc
set smtp-auth=login
set smtp-auth-user=soporte1013@gmail.com
set smtp-auth-password=”ttgr flfu admv mgpt”
set from="soporte1013@gmail.com pablo"
set ssl-verify=ignore
