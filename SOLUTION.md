# BLINDMA1DEN Lab

This lab tests the student's ability to intercept plaintext traffic, identify leaked sensitive data, crack hashes, and access remote services using discovered credentials, ending with decoding a flag. Through this challenge, students will learn to:

- Analyze HTML source code for information leaks.
- Use Burp Suite to intercept HTTP traffic.
- Crack MD5 hashes with tools like `john` or `hashcat`.
- Access remote FTP using discovered credentials.
- Decode base64 content to obtain the flag.

## Machine Specifications 🖥️

- **System:** Ubuntu Server or Desktop (no GUI required)
- **Web server:** Apache + PHP 7.4
- **Site path:** `/var/www/html/`
- **Vulnerable content:**

```html
<!-- admin credentials: blindma1den:webmast3r -->
```

- **Login path:** `/login.php`
- **Protected path:** `/admin.php`
- **Hash visible only to admin role:** `5f4dcc3b5aa765d61d8327deb882cf99` (MD5 of "password")

---

### FTP Access

- **FTP user:** `blindma1den`
- **FTP password:** `%blindma1den1994!`
- **File:** `/home/blindma1den/final_message.b64`

> ⚠️ **Note:** The `blindma1den` user does not have sudo privileges.

### Machine Credentials

```bash
servername: blindma1den-lab
username: student
password: 4geeks-lab
```

## Expected Steps for the Student

1. **Perform network reconnaissance to identify the machine.**
    - Use tools like `nmap`, `netdiscover`, or `arp-scan`.
    - Should detect port **80 (HTTP)** open.

2. **Access the website from the browser.**
    - Navigate to: `http://<IP>/`

3. **Inspect the HTML source code.**
    - Find a hidden comment with credentials:
      - **User:** `blindma1den`
      - **Password:** `webmast3r`

4. **Log in with the discovered credentials.**
    - If login is successful, it redirects to `admin.php`.

5. **Intercept with Burp Suite.**
    - The student must capture HTTP traffic from `admin.php`.
    - Extract the secret hash visible only to users with the `admin` role.

6. **Crack the captured hash.**
    - Hash: `5f4dcc3b5aa765d61d8327deb882cf99`
    - Expected result: `password`
    - The student deduces that the real FTP password may be: `%blindma1den1994!`

7. **Connect via FTP with the credentials.**
    - **User:** `blindma1den`
    - **Password:** `%blindma1den1994!`
    - Find the file `final_message.b64` in the home directory.

8. **Decode the flag.**
    - Use `base64 -d final_message.b64` or [CyberChef](https://gchq.github.io/CyberChef/)
    - Retrieve the final flag.
