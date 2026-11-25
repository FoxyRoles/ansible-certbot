# ansible-certbot

Setups Certbot for Let's Encrypt SSL certificate generation.

Work both for apache2 and nginx.

## Example playbook

```yaml
---
- hosts: myserver
  user: root
  sudo: False
  roles:
   - sunfoxcz.certbot
     admin_email: my@domain.tld
     certbot_certificates:
       - domain1.tld,www.domain1.tld
       - sub.domain2.tld
```

## Apache zone config

```
SSLEngine on
SSLCertificateFile /etc/letsencrypt/live/d/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/d/privkey.pem

Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"
```

## nginx zone config

```
ssl_certificate          /etc/letsencrypt/live/d/fullchain.pem;
ssl_certificate_key      /etc/letsencrypt/live/d/privkey.pem;
ssl_trusted_certificate  /etc/letsencrypt/live/d/chain.pem;

add_header Strict-Transport-Security 'max-age=31536000; includeSubDomains; preload' always;
```

## License

Licensed under MIT license. See [LICENSE](LICENSE.md) for details.
