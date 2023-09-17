 cd .\auth-api\
 docker build -t arminferhat93/kub-demo-auth-1 .
 docker push arminferhat93/kub-demo-auth-1
 cd ..
cd .\users-api\
 docker build -t arminferhat93/kub-demo-users-1 .
 docker push arminferhat93/kub-demo-users-1
 
MUST RUN
minikube service users-service

kubectl get pods/services/deployments
kubectl apply -f="users-service.yaml" -f="users-deployment.yaml"
kubectl apply -f="auth-service.yaml" -f="auth-deployment.yaml"
kubectl delete -f="auth-service.yaml" -f="auth-deployment.yaml"
kubectl apply -f="tasks-service.yaml" -f="tasks-deployment.yaml"
kubectl apply -f="frontend-service.yaml" -f="frontend-deployment.yaml"
minikube service tasks-service

Frontend app

docker run -p 80:80 --rm arminferhat93/kub-demo-frontend-1
kubectl service frontend-service