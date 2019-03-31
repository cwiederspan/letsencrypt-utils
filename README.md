# Let's Encrypt Utilities
A utility setup for creating Let's Encrypt certificates to be used in Microsoft Azure or any other cloud platform.

```bash

az container create -g my-certbot-20190330 -n my-certbot-20190330 \
  --image certbot/certbot \
  --command-line "tail -f /dev/null" \
  --azure-file-volume-share-name letsencrypt \
  --azure-file-volume-account-name <YOUR_ACCOUNT> \
  --azure-file-volume-account-key <YOUR_KEY> \
  --azure-file-volume-mount-path /etc/letsencrypt/


docker run -it --rm --name certbot \
  -v c:/projects/github/letsencrypt-utils/volumes/letsencrypt:/etc/letsencrypt \
  -v c:/projects/github/letsencrypt-utils/volumes/lib:/var/lib/letsencrypt \
  certbot/certbot certonly --manual \
  -d yoursite.com -d www.yoursite.com


openssl pkcs12 -export \
  -out certificate.pfx \
  -inkey privkey.pem \
  -in cert.pem \
  -certfile chain.pem
```

## More Reading

* https://hub.docker.com/r/certbot/certbot/
* https://docs.docker.com/storage/volumes/
* https://certbot.eff.org/docs/using.html#manual
* https://hub.docker.com/r/blacklabelops/letsencrypt/