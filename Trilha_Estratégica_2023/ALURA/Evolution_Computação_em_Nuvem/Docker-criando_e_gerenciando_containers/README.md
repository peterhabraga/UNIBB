## Configurando o WLS no Windows para execução de subsistema Linux
	
	https://learn.microsoft.com/en-us/windows/wsl/install

## Instalando o docker no Ubuntu
	
	https://docs.docker.com/engine/install/ubuntu/
	https://docs.docker.com/engine/install/linux-postinstall/
	
## Help do Docker Run

	docker run -help
	docker run --help  								// Lista de comandos do Docker
	docker run <imagem_container>  					// Executa um container com a imagem passada como parametro
	docker run -it <imagem_container> bash  		// Executa um container com a imagem passada como parametro, de forma iterativa já abre uma console bash
	docker run -d <imagem_container>        		// Executa o container em modo deamon (backgroud)
	docker run -d -p 8080:80 <imagem_container>     // Executa o container em modo deamon (backgroud), e expoe a porta 8080 como a porta 80 do container

## Listado Containers 

	docker ps
	docker ps -a 			// Listar todos os Containers em execução ou não
	docker container ls		// Semelhante ao docker ps
	docker container ls -a  // Listar todos os Containers em execução ou não
	
## Start / Stop de Containers

	docker start <container_name ou container_id>
	docker stop <container_name ou container_id>
	
## Abrindo interação com o container

	docker exec -it <container_id> bash
	
## Removendo o container

	docker rm <container_name / container_id> --force

## Verificando as Portas do container

	docker port <container_id>

## Consultado imagens e History de imagens

	docker images
	docker history <imagem_id>

## Fazendo Build de uma Imagem

	docker build -t peterhabraga/app-node:1.0 .

## Fazendo o push da imagem para o DockerHub

	docker push peterhabraga/app-node:1.0

## Persistindo dados com Bind Mount (flag -v)

	docker run -it -v /home/pedro/volume_docker:/app ubuntu bash 

## Persistindo dados com criação de Volume (Melhor pratica e recomendado pela documentação do Docker)

	docker run –mount type=bind,source=/home/diretorio,target=/app nginx
	docker run -it --mount type=bind,source=/home/pedro/volume_docker,target=/app ubuntu bash

## Gerenciando Volumes 
	
	docker volume ls
	docker volume create <nome_volume>  // O docker mapeia os volumes dentro de sua estrutura,
										   usando o apontamento /var/lib/docker/volumes
	docker run -it --mount source=meu-novo-volume,target=/app ubuntu bash   // Cria automaticamente 
																			   o volume e faz a associação

## Persistindo dados com TMPFS

