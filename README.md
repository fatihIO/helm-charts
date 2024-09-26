## HELM CHARTS
- Charts in this repository are mostly used for testing docker, kubernetes, helm and argocd
- Charts are tested on docker-desktop

### demo-app-one
- Build container image for demo-app-one on local  
  https://github.com/fatihIO/demo-apps.git
- Deploy app to dev/prod namespaces with paramaters for dev/prod environments
  ```
  helm install demo-app-one-dev demo-app-one -f demo-app-one/env/dev.yaml --namespace dev --create-namespace
  helm install demo-app-one-prod demo-app-one -f demo-app-one/env/prod.yaml --namespace prod --create-namespace
  ```

- Check helm releases
  ```
  helm ls -A
  ```

- Check pods, deployments, services and their configurations
  ```
  kubectl get all -n dev
  kubectl get all -n dev
  kubectl describe pod <pod-name> -n <namespace>
  kubectl describe deploy <deployment-name> -n <namespace>
  kubectl describe svc <service-name> -n <namespace>
  ```

- Test application connection from browser  
  http://localhost:30080  
  http://localhost:30090

- Cleanup
  ```
  helm uninstall demo-app-one-dev -n dev
  helm uninstall demo-app-one-prod -n prod
  ```