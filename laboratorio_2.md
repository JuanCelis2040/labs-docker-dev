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


## Ejercicio 4: Construir y ejecutar la imagen de Nginx

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 13.2s (6/6) FINISHED                            docker:default
 => [internal] load build definition from Dockerfile                   0.1s
 => => transferring dockerfile: 140B                                   0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest       0.0s
 => [internal] load .dockerignore                                      0.1s
 => => transferring context: 2B                                        0.0s
 => CACHED [1/2] FROM docker.io/library/ubuntu:latest                  0.0s
 => [2/2] RUN apt-get update && apt-get install -y nginx              11.8s
 => exporting to image                                                 0.9s 
 => => exporting layers                                                0.8s 
 => => writing image sha256:68bd95e7bdce117b873548ccdfce9bd25623c06f0  0.0s 
 => => naming to docker.io/library/my-nginx:latest                     0.0s 
@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker run -d -p 80:80 my-nginx:latest                                                            
24424617c94cd99f830ed267b2304d49bc414a4bf2b3725d22ee3737afd73f3f
@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ 

## Ejercicio 5: Modificar el Dockerfile de Nginx para exponer el puerto 80
@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ nano Dockerfile

## Archivo Dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y nginx
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

@JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ docker build -t my-nginx:latest .
[+] Building 0.6s (6/6) FINISHED                             docker:default
 => [internal] load build definition from Dockerfile                   0.1s
 => => transferring dockerfile: 150B                                   0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest       0.0s
 => [internal] load .dockerignore                                      0.1s
 => => transferring context: 2B                                        0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                         0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y nginx        0.0s
 => exporting to image                                                 0.1s
 => => exporting layers                                                0.0s
 => => writing image sha256:eb43d236e2d85af13d3a5c19c6ed4277854aaf6db  0.0s
 => => naming to docker.io/library/my-nginx:latest                     0.0s

 ## Tema 2
 # Ejercicio 1: Copiar un archivo HTML local a una imagen de Nginx

 @JuanCelis2040 ➜ /workspaces/labs-docker-dev (main) $ nano Dockerfile
 # Archivo Docerkfile
 FROM nginx:latest
COPY index.html /usr/share/nginx/html/


