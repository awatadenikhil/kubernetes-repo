# docker up and app deployment
-   docker-compose up -d python
-   kubectl apply -f .\example-app\configmaps\configmap.yaml
-   kubectl apply -f .\example-app\deployments\deployment.yaml
-   kubectl apply -f .\example-app\namespaces\example-app.yaml
-   kubectl apply -f .\example-app\secrets\secret.yaml
-   kubectl apply -f .\example-app\services\service.yaml
-   kubectl get pods -n=example-app
-   kubectl port-forward example-deploy-86f65bc64f-9m6vk 2001:80 -n=example-app
# docker down and app delete
-   docker-compose down 
-   kubectl delete -f .\example-app\configmaps\configmap.yaml
-   kubectl delete -f .\example-app\deployments\deployment.yaml
-   kubectl delete -f .\example-app\namespaces\example-app.yaml
-   kubectl delete -f .\example-app\secrets\secret.yaml
-   kubectl delete -f .\example-app\services\service.yaml

# Ingress

-   kubectl apply -f .\kubernetes\ingress\controller\nginx\namespace.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\configMap.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\tls-secret.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\custom-snippets.configmap.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\service-account.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\deployment.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\service.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\cluster-role.yaml
-   kubectl apply -f .\kubernetes\ingress\controller\nginx\cluster-role-binding.yaml

-   kubectl apply -f .\kubernetes\ingress\ingress-nginx-example.yaml

# Restart application
-   kubectl get deployment -n=example-app
-   kubectl rollout restart deployment example-deploy -n=example-app

# Urls
-   https://nick.test/v2/hello
-   https://nick.test/v1/hello
-   http://localhost:5003/
-   http://localhost:7000/
-   http://localhost:2000/web/home.html
-   http://localhost:2002/web/home.html

# Useful coomands
-   kubectl get deployment -n=example-app
-   kubectl delete deploy  example-deploy -n=example-app


# Delete Commands
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\namespace.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\configMap.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\tls-secret.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\custom-snippets.configmap.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\service-account.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\deployment.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\service.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\cluster-role.yaml
-   kubectl delete -f .\kubernetes\ingress\controller\nginx\cluster-role-binding.yaml

-   kubectl delete -f .\kubernetes\ingress\ingress-nginx-example.yaml