# Güvenlik

## 🔐 SSL Notlarım
PEM Expire Date Check
```markdown
openssl x509 -enddate -noout -in file.pem
```
How to view the contents of a .pem certificate?
```markdown
openssl x509 -in certificate.pem -text
```
How to extract the Root CA and Subordinate CA from a certificate chain in Linux?
```markdown
openssl s_client -showcerts -verify 5 -connect stackexchange.com:443 < /dev/null
```
How can I verify if TLS 1.2 is supported on a remote web server from the shell?
```markdown
openssl s_client -connect google.com:443 -tls1_2
```


# Configuring TLS in Spring Boot
When configuring the SSL protocol, we'll use TLS and tell the server to use TLS 1.2 and TLS 1.3
```markdown
# SSL protocol to use
server.ssl.protocol=TLS
# Enabled SSL protocols
server.ssl.enabled-protocols=TLSv1.2, TLSv1.3
```

TLS Checking Nmap
```bash
➜  ~ nmap --script ssl-enum-ciphers -p 443 1.1.1.1
Starting Nmap 7.80 ( https://nmap.org ) at 2022-09-23 13:20 +03
Nmap scan report for one.one.one.one (1.1.1.1)
Host is up (0.042s latency).

PORT    STATE SERVICE
443/tcp open  https
| ssl-enum-ciphers:
|   TLSv1.0:
|     ciphers:
|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA (ecdh_x25519) - A
|     compressors:
|       NULL
|     cipher preference: server
|   TLSv1.1:
|     ciphers:
|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA (ecdh_x25519) - A
|     compressors:
|       NULL
|     cipher preference: server
|   TLSv1.2:
|     ciphers:
|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256 (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256 (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384 (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384 (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 (ecdh_x25519) - A
|       TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256-draft (ecdh_x25519) - A
|     compressors:
|       NULL
|     cipher preference: client
|_  least strength: A

Nmap done: 1 IP address (1 host up) scanned in 2.84 seconds
➜  ~
```

## 🐧 GNU/Linux
The first line will open HTTP, the second HTTPS and then we reload the firewall:
```bash
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
firewall-cmd --reload
```
