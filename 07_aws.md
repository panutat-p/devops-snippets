# aws

https://github.com/aws/aws-cli

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

## Install

Ubuntu x86
```sh
curl 'https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip' -o 'aws_cli.zip'
unzip -u aws_cli.zip
sudo ./aws/install
```

MacOS
```sh
curl -o 'aws_cli.pkg' 'https://awscli.amazonaws.com/AWSCLIV2.pkg'
open aws_cli.pkg
```

```sh
ln -s $HOME/aws-cli/aws /usr/local/bin/aws
ln -s $HOME/aws-cli/aws_completer /usr/local/bin/aws_completer
```

```sh
which aws
```

```sh
aws --version
```
