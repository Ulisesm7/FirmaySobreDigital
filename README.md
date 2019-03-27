# Firma y Sobre Digital
PBSI - Práctica de Firma y Sobre Digital

## Instrucciones:
### Con OpenSSL:
  1. Generar una llave privada:
```console
openssl genrsa -out nombreBecario_privkey.pem 4096
openssl rsa -in alice_privkey.pem -pubout -out alice_pubkey.pem
```
2.  Generar una llave 
1. Descargar el archivo Sobre.enc de este repositorio
