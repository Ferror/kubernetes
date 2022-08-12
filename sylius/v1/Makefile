init:
	git clone git@github.com:Ferror/sylius-standard-dockerized.git

deploy:
	mkdir -p /tmp/kubernetes/mysql
	docker build --tag sylius-prod:latest --platform linux/amd64 sylius-standard-dockerized/.
	kubectl apply -f volume.yaml
	kubectl apply -f deployment.yaml

delete:
	kubectl delete -f deployment.yaml
	kubectl delete -f volume.yaml

into:
	kubectl exec -it sylius-deployment-VERSION -- bash
