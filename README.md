# k8s

To setup a cluster run the following command:

KOPS_STATE_STORE=s3://k8s.dev.suhaspasricha.com AWS_PROFILE=dev ansible-playbook setup-k8s-cluster.yaml -i production

Here KOPS_STATE_STORE is S3 bucket where cluster config is stored. AWS_PROFILE is setup using 
"aws configure --profile dev"

To add parameters from command line pass the extra-vars flag like below:

KOPS_STATE_STORE=s3://k8s.dev.suhaspasricha.com AWS_PROFILE=dev ansible-playbook setup-k8s-cluster.yaml -i production --extra-vars="k8s_version=1.17"

The cluster will be setup as High Availability or not depending on the availability zones of the region your AWS profile is 
configured in.

To teardown the cluster run:

KOPS_STATE_STORE=s3://k8s.dev.suhaspasricha.com AWS_PROFILE=dev ansible-playbook teardown-k8s-cluster.yaml -i production
 
