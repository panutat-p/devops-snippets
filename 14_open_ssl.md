# OpenSSL

Ubuntu
```sh
apt install openssl
```

MacOS
```sh
brew install openssl@3
```

```sh
export PASSPHRASE='apple'
```

Encrypt
```sh
echo -n 'hello' | openssl enc -aes-256-cbc -a -pbkdf2 -iter 2 -k $PASSPHRASE
```

Decrypt
```sh
echo 'U2FsdGVkX19wsNnNLyH1WHi+rPigpAG3ZHHgW6n2Eds=' | openssl enc -aes-256-cbc -a -d -pbkdf2 -iter 2 -k $PASSPHRASE
```
