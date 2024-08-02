## labs-docker-dev

## 1.1 Descarga la imagen oficial de Ubuntu

 @JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker pull ubuntu
 Using default tag: latest
 latest: Pulling from library/ubuntu
 9c704ecd0c69: Pull complete 
 Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
 Status: Downloaded newer image for ubuntu:latest
 docker.io/library/ubuntu:latest



## 1.2. Descarga una versión específica de Python

 $ docker pull python:3.9
 3.9: Pulling from library/python
 ca4e5d672725: Pull complete 
 30b93c12a9c9: Pull complete 
 10d643a5fa82: Pull complete 
 d6dc1019d793: Pull complete 
 c387064957b7: Pull complete 
 26766ebde481: Pull complete 
 8a42d17fd0e2: Pull complete 
 79eda865cc8a: Pull complete 
 Digest: ## sha256:fea84f3a3b72c41efe7fc3b07ae209c6856b852b942c05fa88b747b74f70e711
 Status: Downloaded newer image for python:3.9
 docker.io/library/python:3.9


## 2.1. Ejecuta un contenedor de Ubuntu en modo interactivo:

 $ docker run -it ubuntu bash
 root@bd76bff4daf3:/# exit


## 2.2. Ejecuta un servidor web Apache en segundo plano, mapeando el puerto 8000 del host al puerto 80 del contenedor:

 @JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker pull httpd
 Using default tag: latest
 latest: Pulling from library/httpd
 efc2b5ad9eec: Already exists 
 fce1785eb819: Pull complete 
 4f4fb700ef54: Pull complete 
 f214daa0692f: Pull complete 
 05383fd8b2b3: Pull complete 
 88ad12232aa1: Pull complete 
 Digest: sha256:932ac36fabe1d2103ed3edbe66224ed2afe0041b317bcdb6f5d9be63594f0030
 Status: Downloaded newer image for httpd:latest
 docker.io/library/httpd:latest
 @JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker run -d -p 8000:80 httpd
 fb1f2c426da9dbeb8458675370cecd2871b6584b7596335aba86635f99e87838

## 3.1. Elimina el contenedor de Ubuntu que creaste en el ejercicio 2.1

 docker ps -a
 CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                     PORTS                                           NAMES
 fb1f2c426da9   httpd     "httpd-foreground"       3 minutes ago    Up 3 minutes               0.0.0.0:8000->80/tcp, :::8000->80/tcp           vibrant_mcclintock
 bd76bff4daf3   ubuntu    "bash"                   15 minutes ago   Exited (0) 8 minutes ago                                                   pedantic_goodall
 6d009cadaad6   nginx     "/docker-entrypoint.…"   16 minutes ago   Up 16 minutes              80/tcp, 0.0.0.0:8001->81/tcp, :::8001->81/tcp   cool_swanson
 a7c88c067d49   nginx     "/docker-entrypoint.…"   16 minutes ago   Created                                                                    great_chaplygin
 3b8973a0da93   nginx     "/docker-entrypoint.…"   17 minutes ago   Created                                                                    eloquent_mclean
 206f84881faa   nginx     "/docker-entrypoint.…"   17 minutes ago   Up 17 minutes              0.0.0.0:8080->80/tcp, :::8080->80/tcp           vibrant_northcutt
 @JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker rm bd76bff4daf3
 bd76bff4daf3


 ## 3.2. Elimina todos los contenedores detenidos

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker container prune -f
Deleted Containers:
a7c88c067d49b8a94589ab7026f6a085ab9f4745b68b9570c5281964c8649c82
3b8973a0da936642698f53bc4214d5d1e41318c157451c72cba3e1e54fce69f6

Total reclaimed space: 0B




