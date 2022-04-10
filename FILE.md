## Command based tasks
---
### **Task1: Requirements**
- Install KOPS

> `wget -O kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64`
>
> `chmod +x ./kops`
>
> `sudo mv ./kops /usr/local/bin/`

- Install GCloud

    Link for installation : <https://cloud.google.com/sdk/>

       Once you are done installing GCloud SDK, you must run gcloud init. This will configure your gcloud with your existing GCP project.

- Install kubectl

> `sudo apt-get update -y`
>
> `sudo apt-get install -y apt-transport-https ca-certificates curl`
>
> `sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg`
>
> `echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list`
>
> `sudo apt-get update -y`
>
> `sudo apt-get install -y kubectl`
>
> `kubectl version`

<p>&nbsp;</p>

### **Task2: Create VPC**

Here I am using subnet-mode as auto, and it will create a VPC ewith a subnet in every zone.

> `gcloud compute networks create <YOUR-VPC-NAME> --project=<YOUR-PROJECT-NAME> --subnet-mode=auto`

<p>&nbsp;</p>

### **Task3: Create a Bucket**

    Kops needs a State Store to hold the configuration of our cluster. In our case, it is Google Cloud Storage Buckets. So, let’s create one empty Bucket using the following:

> `gsutil mb gs://<YOUR-BUCKET-NAME>/`

    Now, since we are ready with the Bucket, we can populate it with our cluster’s State Store, i.e. Cluster object and InstanceGroup object.














