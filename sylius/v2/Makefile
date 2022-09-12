init:
	git clone https://github.com/Sylius/Sylius-Standard.git app

build:
	docker build --tag sylius-prod-php --target sylius_php_prod --platform linux/amd64 app/
	docker build --tag sylius-prod-nginx --target sylius_nginx --platform linux/amd64 app/

deploy:
	kubectl apply -f volume.yaml
	kubectl apply -f deployment-app.yaml
	kubectl apply -f deployment-mysql.yaml

delete:
	kubectl delete -f deployment-app.yaml
	kubectl delete -f deployment-mysql.yaml
	kubectl delete -f volume.yaml
