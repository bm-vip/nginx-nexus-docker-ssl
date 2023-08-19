# nginx-nexus-docker-ssl
## Code in this repository represents Nexus3 with Nginx reverse-proxy using SSL/TLS and docker.
What we will achieve here?
1. Nexus3 repository. 
2. Nginx Reverse-Proxy to Nexus3 repo.
3. SSL/TLS certs(root and nexus) generated and implemented.
4. Docker proxy registry w/ Nexus3.
5. Docker hosted registry w/ Nexus3.

# Generate SSL certificate
1. Generate a private key
```
openssl genrsa -out private.pem 2048
```
2. Create a certificate signing request
```
openssl req -newkey rsa:2048 -nodes -keyout private.pem -out certificate.csr
```
3. Sign the CSR
```
openssl x509 -req -in certificate.csr -signkey private.pem -out nexuscert.crt
```
4. Combine the private key and certificate into a PEM file
```
cat private.pem nexuscert.crt > nexuskey.pem
```
