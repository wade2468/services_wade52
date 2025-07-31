# services

## 刪除所有 container

    docker rm -f $(docker ps -a -q)

# Swarm

## init

    docker swarm init

# 若發現本機已經是 Docker Swarm 的一部分（可能是 manager 或 worker node），所以你無法再次執行 docker swarm init。
# 重新建立 Swarm，然後重新初始化
docker swarm leave --force

## 初始化後，會出現一段訊息，讓 Node 加入 Swarm 集群

    docker swarm join --token SWMTKN-xxxx xxx.xxx.xxx.xx:2377

## 忘記 docker swarm join 以上指令怎麼辦?

	docker swarm join-token worker

## 部屬 Portainer 服務

	docker pull portainer/portainer-ce:2.0.1
	docker pull portainer/agent
	docker stack deploy -c portainer.yml por

## 打開 Portainer 服務
http://127.0.0.1:9000

## create-mysql-volume:
	docker volume create mysql

## remove-network
	docker network rm my_swarm_network

## create-network:
	docker network create --scope=swarm --driver=overlay my_swarm_network
	docker network create --scope=swarm --driver=overlay --attachable my_swarm_network

## deploy-mysql:
	docker stack deploy --with-registry-auth -c mysql.yml mysql

# 打開phpMyAdmin 服務:
http://127.0.0.1:8080/

## deploy-rabbitmq:
	docker stack deploy --with-registry-auth -c rabbitmq.yml rabbitmq

## 離開 docker swarm
	docker swarm leave --force

## deploy-crawler:
	DOCKER_IMAGE_VERSION=0.0.6 docker stack deploy --with-registry-auth -c docker-compose-worker-network-version-swarm.yml crawler

## 發送任務:
	DOCKER_IMAGE_VERSION=0.0.6 docker stack deploy --with-registry-auth -c docker-compose-producer-duplicate-network-version.yml crawler

## 部屬 API:
	DOCKER_IMAGE_VERSION=0.0.1 docker stack deploy --with-registry-auth -c docker-compose-api-network-version-swarm.yml api

# 檢查有哪些stack
docker stack ls

## rm stack
	docker stack rm airflow api crawler mysql rabbitmq

## ubuntu 安裝 docker

	sudo apt-get update
	sudo apt-get install docker.io -y

## 將你的帳號加入 docker group
	sudo usermod -aG docker $USER

## 登入 docker
	docker login -u wade52

# 在manager執行
docker swarm join-token worker

## upload_taiwan_stock_price_to_mysql
	DOCKER_IMAGE_VERSION=0.0.7 docker stack deploy --with-registry-auth -c docker-compose-upload_taiwan_stock_price_to_mysql.yml upload
	DOCKER_IMAGE_VERSION=0.0.9 docker stack deploy --with-registry-auth -c docker-compose-upload_taiwan_stock_price_to_mysql.yml upload

## 設定 linode hostname
	sudo hostname manager
	sudo hostname mysql
	sudo hostname rabbitmq
	sudo hostname airflow

## 啟動 redash
	docker stack deploy -c docker-compose-redash.yml redash

	