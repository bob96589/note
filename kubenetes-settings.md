# Kubenetes settings

install

```text
# install 1
https://cloud.google.com/sdk/downloads?hl=zh-TW#linux
 
sudo tee -a /etc/yum.repos.d/google-cloud-sdk.repo << EOM
[google-cloud-sdk]
name=Google Cloud SDK
baseurl=https://packages.cloud.google.com/yum/repos/cloud-sdk-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
       https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOM

yum install google-cloud-sdk
gcloud init
yum install kubectl

gcloud container clusters create [cluster-name] --num-nodes 1
```

```text
# install 2
# https://cloud.google.com/sdk/downloads#interactive
curl https://sdk.cloud.google.com | bash
exec -l $SHELL
gcloud init
gcloud components install kubectl
```

login

```text
gcloud auth login
gcloud config set project [project-name]
```

update your kubectl config file $HOME/.kube/config

```text
gcloud container clusters list
gcloud container clusters get-credentials [cluster-name] --zone asia-east1-b
```

list of available contexts

```text
kubectl config get-contexts -o=name
kubectl config use-context [context-name]
kubectl config set-context [context-name]
```

```text
 kubectl version
```

Create Service

```text
kubectl expose deployment polling-frontend polling-backend --type=LoadBalancer
```

centos

```text
export KUBECONFIG=~user/.kube/config
kubectl get pods
```

log

```text
kubectl get pods
kubectl logs [pod-name]
```

remove kubectl

```text
 # remove
 yum remove kubectl
 yum remove google-cloud-sdk
 rm -rf .kube 
```

kubectl command

```text
kubectl cluster-info
kubectl cluster-info dump
kubectl config get-clusters
kubectl config get-contexts
kubectl config current-context
kubectl config view
```

gcloud command

```text
# authenticated account
gcloud auth list
# set authenticated account
gcloud config set account [account]

# list the projects running on my account
gcloud projects list
# Switch to intended project
gcloud config set project [project-name]

# configurations list
gcloud config configurations list

gcloud auth list
gcloud config list
gcloud info 
```





