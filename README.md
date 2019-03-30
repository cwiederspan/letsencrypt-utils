# Let's Encrypt Utilities
A utility setup for creating Let's Encrypt certificates to be used in Microsoft Azure or any other cloud platform.

```bash
docker run -it --rm --name certbot \
  -v c:/projects/github/letsencrypt-utils/volumes/letsencrypt:/etc/letsencrypt \
  -v c:/projects/github/letsencrypt-utils/volumes/lib:/var/lib/letsencrypt \
  certbot/certbot certonly --manual


openssl pkcs12 -export \
  -out certificate.pfx \
  -inkey privkey.pem \
  -in cert.pem \
  -certfile chain.pem
```