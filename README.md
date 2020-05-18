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
