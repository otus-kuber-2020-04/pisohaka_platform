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

## HW6
1. Зарегистрировался в GCP
2. Запустил k8s кластер в GCP
3. Установил Helm3
4. Установил и настроил nginx-ingress, cert-manager, chartmuseum, harbor
5. Создал helm-chart для hipster-shop
6. Вынес frontend в отдельный helm-chart, добавил его к зависимостям hipster-shop
7. Создал helm-secret
8. Вынес сервисы paymentservice и shippingservice для использования в kubecfg
9. Создал service.jsonnet для генерации манифестов для paymentservice и shippingservice
10. Вынес сервис recommendationservice для использования в kustomize
11. Настроил kustomize для окружений dev и prod



Запустили кластер, установили helm
Установили nginx-ingress, используя helm-3. Версия 1.11.1 не встала. Номер версии убрал
Установили CRD для cert-manager, согласно докоментации, версии v0.15.1
Установили cert-manager
Дополнительно установили Issuer для тестирования - test-resources.yaml
Проверили, что все ок.
Создали Basic ACME Issuer - letsencryp-acme.yml - установил production сервер
Модифицировал данные в volume.yaml для chartmuseum согласно описанию https://cert-manager.io/docs/usage/ingress/ и установил, сертификат подхватился.
Работа с chartmuseum:
helm repo add chartmuseum https://chartmuseum.35.238.80.184.nip.io
для примера взял чарт cert-manager/
helm plugin install https://github.com/chartmuseum/helm-push.git
Включил api в values
helm push cert-manager/ chartmuseum
далее для установки helm install chartmuseum/cert-manager
Harbor:
взял values.yaml c гитхаба
отключил notary
добавил домен для core, подключил cert-manager
уставновил harbor
hipster-shop:
Скачал all-hipster-shop.yaml
Выпилил deployment, service, создал ingress для frontend
Шаблонизировал, создал values.yaml
Без шаблонизации выпилил redis, подключил как dependencies
работу с secrets пропустил
Положил в харбор hipster-shop/, frontend/, redis/
kubecfg
Скачал локально kube.libsonnet - поменял версию api а deployment на "apps/v1"
восстановил работу сервисов
kustomize
вынес productcatalogservice
kubectl apply -k kubernetes-templating/kustomize/overrides/hipster-shop -n hipster-shop # - вернул сервис обратно
