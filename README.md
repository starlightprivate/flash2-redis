# flash2-redis

### How to deploy

0) Run build in codeship CI

1) create blank disk in ui or cli of GCP. 50Gb will be enough. The disk must be name redis-disk
https://cloud.google.com/sdk/gcloud/reference/compute/disks/create

2) Replace latest tag by branch_name.commit_id value in the deploy/kubernetes/redis_deployment.yml file. Also change image repo name (flash2-staging by default). Example:
```
      - image: gcr.io/flash2-staging/redis:featureredis-pass.595830c69e171f5d7499478fac5e27ca03c408c9
```

3) kubectl create -f deploy/kubernetes/redis_volume.yml

4) kubectl create -f deploy/kubernetes/redis_deployment.yml

5) kubectl expose deployment redis --name=redis --port=6379 --type="NodePort"
