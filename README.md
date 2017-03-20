# flash2-redis

### How to deploy

0) Run build in codeship CI

1) create blank disk in ui or cli of GCP. 50Gb will be enough. The disk must be name redis-disk
https://cloud.google.com/sdk/gcloud/reference/compute/disks/create

2) kubectl create -f deploy/kubernetes/redis_volume.yml

3) kubectl create -f deploy/kubernetes/redis_deployment.yml

4) kubectl expose deployment redis --name=redis --port=6379 --type="NodePort"
