create:
	git clone https://github.com/Sylius/Sylius-Standard.git app

build:
	docker build --tag sylius-prod-php --target sylius_php_prod app/
	docker build --tag sylius-prod-nginx --target sylius_nginx app/
