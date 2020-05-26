# Platform repository
## HW1
Create minicube cluster with two pods: web and frontend.
1. Web pod is created from docker file in web dir, and init-container busybix which  downloads [page](https://tinyurl.com/otus-k8s-intro) and puts the page in */app* dir.
2. Frontend is created from [repo](https://github.com/GoogleCloudPlatform/microservices-demo), for correct starting env section was added in manifest file.

## HW2
1. Create frontend Deployment and ReplicaSet manifests
2. Build paymentservice docker container, push it on docker.io
3. Create paymentservice Deployment manifest, create manifests for blue-green and reverse deployments
4. Add readinessProbe to frontend-deployment.yaml
5. Create node-exporter DaemonSet manifest and edited it to monitor master nodes

## HW3
1. In first task:
  1. Create service_account bob
  2. Add cluster_admin rights to bob
  3. Create service_account dave
2. In second task:
  1. Create namespace prometheus
  2. Create service_account carol in namespace prometheus
  3. Give rights to get, list, watch to all service_accounts in namespace prometheus
3. In third task:
  1. Create namespace dev
  2. Create service_account jane in namespace dev
  3. Give admin role in namespace dev to jane
  4. Create service_account ken in namespace dev
  5. Give view role in namespace dev to ken

## HW4
1. Create manifest Service with ClusterIP in web-svc-cip.yaml
2. Install MetalLB, create manifest which configures MetalLB in netallb-config.yaml, create manifest Service with LoadBalancer in web-svc-lb.yaml
3. Install ingress controller ingress-nginx, create manifest for ingress-nginx in nginx-lb.yaml, create manifest for web service in web-svc-headless.yaml, create ingress rules in web-ingress.yaml

## HW5
1. Create manifest StatefulSet with MinIO in minio-statefulset.yaml, create manifest Headkess Service MinIO in minio-headless-service.yaml
2. Create manifest with secrets for MinIO StatefulSet
