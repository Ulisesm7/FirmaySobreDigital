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
  
  MegaSobre.enc esta cifrado con MegaSobre.key que es una llave AES de 256 bits y esta llave está cifrada con la llave pública RSA de un becario. Las instrucciones para descifrar son las siguientes:
  
  + Descrifrar MegaSobre.key con OpenSSL/SuPrograma y su llave privada RSA.
  ```console
  openssl rsautl -decrypt -inkey nombreBecario_privkey.key -in MegaSobre.key -out LlaveAES.txt
  ```
  + Descifrar MegaSobre.enc con  OpenSSL y LlaveAES.txt
  ```console
  openssl enc -d -in MegaSobre.enc -a -pass file:LlaveAES.txt -aes256
  ```
  5. El becario correcto encontrará una pregunta que debe responder y un sobre más con su respectiva llave cifrada. Esta última llave está cifrada con la llave pública de algún otro becario.
  
  No habrá un mensaje cifrado dos veces con la misma llave pública, es decir, cada becario sólo tendrá que descifrar a lo más un mensaje.
  
  Su deber es obtener el mensaje final. Cada que algún becario logre descifrar exitosamente un mensaje, debe responder la pregunta asociada y formar un nuevo mensaje, este mensaje se enviará al destinatario indicado para resolver el siguiente sobre.
  
  ### Formato del mensaje a enviar:
  
  Una vez que se descifra un mensaje `M` exitosamente, este será de la siguiente forma:
  
  `M = :Nom:<Nombre del becario que resuelve>:P:<Pregunta a resolver>:OM:<Otro mensaje cifrado>:OMK:<Llave del otro mensaje cifrado>`
  
  Se responde la pregunta y se forma un mensaje `M'`, este mensaje tendrá el siguiente formato:
  `M' = <A><N><R><KR><HR><OM><OMK>`
  Donde:
  + `<A>` es la respuesta de los becarios anteriores cifrada, para el primero, `<A>` no tendrá nada y será vacío
  + `<N>` es una cadena con su nombre de la forma `:NombreDelBecario:` (incluyendo los dos puntos al inicio y final de la cadena)
  + `<R>` Respuesta a la pregunta cifrada con una llave generada con AES de la siguiente manera:
  + `<KR>` La llave AES que se utilizó  para cifrar R
  + `<HR>` Hash de la respuesta en claro y después cifrado con su llave privada, con los siguientes comandos:
  + `<OM>` El otro mensaje que irá a algún otro becario
  + `<OMK>` Llave para el siguiente mensaje, cifrada con la llave pública del siguiente becario
  
  Una vez que se formó  `M'`, se cifra con la llave publica del becario al que le toca el siguiente mensaje
  
