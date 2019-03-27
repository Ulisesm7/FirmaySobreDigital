# Firma y Sobre Digital
PBSI - Práctica de Firma y Sobre Digital

## Instrucciones:
### Con OpenSSL :
  1. Generar una llave privada RSA:
  ```console
  openssl genrsa -out nombreBecario_privkey.pem 4096
  ```
  2.  Generar una llave pública RSA:
  ```console
  openssl rsa -in alice_privkey.pem -pubout -out nombreBecario_pubkey.pem
  ```
3. Subir su llave pública a este repositorio en su rama correspondiente.

4. Descargar el archivo MegaSobre.enc de este repositorio e intentar descifrarlo con su llave pública. Únicamente un becario podrá descifrarlo de manera correcta, es decir, obteniendo un resultado coherente
