init:
	docker-compose up --build -d 
	make exec 

exec shell:
	docker exec -it magenta bash 

up:
	docker-compose up -d 
	make exec 

down:
	docker-compose down 

rebuild:
	docker stop magenta
	docker rmi -f ktapi-v2-app
	make init 