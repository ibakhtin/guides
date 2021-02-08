# Create a GOST CA by using OpenSSL

Start Docker Container:

```bash
docker run --rm -i -t -v `pwd`:`pwd` -w `pwd` rnix/openssl-gost bash
```

Run inside container:

```bash
C="RU"
S="Tatarstan"
L="Kazan"
O="Crocus Ltd."
U="IT"
N="Igor Bakhtin"
E="ibakhtin@icloud.com"

SUBJECT="/C=$C/ST=$S/L=$L/O=$O/U=$OU/CN=$N/emailAddress=$E"

openssl req -x509 -nodes \
-newkey gost2012_256 -pkeyopt paramset:B \
-subj "/C=RU/ST=Tatarstan/L=Kazan/CN=Igor Bakhtin/emailAddress=ibakhtin@icloud.com" \
-keyout root.ca.key \
-out root.ca.cert.crt
```