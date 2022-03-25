apply:
	#kubectl apply -f ingress.yaml
	kubectl apply -f configmap.yaml
	kubectl apply -f secret.yaml
	kubectl apply -f mongodb.yaml
	sleep 5
	kubectl apply -f mongo-express.yaml
ingress:
	kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.1/deploy/static/provider/cloud/deploy.yaml
