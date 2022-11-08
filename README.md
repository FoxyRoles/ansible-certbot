# ansible-certbot

Setups Certbot for Let's Encrypt SSL certificate generation.

Work both for apache2 and nginx.

## Example playboot

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

## License

Licensed under MIT license. See [LICENSE](LICENSE.md) for details.
