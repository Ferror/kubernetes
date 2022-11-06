init:
	git clone https://github.com/Sylius/Sylius-Standard.git app

build:
	docker build --tag sylius-php --target sylius_php_prod --platform linux/amd64 app/
	docker build --tag sylius-nginx --target sylius_nginx --platform linux/amd64 app/

deploy: build
	helm install sylius sylius/ --values sylius/values.yaml

delete:
	helm uninstall sylius

validate:
	helm lint sylius --values sylius/values.yaml
