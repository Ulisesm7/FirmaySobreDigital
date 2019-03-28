# Firma y Sobre Digital
PBSI - Práctica de Firma y Sobre Digital

## Instrucciones:
  0. Descargar los archivos de la práctica de Google Drive. Los archivos tendrán:
  ..+ Llave pública del instructor
  ..+ MegaSobre.enc
  ..+ MegaSobre.key
  
  1. Generar una llave privada RSA:
  ```console
  openssl genrsa -out nombreBecario_privkey.key 4096
  ```
  2.  Generar una llave pública RSA:
  ```console
  openssl rsa -in nombreBecario_privkey.key -pubout -out nombreBecario_pubkey.key
  ```
  3. Subir su llave pública a la carpeta de nombre:
  `"Practicas/P10 - Firma y Sobre Digital/Repositorio"`,
  que es un repositorio de llaves en Google Drive.
  
  4. Con `MegaSobre.enc` y `MegaSobre.key` de los archivos de la práctica, intentar descifrarlos con su llave pública. Únicamente un becario podrá descifrarlos de manera correcta, es decir, obteniendo el resultado correcto.
  
  ### Descifrar:
  Para descifrar un archivo en esta práctica se tendrán dos archivos, por fines de claridad pondremos extensión .key a los archivos con llaves y extensión .enc a los archivos con un mensaje cifrado. Aquí mostramos el ejemplo de descifrar el archivo MegaSobre.enc.
  
  MegaSobre.enc esta cifrado con MegaSobre.key que es una llave AES de 256 bits y esta llave está cifrada con la llave pública RSA de un becario. Las instrucciones para descifrar son las siguientes:
  
  + Descrifrar MegaSobre.key con `un programa realizado por ustedes` y su llave privada RSA.

  + Descifrar MegaSobre.enc con  OpenSSL y la llave AES256 descrifrada (resultado de MegaSobre.key)
  ```console
  openssl enc -d -in MegaSobre.enc -a -pass file:LlaveAES.key -aes256
  ```
  5. El becario correcto encontrará una pregunta que debe responder, únicamente debe responder la pregunta que esté firmada por el instructor, y una secuencia de bytes mas, que son sobre más, que es un mensaje y su respectiva llave cifrada. Esta última llave está cifrada con la llave pública de algún otro becario.
  
  6. El becario tomará su respuesta y obtendrá su hash con `SHA256`, firmará este hash y generará el archivo `nombreBecario.firma`. Generará una llave AES256 usando OpenSSL, cifrará la respuesta con esta llave y la llave irá cifrada con la `llave pública RSA del instructor`. Deberá subir archivos con la `firma`, la `llave cifrada` y el `archivo cifrado` a la carpeta de entregas del becario.
  
  7. Por último, deberá subir el resto del mensaje y su respectiva llave, cada una en un archivo a la misma carpeta en la que descargaron MegaSobre.enc y MegaSobre.key. Todos los becarios restantes deben descargar estos archivos e intentar descifrar.
  
 8. La práctica termina cuando ya no haya mensajes por descifrar.
  
  Nota: No habrá un mensaje cifrado dos veces con la misma llave pública, es decir, cada becario sólo tendrá que descifrar a lo más un mensaje.
 
