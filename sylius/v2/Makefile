init:
	git clone https://github.com/Sylius/Sylius-Standard.git app

build:
	docker build --tag sylius-prod-php --target sylius_php_prod --platform linux/amd64 app/
	docker build --tag sylius-prod-nginx --target sylius_nginx --platform linux/amd64 app/

deploy:
	kubectl apply -f manifest/volume.yaml
	kubectl apply -f manifest/deployment-app.yaml
	kubectl apply -f manifest/deployment-mysql.yaml

delete:
	kubectl delete -f manifest/deployment-app.yaml
	kubectl delete -f manifest/deployment-mysql.yaml
	kubectl delete -f manifest/volume.yaml
