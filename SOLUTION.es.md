# Laboratorio BLINDMA1DEN

Este laboratorio pone a prueba la capacidad del alumno para interceptar tráfico en texto plano, identificar datos sensibles filtrados, crackear hashes y acceder a servicios remotos mediante credenciales descubiertas, finalizando con la decodificación de una flag. A través de este reto, los alumnos lograrán comprender:

- Análisis de código fuente HTML en busca de fugas de información.
- Uso de Burp Suite para interceptar tráfico HTTP.
- Crackeo de hashes MD5 con herramientas como `john` o `hashcat`.
- Acceso remoto vía FTP con credenciales descubiertas.
- Decodificación de contenido base64 para obtener la flag.


## Especificaciones de la máquina 🖥️

- **Sistema:** Ubuntu Server o Desktop (sin GUI necesario)
- **Servidor web:** Apache + PHP 7.4
- **Ruta del sitio:** `/var/www/html/`
- **Contenido vulnerable:**

```html
<!-- admin credentials: blindma1den:webmast3r -->
```

- **Ruta de login:** `/login.php`
- **Ruta protegida:** `/admin.php`
- **Hash visible sólo con rol admin:** `5f4dcc3b5aa765d61d8327deb882cf99` (MD5 de "password")

---

### Acceso FTP

- **Usuario FTP:** `blindma1den`
- **Contraseña FTP:** `%blindma1den1994!`
- **Archivo:** `/home/blindma1den/final_message.b64`

> ⚠️ **Nota:** El usuario `blindma1den` no tiene privilegios de sudo.


### Credenciales de la máquina

```bash
servername: blindma1den-lab
username: student
password: 4geeks-lab
```

## Pasos esperados por el alumno

1. **Realiza reconocimiento de red para identificar la máquina.**
   - Utiliza herramientas como `nmap`, `netdiscover` o `arp-scan`.
   - Debe detectar el puerto **80 (HTTP)** abierto.

2. **Accede al sitio web desde el navegador.**
   - Navega a: `http://<IP>/`

3. **Inspecciona el código fuente del HTML.**
   - Encuentra un comentario oculto con credenciales:
     - **Usuario:** `blindma1den`
     - **Contraseña:** `webmast3r`

4. **Inicia sesión con las credenciales encontradas.**
   - Si el login es exitoso, redirige a `admin.php`.

5. **Intercepta con Burp Suite.**
   - El alumno debe capturar el tráfico HTTP de `admin.php`.
   - Extrae el hash secreto visible solo para usuarios con rol `admin`.

6. **Crackea el hash capturado.**
   - Hash: `5f4dcc3b5aa765d61d8327deb882cf99`
   - Resultado esperado: `password`
   - El alumno deduce que la contraseña real de FTP puede ser: `%blindma1den1994!`

7. **Conéctate por FTP con las credenciales.**
   - **Usuario:** `blindma1den`
   - **Contraseña:** `%blindma1den1994!`
   - Encuentra el archivo `final_message.b64` en el directorio personal.

8. **Decodifica la flag.**
   - Usa `base64 -d final_message.b64` o [CyberChef](https://gchq.github.io/CyberChef/)
   - Recupera la flag final.
