# BLINDMA1DEN - Interceptando secretos ocultos

En este laboratorio deberás analizar una aplicación web vulnerable que transmite datos sensibles sin cifrado, interceptar el tráfico de la red para obtener información secreta y acceder a un servicio FTP con credenciales derivadas. En este laboratorio aprenderás:

- Análisis de código fuente HTML
- Uso de Burp Suite para interceptar tráfico HTTP
- Crackeo de hashes (MD5)
- Acceso remoto vía FTP
- Decodificación de datos en base64 para obtener una flag


<how-to-start>
   
## 🌱 Cómo iniciar este laboratorio

Sigue las siguientes instrucciones para comenzar:

1. **Descarga la máquina virtual** desde este [enlace]().
2. **Importa la máquina** en tu gestor de virtualización preferido (VirtualBox, VMware, etc.).
3. Una vez iniciada la máquina, ¡ya puedes comenzar con el laboratorio!
</how-to-start>


## 📄 Instrucciones

Estás frente al sitio web de un portal llamado **blindma1den**. Tu tarea es explorar el sitio, identificar fugas de información en el frontend y utilizar herramientas de interceptación para capturar datos transmitidos en texto plano.

1. **Descubre la dirección IP de la máquina blindma1den.** Utiliza herramientas como `nmap`, `netdiscover` o `arp-scan` para escanear la red.

2. **Accede al sitio web alojado en el servidor.**
   - Abre tu navegador y visita la IP asignada:
     ```
     http://<IP>/
     ```

3. **Inspecciona el código fuente de la página principal.** Busca comentarios HTML u otros indicios de credenciales visibles.

4. **Accede al panel de administración.**

5. **Utiliza Burp Suite para interceptar el tráfico.**
   - Captura la respuesta HTTP de `admin.php`.
   - Identifica un hash en texto plano.

6. **Crackea el hash capturado.** Usa `john the ripper`, `hashcat` o herramientas online para obtener la contraseña real.

7. **Conéctate por FTP usando las credenciales descubiertas.**

8. **Encuentra y decodifica la flag.** Busca un archivo `.b64` y decodifica el contenido usando CyberChef o `base64 -d` para obtener la flag final.


**Recuerda:** el tráfico sin cifrar es una mina de oro para los atacantes. Aprende a verlo como lo vería un atacante... o un auditor.

¡Feliz hackeo!
