# Imagen docker para Python



Imagen docker para crear y ejecutar Python dentro de docker pero como si estuviera instalado en el sistema operativo.



## Construir imagen:

	docker build -t python-docker .

Dentro de requirements.txt incluir los módulos Python necesarios. Del tipo:
	Flask>=1.1.1,<1.2

Para instalar módulos puthon, incluir en el DockerFile los comandos necesarios:

	RUN apk add libxml2-dev libxslt-dev python-dev
	
	#If you’re on a debian-based system like ubuntu, you can instead use the following command:
	
	sudo apt-get install libxml2-dev libxslt-dev python-dev

## Probar módulos

Para entrar en la máquina y probar comandos o instalaciones (util al tener problemas en las instalaciones y para antes de automatizar en el Dockerfile):

	docker run -v "$PWD:$PWD" -w "$PWD"  --rm -it python-docker bash



## Referencias de uso



* python interactivo:

docker run -v "$PWD:$PWD" -w "$PWD"  --rm -it python-docker


* ejecución de fichero python

docker run -v "$PWD:$PWD" -w "$PWD"  --rm -it python-docker python3 myFile.py


* ejecución de una funcion dentro de un fichero python(modulo):

docker run -v "$PWD:$PWD" -w "$PWD"  --rm -it python-docker python3 -c 'from function-gcloud-noticias-opos import *; request=""; hello_world(request)'



## Alias para instalarlo en el SO

Crear alias para ejecutar python como comando del sistema:

```bash
alias python3='docker run -v "$PWD:$PWD" -w "$PWD"  --rm -it python-docker python3'
```



Una vez creado el alias podrás ejecutar el comando como si Python estuviera instalado en el sistema:

```bash
python3 test.py
```





## Referencias

https://pythonspeed.com/articles/official-python-docker-image/

https://hub.docker.com/_/python

