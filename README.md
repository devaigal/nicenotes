# NiceNotes #
Prototipo conceptual para diseño de persistencia para sistemas notas, wiki, tareas, etc. basado en ficheros del sistema local.

Se diseña un estándar para guardar notas, sus metadatos, ficheros adjuntos, etc. y por otra parte un prototipo conceptual de aplicación para utilizar esos datos guardados. 

El objetivo es validar si esta aplicación y otras futuras con distintas funcionalidades pueden hacer uso de la persistencia solo en base a lo guardado en el sistema de ficheros.

---

Para el prototipo, utilizamos scripts en python para editar nuevas notas guardadas en ficheros md en local.

Los scripts están basados en la utilidad https://github.com/janusnic/mkdocsadmin

## Mkadmin

Flask application written to manage content for the [mkdocs] static site generator.
The site serves as an admin page and uses simply HTML forms to edit the text which will be used by mkdocs to render your documentation site.

I built this to use mkdocs as a makeshift wiki originally but do plan on expanding this to manage multiple mkdocs sites.

### Requirements ###
Most recent version of Flask and mkdocs.

This was tested on CentOS 7 and Debian 8 running Python 3.4.3. As the main code is in Flask it should work with Python 2 but this is not guarenteed.

Son necesarios los siguientes paquetes para Python:

- flask
- pyyaml

`pip install flask,pyyaml`

### Installation ###
Simply clone this repository to a directory of your choice.

If running behind a full webserver you can simply proxy to http://127.0.0.1:5000/mkdadmin for a basic setup.

UWSGI and a systemd service can also be used if desired.



### Usage ###
The site can be used behind a full webserver or by simply running the script manually. By default it will listen on port 5000 for localhost only. This is configurable in the provided configuration script.

Once running simply navigate to the specified host and port followed by /mkdadmin to see the index page. 

*Note:* No authentication is provided by this script! It can be provided by any other means of your choosing such as BasicAuth with the web server. This means anyone with access to the URL will be able to edit your site content.

For both edit and new docs clicking the save button will automatically run the 'mkdocs build' command on the server and generate the documentation. This will be immediately visible on the page configured for your site.

### Limitations ###
Currently this manages only a single site and is configured within the mkadmconfig.py file. You can change this at anytime and simply reload the script to work with the new directory.

Very basic UI. Some pages such as the log will simply scroll to fit the content. Additionally this will happen with large numbers of files.

Subpages are not supported. Nesting pages is not yet implemented. For best results I recommend setting the readthedocs theme within your mkdocs configuration file.



### Ejecución en local con imagen docker

`docker run -v "$PWD:$PWD" -w "$PWD" -p5000:5000 --rm -it python-docker python3 mkdocsadmin.py`



[1]: http://www.mkdocs.org/ "mkdocs.org"