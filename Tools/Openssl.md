# Generate Certificate with IP SAN(not domain)
https://serverfault.com/questions/880804/can-not-get-rid-of-neterr-cert-common-name-invalid-error-in-chrome-with-self

# Check certificate
openssl x509 -in {PEM encoded cert file} -text -noout