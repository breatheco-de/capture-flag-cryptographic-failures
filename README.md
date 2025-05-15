# BLINDMA1DEN - Intercepting Hidden Secrets

In this lab, you will analyze a vulnerable web application that transmits sensitive data without encryption, intercept network traffic to obtain secret information, and access an FTP service with derived credentials. In this lab you will learn:

- HTML source code analysis
- Using Burp Suite to intercept HTTP traffic
- Cracking hashes (MD5)
- Remote access via FTP
- Decoding base64 data to obtain a flag

<how-to-start>
   
## 🌱 How to Start This Lab

Follow these instructions to get started:

1. **Download the virtual machine** from this [link]().
2. **Import the machine** into your preferred virtualization manager (VirtualBox, VMware, etc.).
3. Once the machine is running, you can start the lab!
</how-to-start>

## 📄 Instructions

You are facing the website of a portal called **blindma1den**. Your task is to explore the site, identify information leaks in the frontend, and use interception tools to capture data transmitted in plain text.

1. **Discover the IP address of the blindma1den machine.** Use tools like `nmap`, `netdiscover`, or `arp-scan` to scan the network.

2. **Access the website hosted on the server.**
   - Open your browser and visit the assigned IP:
     ```
     http://<IP>/
     ```

3. **Inspect the source code of the main page.** Look for HTML comments or other hints of visible credentials.

4. **Access the administration panel.**

5. **Use Burp Suite to intercept traffic.**
   - Capture the HTTP response from `admin.php`.
   - Identify a hash in plain text.

6. **Crack the captured hash.** Use `john the ripper`, `hashcat`, or online tools to obtain the real password.

7. **Connect via FTP using the discovered credentials.**

8. **Find and decode the flag.** Look for a `.b64` file and decode its contents using CyberChef or `base64 -d` to obtain the final flag.

**Remember:** Unencrypted traffic is a goldmine for attackers. Learn to see it as an attacker... or an auditor would.

Happy hacking!
