# To Do App - Kubernetes Configuration Files

These are the configuration files to deploy the fullstack To Do App in Kubernetes with Minikube.

The code for the To Do App is located here:

- https://github.com/xbmac2/nology-todo-app-project-xandra
- https://github.com/xbmac2/nology-todo-backend-xandra

## Requirements

- minikube: https://minikube.sigs.k8s.io/docs/start/
- kubectl (Kubernetes command line tool): https://kubernetes.io/docs/reference/kubectl/

## How To Use

1. `minikube start`

2. Apply each file in this order:\
   `kubectl apply -f mysql-configMap.yaml`\
   `kubectl apply -f mysql-secrets.yaml`\
   `kubectl apply -f mysql-pv.yaml`\
   `kubectl apply -f db-deployment.yaml`\
   `kubectl apply -f springboot-deployment.yaml`\
   `kubectl apply -f react-app-deployment.yaml`

3. Check that the pods are RUNNING and READY 1/1\
   `kubectl get pods`

4. To access the deployments in your browser, you need to port forward the services for springboot and react-app.
   **You need to keep these running in separate terminals while you access your browser:**\
    `kubectl port-forward service/springboot-todo-service 8080:8080`\
    `kubectl port-forward service/react-app-service 5173:5173`

5. Open localhost:5173 in your browser to see and use the app.

## Notes

These files reference images hosted on my Docker Hub. These images were built from my code at these repos:

- https://github.com/xbmac2/nology-todo-app-project-xandra
- https://github.com/xbmac2/nology-todo-backend-xandra

In the backend, the application.yaml file has been configured to accept the environment variables in the spingboot-deployment.yaml file in this repo.
