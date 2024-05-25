# Secret-MongoDB-Deployment


The file contains a statefulset for mongodb database.

It uses storage from aws ebs; for which Persistent Volume is created and mounted in the statefulset. For ebs storage we need to configure the `csi driver` for it.

The config map provided is used to configure the pods from the statefulset. And the secret is regulated through the `SecretProviderClass`. Please read more about it in the blog. The secret provided here to reference a snapshot of the secret, created through the SecretProvider class. The secrets are encoded in `base64`. To retrieve the secrets use the command, `echo secretname | base64 -d`.

The role and aws account number must be configured in the service account before using it in creating pods.



# Other essential resources 


## Aws cli2

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

## EKS cluster
Create your eks cluster from https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html


## Update context in EKS
aws eks update-kubeconfig --name EKS_CLUSTER_NAME --region ap-south-1