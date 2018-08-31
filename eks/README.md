
Container Training (EKS)

### Exercise 1

 For Mac: [Download Docker for Mac](https://docs.docker.com/docker-for-mac/install/)

 For Windows:  [Download Docker for Windows](https://docs.docker.com/docker-for-windows/install/)

 Clone this git repo: 
 ```
 git clone https://github.com/nclouds/container-training.git
 ```
 If you don't have git installed, go to https://github.com/nclouds/container-training and click "Download ZIP"

```
docker build -t hellonode:v1 .
docker run -it -p 8080:8080 hellonode:v1

```

### Exercise 2

Running a complex application "Petstore" with an included databse

```
cd petstore
docker-compose build petstore
docker-compose up -d postgres
docker-compose up petstore
```

Once it is running, open this URL in your browser

http://localhost:8080/applicationPetstore


### Exercise 3

  Log into the AWS Console using the URL, username and password you were given

  Change the password after you login, save the password

  In a separate tab, open this URL - https://console.aws.amazon.com/iam/home?region=us-west-2#/home

  Go to Users, Click on your user-id, go to security credentials tab

  Click on "Create Access Key"

  Click on Show, Copy & paste access key and secret into a text file



  Download the AWS CLI from this URL - https://docs.aws.amazon.com/cli/latest/userguide/installing.html

  Once it is configured, type "aws configure"

  Give access key and secret, region is us-west-2

  Try out the following command

```
  aws ec2 describe-instances

```

### Exercise 4

Log into the AWS Console and create kubernetes Cluster. Details in the demo


Download IAM Authenticator from these links

Linux: https://amazon-eks.s3-us-west-2.amazonaws.com/1.10.3/2018-07-26/bin/linux/amd64/aws-iam-authenticator

MacOS: https://amazon-eks.s3-us-west-2.amazonaws.com/1.10.3/2018-07-26/bin/darwin/amd64/aws-iam-authenticator

Windows: https://amazon-eks.s3-us-west-2.amazonaws.com/1.10.3/2018-07-26/bin/windows/amd64/aws-iam-authenticator.exe

Download kubectl from [here](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

Copy this file to ~/.kube/config. 
If you already have a config file, make a new file ~/.kube/config-eks

```
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: <CERT>
    server: <URL>
  name: eks
contexts:
- context:
    cluster: eks
    namespace: petstore
    user: aws
  name: aws
current-context: aws
kind: Config
preferences: {}
users:
- name: aws
  user:
    exec:
      apiVersion: client.authentication.k8s.io/v1alpha1
      args:
      - token
      - -i
      - <EKS-CLUSTER>
      command: <PATH-TO-IAM>
      env: null


```

Try out these commands

```
kubectl get all

```


### Exercise 5



### Exercise 6


### Exercise 7








