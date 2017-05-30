![Netflax Calendar logo](http://i.imgur.com/E4wKn4j.png)

Si siempre te pierdes tus series favoritas en Netflix, utilizando ***Netflax Calendar*** se actualizará tu calendario de Google cada vez que la cuenta ***[@gallonetflix](https://twitter.com/gallonetflix)*** tuitee la fecha de salida de una nueva serie o película en dicha plataforma.

## Participantes

- [Manuel Rodríguez-Sanchez Guerra](https://github.com/manuelrdsg)
- [Luis Gonzaga Rozo Bueno](https://github.com/luisrozo)

## Método de uso

Pare ejecutar la aplicación es necesario tener instaladas las siguientes librerías Python: *Celery, Dropbox, Tweepy, Google Calendar*, además de *RabbitMQ* u otro broker. El programa corre sobre **Python3**.

Antes de esto, además, hay que rellenar el fichero *credentials.py* con los *tokens* de acceso a la aplicación tanto en *Google* como en *Dropbox*. Para más información de cómo obtener estos tokens, accede a los siguientes tutoriales. 
* [*Dropbox*](https://blogs.dropbox.com/developers/2014/05/generate-an-access-token-for-your-own-account/)
* [*Google Calendar: Step 1*](https://developers.google.com/google-apps/calendar/quickstart/python)

Una vez hecho esto, realizar los siguientes pasos:

1. Ejecutar rabbitmq, para esto lanzaremos el siguiente comando
	```
	sudo rabbitmq-server
    ```
    
2. Lanzar el worker de celery, para esto, estando situados en la carpeta raiz del proyecto, ejecutaremos el siguiente comando
	```
	celery -A server worker --loglevel=info
    ```

3. Lanzar el streaming de Twitter, para esto ejecutaremos el fichero *twitter.py*
	```
	python3 twitter.py
    ```
    
4. Ejecutar el programa que nos actualice el calendario una vez que se hayan publicado tuits nuevos
	```
	python3 calen.py
    ```
