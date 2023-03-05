# Create Application
-   docker-compose -f .\example-app\docker-compose.yaml up
-   kubectl apply -f .\example-app\KubeFiles\namespaces\example-app.yaml
-   kubectl apply -f .\example-app\KubeFiles\configmaps\configmap.yaml
-   kubectl apply -f .\example-app\KubeFiles\deployments\deployment.yaml
-   kubectl apply -f .\example-app\KubeFiles\secrets\secret.yaml
-   kubectl apply -f .\example-app\KubeFiles\services\service.yaml
-   kubectl get pods -n=example-app
-   kubectl port-forward example-deploy-86f65bc64f-kddjc 2001:80 -n=example-app
-   kubectl logs example-deploy-86f65bc64f-9m6vk -n=example-app
# Enable Ingress
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\namespace.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\configMap.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\custom-snippets.configmap.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\service-account.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\deployment.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\service.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\cluster-role.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\cluster-role-binding.yaml
-   kubectl get pods -n=ingress-nginx

-   kubectl apply -f .\example-app\KubeFiles\ingress\ingress-nginx-example.yaml
-   kubectl apply -f .\example-app\KubeFiles\certificate\tls-secret.yaml

# Delete Application
-   docker-compose -f .\example-app\docker-compose.yaml down
-   kubectl delete -f .\example-app\KubeFiles\configmaps\configmap.yaml
-   kubectl delete -f .\example-app\KubeFiles\deployments\deployment.yaml
-   kubectl delete -f .\example-app\KubeFiles\secrets\secret.yaml
-   kubectl delete -f .\example-app\KubeFiles\services\service.yaml
-   kubectl delete -f .\example-app\KubeFiles\namespaces\example-app.yaml

# Delete Ingress
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\configMap.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\tls-secret.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\custom-snippets.configmap.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\service-account.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\deployment.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\service.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\cluster-role.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\cluster-role-binding.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\namespace.yaml

-   kubectl delete -f .\example-app\KubeFiles\ingress\ingress-nginx-example.yaml

# URLs
-   http://localhost:2000/web/home.html
-   http://localhost:2001/web/home.html
-   http://localhost:2002/web/home.html --need add loadBlancer as type in service
-   https://nikhil.test/v2/web/home.html

# URL Referances 
-   For $2 in ingress
    -   https://kubernetes.github.io/ingress-nginx/examples/rewrite/

# Steps to create application with ingress controller
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\namespace.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\configMap.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\custom-snippets.configmap.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\service-account.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\deployment.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\service.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\cluster-role.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\cluster-role-binding.yaml
-   docker-compose -f .\example-app\docker-compose.yaml up
-   kubectl apply -f .\example-app\KubeFiles\namespaces\example-app.yaml
-   kubectl apply -f .\example-app\KubeFiles\configmaps\configmap.yaml
-   kubectl apply -f .\example-app\KubeFiles\deployments\deployment.yaml
-   kubectl apply -f .\example-app\KubeFiles\secrets\secret.yaml
-   kubectl apply -f .\example-app\KubeFiles\services\service.yaml
-   kubectl apply -f .\example-app\KubeFiles\ingress\ingress-nginx-example.yaml
-   kubectl apply -f .\example-app\KubeFiles\certificate\tls-secret.yaml

# Azure
-   Container Registry: containerregistrywebapp
    -   Login Servier : containerregistrywebapp.azurecr.io
-   Resource Group : rg-kube-demo1
-   Kubernetes : kubewebservice
-   docker images
-   docker tag webfrontendappwithdocker:v1 containerregistrywebapp.azurecr.io/webfrontendappwithdocker:v1
-   # Push docker image  to Azure container 
    -   az login
    -   az account set --subscription "Visual Studio Professional Subscription"
    -   az acr login --name containerregistrywebapp
    -   docker push containerregistrywebapp.azurecr.io/webfrontendappwithdocker:v1
-   # Kubernetes in Azure
    -   kubectl config current-context
    -   az aks get-credentials --resource-group rg-kube-demo1 --name kubewebservice
    -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\mandatory-nginx.yaml
    -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\custom-headers.yaml
    -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\configmap.yaml
    -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\configmap-client-response.yaml
    -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\add-custom-headers.yaml
    -   kubectl get svc -n=ingress-nginx
    -   kubectl get pods -n=ingress-nginx
    -   ----------------------------------------
    -   kubectl apply -f .\example-app\KubeFiles\certificate\tls-secret.yaml
    -   kubectl apply -f .\example-app\KubeFiles\ingress-azure\ingress-nginx-example.yaml
-   # Steps to deploy in Azure    
    -   -- For Ingress
        -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\mandatory-nginx.yaml
        -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\custom-headers.yaml
        -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\configmap.yaml
        -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\configmap-client-response.yaml
        -   kubectl apply -f .\kubernetes\ingress\controller\nginx1\add-custom-headers.yaml
    -   --In docker
        -   docker-compose -f .\example-app\docker-compose.yaml up
        -   az login
        -   az account set --subscription "Visual Studio Professional Subscription"
        -   az acr login --name containerregistrywebapp
        -   docker push containerregistrywebapp.azurecr.io/webfrontendappwithdocker:v1
    -   --For app 
        -   kubectl apply -f .\example-app\KubeFiles\namespaces\example-app.yaml
        -   kubectl apply -f .\example-app\KubeFiles\configmaps\configmap.yaml
        -   kubectl apply -f .\example-app\KubeFiles\deployments\deployment-azure.yaml
        -   kubectl apply -f .\example-app\KubeFiles\secrets\secret.yaml
        -   kubectl apply -f .\example-app\KubeFiles\services\service.yaml
        -   kubectl get pods -n=example-app
        -   kubectl apply -f .\example-app\KubeFiles\ingress\ingress-nginx-example.yaml
        -   kubectl apply -f .\example-app\KubeFiles\certificate\tls-secret.yaml
    -   --Assgin IP address to domain
        -   kubectl get svc -n=ingress-nginx
        -   Get ip address and assign to Site.
# Assign public address to Site
-   kubectl get svc -n=ingress-nginx
-   https://www.thegeekdiary.com/how-to-map-static-ip-to-your-domain-with-godaddy-example/
-   Set Type "A" as 20.72.139.227 in DNS setting and wait for sometime.
-   Hit URL : https://nikhils.cloud/v2/web/home.html
# Azure Service Principle for Pipeline
-   Subscription ID : xxxx
-   Subscription Name: Visual Studio Professional Subscription
-   Service Principle ID(Client ID) : xxxx
-   Tenant ID : xxxx
-   Service Principle Secret(value) : xxxx
-   Service Principle SecretID(ID) : xxxxx
-   App Name : devops_app

# Certificates
-   Commands to create certificate
    -   go to folder certificate/
    -   C:\OpenSSL\openssl.exe req -x509 -sha256 -days 356 -nodes -newkey rsa:2048 -subj "/CN=nikhils.cloud/C=US/L=San Fransisco" -keyout rootCA.key -out rootCA.crt
-   Exe saved in folders
    -   SSLexe/openssl.exe
-   Encode code using https://www.base64encode.org/ of rootCA.key and rootCA.crt and replace in file tls-secret.yaml
-   Referances
    -   1 https://devopscube.com/configure-ingress-tls-kubernetes/




