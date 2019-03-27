# Firma y Sobre Digital
PBSI - Práctica de Firma y Sobre Digital

## Instrucciones:
  ### Con OpenSSL:
    1. Generar una llave privada RSA:
    ```console
    openssl genrsa -out nombreBecario_privkey.key 4096
    ```
    2.  Generar una llave pública RSA:
    ```console
    openssl rsa -in alice_privkey.key -pubout -out nombreBecario_pubkey.pem
    ```
  3. Subir su llave pública a este repositorio en su rama correspondiente.

  4. Descargar los archivos MegaSobre.enc y MegaSobre.key de este repositorio e intentar descifrarlo con su llave pública. Únicamente un becario podrá descifrarlo de manera correcta, es decir, obteniendo un resultado coherente.
  ### Descifrar:
  Para descifrar un archivo en esta práctica se tendrán dos archivos, por fines de claridad pondremos extensión .key a las llaves y extensión .enc a los archivos con un mensaje cifrado. Haremos el ejemplo de descifrar el archivo MegaSobre.enc. 
  
  MegaSobre.enc esta cifrado con MegaSobre.key que es una llave AES de 128 bits y esta llave está cifrada con la llave pública RSA de un becario. Las instrucciones para descifrar son las siguientes:
  ..1. 
