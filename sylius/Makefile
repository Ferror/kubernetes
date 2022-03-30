init:
	git clone git@github.com:Ferror/sylius-standard-dockerized.git

deploy:
	docker build --tag sylius-prod:latest sylius-standard-dockerized/.
	kubectl apply -f deployment.yaml

delete:
	kubectl delete -f deployment.yaml

into:
	kubectl exec -it sylius-deployment-VERSION -- bash
