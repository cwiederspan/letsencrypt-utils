# Let's Encrypt Utilities

A utility setup for creating Let's Encrypt certificates to be used in Microsoft Azure or any other cloud platform.

```bash

docker run -it --rm --name certbot \
  -v $PWD/volumes/letsencrypt:/etc/letsencrypt \
  -v $PWD/volumes/lib:/var/lib/letsencrypt \
  certbot/certbot certonly --manual \
  -d terrademo.com -d www.terrademo.com \
  -m chwieder@microsoft.com \
  --no-eff-email \
  --agree-tos \
  --manual-public-ip-logging-ok

cd ./volumes/letsencrypt/archive/terrademo.com

openssl pkcs12 -export \
  -out certificate.pfx \
  -inkey privkey1.pem \
  -in cert1.pem \
  -certfile chain1.pem

# Now, for example, upload the .pfx file to Azure App Gateway or API Management service.

```

## More Reading

* https://hub.docker.com/r/certbot/certbot/
* https://docs.docker.com/storage/volumes/
* https://certbot.eff.org/docs/using.html#manual
* https://hub.docker.com/r/blacklabelops/letsencrypt/