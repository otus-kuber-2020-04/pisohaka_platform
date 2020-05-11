# pisohaka_platform
pisohaka Platform repository
Create minicube cluster with two pods: web and frontend.
1. Web pod is created from docker file in web dir, and init-container busybix which  downloads [page](https://tinyurl.com/otus-k8s-intro) and puts the page in */app* dir.
2. Frontend is created from [repo](https://github.com/GoogleCloudPlatform/microservices-demo), for correct starting env section was added in manifest file.
