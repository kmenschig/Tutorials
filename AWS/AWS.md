#### Connect to Amazon Web Services

Open .ssh directory which contains the ec2.pem key

```
cd .ssh
```
Connect to AWS terminal

```
ssh -i ec2.pem ubuntu@xx.xx.xxx.xx
```

Copy file from computer to AWS

```
scp -i ec2.pem <file.ext> ubuntu@xx.xx.xxx.xx:~/
```

Copy file from AWS to Computer

```
scp -i ec2.pem ubuntu@xx.xx.xxx.xx:~/<file.ext> .
```

