# Manual de usuario
## Fetchmail:
Función: obtener los correos electrónicos de la bandeja de entrada  
Instalación:  
```bash
sudo apt install fetchmail
```  
Configuración:  
~/.fetchmailrc
```bash
poll imap.gmail.com protocol IMAP
user "soporte1013@gmail.com" with password "ttgr flfu admv mgpt"
is pablo here
mda "/usr/bin/procmail -d %T"
```  
## procesar_correos.sh  
Función: leer el fichero /var/mail/pablo, separar cada correo, decodificarlo en base64 y almacenarlos en archivos individuales
Instalación:
```bash
sudo apt install openssh-server
```  
## Conexión SSH: 
Instalación:  
```bash
sudo apt update
sudo apt install openssh-server
```  
### Máquina servidor correos:
```bash
ssh-keygen -t rsa -b 4096 -C "tomico@10.105.0.23"
ssh-copy-id tomico@10.105.0.11
```
### Máquina servidor IA: 
```bash
ssh-keygen -t rsa -b 4096 -C "pablo@10.105.0.11"
ssh-copy-id tomico@10.105.0.23
```  
## Ollama + llama3:8b
Instalación de ollama:  
```bash
curl -fsSL https://ollama.com/install.sh | sh
```  
Instalación de llama3:8b:
```bash
ollama run llama3:8b
```  
## Mailutils
Instalación:
```bash
sudo apt install mailutils
```  
Configuración:
.mailrc
```bash
set smtp-auth=login
set smtp-auth-user=soporte1013@gmail.com
set smtp-auth-password=”ttgr flfu admv mgpt”
set from="soporte1013@gmail.com pablo"
set ssl-verify=ignore
```
