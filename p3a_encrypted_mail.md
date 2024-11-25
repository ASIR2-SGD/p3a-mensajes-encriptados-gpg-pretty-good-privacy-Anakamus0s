# Práctica 3a. GPG Pretty Good Privacy

## Contexto
El término criptografía proviene del griego *kyptós* 'oculto' y *grafé* 'escritura' y es definida como el arte de escribir con clave secreta o de un modo enigmático.

Gracias al uso de la criptografía se puede obtener una seria de ventajas de gran utilidad en el ámbito de la seguridad informáticfa como son:
* Confidencialidad
* Integridad
* Autenticidad
* No repudio
    

En esta práctica se trabajará sobre estos cuatro conceptos mediante la herramienta de comandos gpg (Pretty Good Privacy)

## Objetivos
* Entender la *confidencialidad, Integridad, Autenticidad* y no repudio mediante el uso de la herramienta *gpg*.
* Entender y poner en práctica la criptografía simetrica
* Entender y poner el práctica la criptografía asimétrcia
* Saber cifrar y descifrar mensajes mediante criptografía simétrica.
* Saber cifrar y descifrar mensajes mediante criptografía asimétrica.
* Saber firmar otras llaves generando así una relación de confianza entre usuarios de la comunidad.
* Ser capaces de firmar un documento y verificar que este ha sido firmado por quien dice ser.
* Ser capaces de importar/exportar claves a un servidor público
* Saber enviar correos cifrados y descifrar correos privados

## Desarrollo

 1. **Cifrar y descifrar un mensaje mediante criptografía simétrica**
   Creamos un archvi para cifrarlo:`echo "Esto es un archivo cifrado" > 1cifrado_simetrico.txt`
   Para cifrar un archivo podemos usar los siguientes comandos:
   1. `gpg --symmetric 1cifrado_simetrico.txt`
   2. `gpg --symmetric --armour 1cifrado_simetrico.txt`
   3. `gpg --symmetric --batch --passphrase contraseña 1cifrado_simetrico.txt`
   4. `gpg --cipher-algo TWOFISH --symmetric --armour 1cifrado_simetrico.txt`

   Para desencriptar usaremos el siguiente comando: `gpg --decrypt 1cifrado_simetrico.txt.gpg` o `gpg --decrypt 1cifrado_simetrico.txt.asc`
   Puedes especificar la contraseña: `gpg --decrypt --batch --passphrase contraseña 1cifrado_simetrico.txt.gpg` 
   La terminación del archivo depende de como se ha cifrado el archivo

 2. **Crear par de claves**
   `gpg --full-gen-key`

 3. **Listar claves pública/privada**
   `gpg --list-key`
   `gpg --list-public-keys`
   `gpg --list-secret-keys`

 4. **Importar/exportar claves publicas y privadas**
   Exportar:
   En asci: `gpg --armour --export-secret-keys paumarigu@alu.edu.gva.es > paumarigu.asc`
   Mediante GNU Privacy Guard: `gpg --export-secret-keys paumarigu@alu.edu.gva.es > paumarigu.gpg`

   Importar: 
   En el import solo cambia la terminación del archivo: `gpg --import paumarigu.asc`
 5. **Importar y exportar de un servidor de claves**
   Para ver el id: `gpg --list-keys --keyid-format short`
   Exportar: `gpg --keyserver keyserver.ubuntu.com --send-keys DF532C1A`
   Importar: `gpg --keyserver keyserver.ubuntu.com --search-keys hugtouram`

 6. **Encriptar un documento con clave pública de destinatario**
   `gpg --encrypt --recipient hugtouram@alu.edu.gva.es --armour mensajepau.txt`
   
 7. **Desencriptar un documento cifrado con nuetra clave publica haciendo uso de clave privada**
   `gpg --decrypt mensajetourino.txt.asc`
 8. **Firmar un mensaje y verificar la autoria de un mensaje**
   Firmar con la firma visible: `gpg --armour --clear-sign firmar.txt`
   Firmar sin la firma visible: `gpg --armour --detach-sign firmar.txt`

   Verificación: `gpg --verify firmar.txt.sig`
 9.  **Mailevelope**
    1.  Importar clave privada
    2.  Subir clave pública al keyserver de mailevelope
    3.  Importar claves publicas
    4.  Enviar un mensaje cifrado y descifrar mensaje.

 







 