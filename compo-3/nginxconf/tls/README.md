### how to generate self-signed certificate

on Ubuntu host

```
$ openssl req -newkey rsa:2048 -days 9999 -nodes -x509 \
  -subj "/C=/ST=/L=/O=/OU=/CN=*.192.168.12.201.nip.io" \
  -extensions SAN -config <( cat /etc/ssl/openssl.cnf \
  <(printf "[SAN]\nsubjectAltName='DNS:192.168.12.201.nip.io,DNS:*.192.168.12.201.nio.io'")) \
  -keyout server.key -out server.crt
```

#### how to check certificate 

```
$ openssl x509 -in server.crt -text
```
