# Team information

| Team Members        | Github Id            | NUID      |
| ------------------- |:--------------------:|:---------:|
| Suhas Pasricha      | suhas1602            | 001434745 |
| Puneet Tanwar       | puneetneu            | 001409671 |
| Cyril Sebastian     | cyrilsebastian1811   | 001448384 |
| Shubham Sharma      | shubh1646            | 001447366 |

# k8s

<!-- Deployment Setup -->
ansible-playbook deploy-app.yaml -i production --extra-vars="db_username=team db_password=Qwerty123 rds_endpoint=<rds_endpoint> dockerhub_username=cyrilsebastian1811 dockerhub_password=Onepiece181195@ dockerhub_email=sebastian.c@northeastern.edu ui_image=frontend api_image=backend"

<!-- Deployment Pull Down -->
kubectl delete namespace ui
kubectl delete namespace api


<!-- Infrastructure Setup -->
Make sure you have added helm chart repo. Verify by running "helm repo list". 
If you have not added the repo then run "helm repo add stable https://kubernetes-charts.storage.googleapis.com"

export KOPS_STATE_STORE=s3://k8.dev.cyril-sebastian.com
export KOPS_FEATURE_FLAGS=SpecOverrideFlag
export AWS_PROFILE=dev
export AWS_REGION=us-east-1
ansible-playbook setup-k8s-cluster.yaml -i production --extra-vars="k8s_version=1.15.7 m_node_size=t2.small c_node_size=t2.small zone=k8.dev.cyril-sebastian.com name=k8.dev.cyril-sebastian.com db_username=team db_password=Qwerty123"

<!-- Infrastructure Teardown -->
ansible-playbook teardown-k8s-cluster.yaml -i production --extra-vars="name=k8.dev.cyril-sebastian.com" -vvv