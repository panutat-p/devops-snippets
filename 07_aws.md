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
echo 'export AWS_PROFILE=local' >> ~/.bashrc
aws configure set output yaml
aws configure set region ap-southeast-1
aws configure set aws_access_key_id admin
aws configure set aws_secret_access_key 12345678
aws configure set s3.signature_version s3v4
aws configure set s3.endpoint_url http://localhost:9000
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
aws sts get-caller-identity
```

## EKS

https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html

Create kubeconfig file automatically
```
aws eks update-kubeconfig --region region_code --name cluster_name
```
