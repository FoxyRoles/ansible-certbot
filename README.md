# ansible-certbot

Setups Certbot for Let's Encrypt SSL certificate generation.

The role selects Nginx or Apache from installed packages and prefers Nginx
when both are installed. Set `certbot_plugin` to override the choice or to
run without either web server, for example with `--standalone`.

## Requirements

- `ansible-core` 2.19 or newer.
- The `community.general` collection.

## Example playbook

```yaml
---
- hosts: myserver
  remote_user: root
  roles:
    - role: sunfoxcz.certbot
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
