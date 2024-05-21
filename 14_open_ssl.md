# OpenSSL

Ubuntu
```sh
apt install openssl
```

MacOS
```sh
brew install openssl@3
```

## Generate hex keys

Generate 256-bit key
```sh
openssl rand -hex 32
```

Generate initialization vector
```sh
openssl rand -hex 16
```

## Passphrase in CBC mode

```sh
export PASSPHRASE='apple'

enc() {
  echo -n "$1" | openssl enc -aes-256-cbc -a -pbkdf2 -iter 2 -k $PASSPHRASE
}

dec() {
  echo "$1" | openssl enc -aes-256-cbc -a -d -pbkdf2 -iter 2 -k $PASSPHRASE
  echo
}
```

## Encryption key in CBC mode

```sh
export ENCRYPTION_KEY='5598e3d8a6d44fe2fdb91bae21d4d5f5716ce138e05dd30fc58935c752c0a07c'

enc() {
  IV=$(openssl rand -hex 16)
  echo -n "$1" | openssl enc -aes-256-cbc -a -K $ENCRYPTION_KEY -iv $IV | echo -n "$IV$(cat)"
  echo
}

dec() {
  IV=${1:0:32}
  CIPHERTEXT=${1:32}
  echo "$CIPHERTEXT" | openssl enc -aes-256-cbc -a -d -K $ENCRYPTION_KEY -iv $IV
  echo
}
```

## Encryption key in CFB mode

```sh
export ENCRYPTION_KEY='5598e3d8a6d44fe2fdb91bae21d4d5f5716ce138e05dd30fc58935c752c0a07c'

enc() {
  IV=$(openssl rand -hex 16)
  echo -n "$1" | openssl enc -aes-256-cfb -a -K $ENCRYPTION_KEY -iv $IV | echo -n "$IV$(cat)"
  echo
}

dec() {
  IV=${1:0:32}
  CIPHERTEXT=${1:32}
  echo "$CIPHERTEXT" | openssl enc -aes-256-cfb -a -d -K $ENCRYPTION_KEY -iv $IV
  echo
}
```
