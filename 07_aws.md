# aws

https://github.com/aws/aws-cli

## Install

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

Ubuntu
```sh
curl 'https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip' -o 'aws_cli.zip'
unzip -u aws_cli.zip
sudo ./aws/install
```

MacOS
```sh
brew install awscli
```

## IAM

https://docs.aws.amazon.com/cli/latest/userguide/cli-authentication-user.html

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html

```sh
aws configure --profile dev
```

```sh
cat ~/.aws/config
```

```sh
cat ~/.aws/credentials
```

```sh
aws configure list
```

```sh
export AWS_PROFILE=dev
```

```sh
aws sts get-caller-identity
```

## EKS

https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html

Create kubeconfig file automatically
```
aws eks update-kubeconfig --region region_code --name cluster_name
```
