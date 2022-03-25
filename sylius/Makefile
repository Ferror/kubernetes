time := date

date:
	date -u +"%Y-%m-%dT%H:%M:%SZ"

deploy1:
	@$(time)

init:
	git clone git@github.com:Ferror/sylius-standard-dockerized.git

deploy:
	docker build --tag sylius-prod:latest --platform linux/amd64 sylius-standard-dockerized/.
	kubectl apply -f deployment.yaml

into:
	kubectl exec -it sylius-deployment -- bash
