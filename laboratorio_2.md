## Ejercicio 1: Crear un Dockerfile simple con Ubuntu y actualizar paquetes

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ pwd
/workspaces/labs-docker-dev

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ ls
Docekrfile  laboratorio_1.md  laboratorio_2.md

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ touch Dockerfile

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ nano Dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get upgrade -y


@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntut .
[+] Building 10.3s (6/6) FINISHED                            docker:default
 => [internal] load build definition from Dockerfile                   0.1s
 => => transferring dockerfile: 98B                                    0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest       0.0s
 => [internal] load .dockerignore                                      0.1s
 => => transferring context: 2B                                        0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                         0.1s
 => [2/2] RUN apt-get update && apt-get upgrade -y                     8.6s
 => exporting to image                                                 1.0s 
 => => exporting layers                                                0.9s 
 => => writing image sha256:183230cd983f1db45ff88b3f476bf14e9abcf96a2  0.0s 
 => => naming to docker.io/library/ubuntut                             0.0s 

## Archivo Dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get upgrade -y

 ## Ejercicio 2: Construir la imagen del ejercicio 1

 @JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker build -t ubuntut .
[+] Building 10.3s (6/6) FINISHED                            docker:default
 => [internal] load build definition from Dockerfile                   0.1s
 => => transferring dockerfile: 98B                                    0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest       0.0s
 => [internal] load .dockerignore                                      0.1s
 => => transferring context: 2B                                        0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                         0.1s
 => [2/2] RUN apt-get update && apt-get upgrade -y                     8.6s
 => exporting to image                                                 1.0s 
 => => exporting layers                                                0.9s 
 => => writing image sha256:183230cd983f1db45ff88b3f476bf14e9abcf96a2  0.0s 
 => => naming to docker.io/library/ubuntut                             0.0s 

 ## Archivo Dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y nginx
CMD ["nginx", "-g", "daemon off;"]


