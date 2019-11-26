# IBM-Kubernetes-Service-Laboratorio de despligue de una imagen de Tomcat


## Índice

* Creación de clúster desde IBM Cloud
* Sección de contenedores en la plataforma de IBM Cloud.
* Conexión al clúster de Kubernetes desde un entorno Ubuntu.
* Despliegue de imagen de Apache Tomcat.

En la siguiente guía puede observar cómo se realiza la conexión al clúster de Kubernetes y posteriormente el despliegue de Apache Tomcat.
Antes de conectarnos al clúster vamos a ver cómo crear uno desde la plataforma de IBM Cloud.

## Creación de clúster desde IBM Cloud

Para realizar la creación del clúster, se dirige a la página principal de IBM Cloud https://www.ibm.com/cloud, una vez allí va a iniciar sesión con su cuenta de IBM Cloud.

<img width="650" alt="1" src="https://user-images.githubusercontent.com/50923637/69644366-90aeb780-1032-11ea-88e9-47532a2b9469.png">

Una vez le haya dado click en log-in, va a aparecer la siguiente pantalla.

<img width="650" alt="2" src="https://user-images.githubusercontent.com/50923637/69644599-dd928e00-1032-11ea-86f2-da1af7377614.png">

Luego de la autenticación de usuario y contraseña, se va a ver la página inicial de IBM Cloud donde puede verificar los servicios y aplicaciones que tiene creados actualmente, Una vez allí se va a dirigir al apartado que dice “Catalogo”.

<img width="650" alt="3" src="https://user-images.githubusercontent.com/50923637/69644822-29453780-1033-11ea-85e7-fa7c2e2a7b15.png">

En el apartado de catálogo puede observar todos y cada uno de los servicios que ofrece IBM dentro de su nube, y allí se va a dirigir a la sección de contenedores.

<img width="650" alt="4" src="https://user-images.githubusercontent.com/50923637/69644928-54c82200-1033-11ea-9927-f7db66fb3ea2.png">

Y allí es donde va a proceder a crear el clúster, para eso seleccionamos el servicio que dice IBM Cloud Kubernetes Services.

<img width="650" alt="5" src="https://user-images.githubusercontent.com/50923637/69645039-7de8b280-1033-11ea-9312-47bed99aa7b5.png">

Una vez ingresemos al servicio de IBM Cloud Kubernetes Service (IKS), la pagina muestra las características y varios links de ayuda del servicio donde se puede encontrar por ejemplo la documentación correspondiente, luego vamos a hacer click en el banner que dice “Create”. 

<img width="650" alt="6" src="https://user-images.githubusercontent.com/50923637/69645170-bb4d4000-1033-11ea-9fe0-2df0bae2f54a.png">

A partir de ese momento se visualiza la página donde podemos crear el clúster con la configuración que más se adapte a la necesidad, por ejemplo: 

-	En la siguiente pantalla podemos ver y seleccionar las opciones que ofrece el servicio como el grupo de recursos, el tipo de clúster.

<img width="650" alt="7" src="https://user-images.githubusercontent.com/50923637/69645281-edf73880-1033-11ea-96dc-d30415d8a98e.png">

-	Luego vamos a ver la locación donde se puede aprovisionar el clúster según la oferta de IBM:

<img width="650" alt="7" src="https://user-images.githubusercontent.com/50923637/69646790-6b23ad00-1036-11ea-8e5c-f0bb032fe3e9.png">

-	Después de elegir la ubicación, hay que seleccionar la versión de Kubernetes que se quiera utilizar para el clúster que se está creando.

<img width="650" alt="7" src="https://user-images.githubusercontent.com/50923637/69646609-13854180-1036-11ea-8037-4648749792c7.png">

-	Ahora hay que seleccionar el aislamiento de hardware con servidores virtuales públicos y dedicados y por otra parte baremetal, según se ajuste a las necesidades del clúster que se esté creando.

<img width="650" alt="10" src="https://user-images.githubusercontent.com/50923637/69646948-a7570d80-1036-11ea-9e74-0c5c415613e5.png">

-	Una vez se haya seleccionado la capacidad de hardware requerida, muestra la opción de encriptar o no el disco local, el número de worker nodes y para finalizar hay que seleccionar el nombre deseado al clúster y dar click en el botón de “Create Cluster”.

<img width="650" alt="11" src="https://user-images.githubusercontent.com/50923637/69647034-ce154400-1036-11ea-90c8-630ab0032f72.png">

Una vez se haya creado el clúster hay que esperar alrededor de 15 minutos para que se aprovisione en la ubicación elegida y con las configuraciones elegidas para el clúster que creamos.

## Sección de contenedores en la plataforma de IBM Cloud.

Una vez se haya creado y aprovisionado el clúster nos va a al a sección de contenedores de IBM Cloud donde podemos observar algunas características y propiedades del clúster creado anteriormente.

-	Overview: En este apartado se puede crear varios clústeres 

<img width="650" alt="12" src="https://user-images.githubusercontent.com/50923637/69647186-0ae13b00-1037-11ea-8bd7-512a2fe23907.png">

-	Clusters: En la sección se revisa los clústeres que tenemos creados y varias de sus propiedades al ingresar en cada uno de ellos, como por ejemplo el acceso al clúster seleccionado que se va a tratar en este manual, el estado, la fecha de creación, los worker nodes y los worker pools.

<img width="650" alt="13" src="https://user-images.githubusercontent.com/50923637/69647286-33693500-1037-11ea-86ae-11a0a904d24d.png">

-	Registry: En el apartado de registry se puede observar los repositorios que tenemos, los namespaces y las imágenes que tenemos en los clústeres que tiene creados.

<img width="650" alt="14" src="https://user-images.githubusercontent.com/50923637/69647378-5eec1f80-1037-11ea-9911-d2177c1e546b.png">

-	Vulnerability Advisor: En este entorno podemos añadir excepciones y configurar diferentes políticas según lo deseado

<img width="650" alt="15" src="https://user-images.githubusercontent.com/50923637/69647476-8d69fa80-1037-11ea-85bb-7cd204e20f17.png">

-	Solutions: Desde el apartado de soluciones podemos desplegar servicios o soluciones desde Helm Charts que lo cual permite realizar despliegues rápidos para el IKS y adicionalmente el catálogo de soluciones que se pueden desplegar desde allí.

<img width="650" alt="16" src="https://user-images.githubusercontent.com/50923637/69647552-b5f1f480-1037-11ea-97ed-e83ed443b0c1.png">

Y básicamente en esta sección de contenedores es donde podemos jugar con todas las características y agregados que ofrece IBM para este servicio.

## Conexión al clúster de Kubernetes desde un entorno Ubuntu.

Iniciar el servicio de Kubernetes desde el terminal de Linux: ```ibmcloud cs init```.

<img width="650" alt="24" src="https://user-images.githubusercontent.com/50923637/69648403-45e46e00-1039-11ea-8b85-04f05bf28075.png">

Loguearse y hacer target a la cuenta: ```ibmcloud login --sso``` abrir la cuenta de IBM Cloud en el navegador; copiar y pegar el código que nos arroja la página luego de esto seleccionar la cuenta deseada, como se ve a continuación: 

<img width="650" alt="25" src="https://user-images.githubusercontent.com/50923637/69648508-73311c00-1039-11ea-8185-1cffcef80ed6.png">

Una vez ejecute el comando, el terminal le preguntara si quiere abrir el link para obtener el código que se usara una vez, tendrá que digitar la tecla “Y” para que así abra el navegador y pueda acceder a su cuenta de IBM Cloud como lo puede ver:

<img width="650" alt="26" src="https://user-images.githubusercontent.com/50923637/69648641-b55a5d80-1039-11ea-9228-a8748aaaa622.png">

<img width="650" alt="27" src="https://user-images.githubusercontent.com/50923637/69648689-c7d49700-1039-11ea-8daf-014f1522fe3f.png">

<img width="650" alt="28" src="https://user-images.githubusercontent.com/50923637/69648697-ca36f100-1039-11ea-9889-20408c4f7b18.png">

Una vez obtenga el código de un solo uso, lo tiene que copiar y pegar en el termina para que le dé a elegir la cuenta con la cual desea iniciar sesión.

<img width="650" alt="29" src="https://user-images.githubusercontent.com/50923637/69648789-f6eb0880-1039-11ea-9e08-58a88969406c.png">

Una vez ingrese a su cuenta debe conectarse a la región donde se encuentra el clúster con el siguiente comando: ```ibmcloud cs region-set us-east```.

<img width="650" alt="30" src="https://user-images.githubusercontent.com/50923637/69648791-f8b4cc00-1039-11ea-8690-17099de07f70.png">

Luego de esto tiene que obtener la configuración del clúster con el siguiente código: ```ibmcloud cs cluster-config <nombre del cluster>```.

<img width="650" alt="31" src="https://user-images.githubusercontent.com/50923637/69648957-47626600-103a-11ea-961c-ae67fb200188.png">

Para exportar la configuración del clúster para así poder habilitar y usar la línea de comandos de Kubernetes tiene que copiar la salida que nos generó cuando ingresamos a la configuración del clúster de la siguiente manera:

<img width="650" alt="32" src="https://user-images.githubusercontent.com/50923637/69649128-8e505b80-103a-11ea-876c-b1a877fe6ea5.png">

Una vez habilitado la línea de comandos de Kubernetes, podemos revisar las propiedades de nuestro clúster desde la consola como lo vamos a ver con los siguientes comandos: 

•	kubectl get pods: Nos permite revisar los pods que tenemos creados en el clúster.

<img width="650" alt="33" src="https://user-images.githubusercontent.com/50923637/69649181-a88a3980-103a-11ea-9be6-704bc47f6b6f.png">

•	kubectl get nodes: Nos permite revisar los nodos que tenemos actualmente en nuestro clúster e información varia de los mismos.

<img width="650" alt="34" src="https://user-images.githubusercontent.com/50923637/69649415-00c13b80-103b-11ea-8e46-367155511cce.png">

Una vez esté conectado al clúster y habilitada la línea de comandos de Kubernetes, vamos a ver cómo realizar el despliegue de una imagen de Apache Tomcat.

## Despliegue de Apache Tomcat

Traemos tomcat desde el repositorio oficial de docker con el siguiente comando: ```sudo docker pull tomcat``` y esperamos a que se complete la descarga de la última versión.

<img width="650" alt="1" src="https://user-images.githubusercontent.com/50923637/69654077-33226700-1042-11ea-90d9-c6d717f36e2f.png">

Una vez completa la descarga podemos revisar que imágenes hemos descargado a nuestro clúster con el siguiente comando: ```docker images```.

<img width="650" alt="2" src="https://user-images.githubusercontent.com/50923637/69654146-4f260880-1042-11ea-9469-7d6d6c4898f1.png">

Una vez hallamos verificado que la imagen se encuentra descargada es necesario realizarle el push a la imagen de Tomcat para poder subirla al clúster con el siguiente comando: ```docker push registry.ng.bluemix.net/<nombre del cluster>/tomcat```.

<img width="650" alt="3" src="https://user-images.githubusercontent.com/50923637/69654218-682eb980-1042-11ea-8aea-fcb9d9ea66ff.png">

En este caso nos indica que la imagen ya está en el clúster, en caso de que no solo hay que esperar a que culmine el proceso y podemos verificar que la imagen ya esta subida en la plataforma de contenedores de IBM Cloud en la sección de “Registry”.

<img width="650" alt="4" src="https://user-images.githubusercontent.com/50923637/69654346-9f9d6600-1042-11ea-914d-f18d4d032991.png">

Como se pude observar la imagen ya se encuentra subida en el clúster, ahora el siguiente paso es crear el despliegue, al cual le tiene que asignar un nombre para eso volvemos al entorno Ubuntu y el terminal se digita el siguiente comando: ```kubectl run <nombre del servicio> --image=registry.ng.bluemix.net/<nombre del cluster/tomcat>```.

<img width="650" alt="5" src="https://user-images.githubusercontent.com/50923637/69654420-c8bdf680-1042-11ea-9bff-3bed07eff7e8.png">

Una vez creado el despliegue con el nombre que se le asigno anteriormente podemos evidenciar en la plataforma de Kubernetes en la sección de despliegues, el proceso que se hizo anteriormente.

<img width="650" alt="6" src="https://user-images.githubusercontent.com/50923637/69654561-03279380-1043-11ea-85fd-56d615b435d2.png">

Igualmente, en el apartado de pods podemos observar lo siguiente.

<img width="650" alt="7" src="https://user-images.githubusercontent.com/50923637/69654664-26524300-1043-11ea-9b4c-49024f0088cc.png">

Luego de esto hay que exponer el servicio anteriormente creado, es necesario asignarle un nombre al “expose”, para que así podamos observar el despliegue con el siguiente comando: ```kubectl expose deployment/<nombre del servicio> --type=NodePort –port=8080 –name<nombre del expose> --target-port=8080```.

<img width="650" alt="8" src="https://user-images.githubusercontent.com/50923637/69654786-5b5e9580-1043-11ea-80bf-a338021e680c.png">

Una creado el “expose” podemos verificar si el servicio de Apache Tomcat ya fue desplegado en nuestro clúster. En el apartado de servicios, aparece el servicio que hemos creado anteriormente y debemos tomar el número del puerto en el cual fue desplegado el servicio de la siguiente manera:

<img width="650" alt="9" src="https://user-images.githubusercontent.com/50923637/69654876-83e68f80-1043-11ea-95ad-764562503e00.png">

En este caso el número del puerto es 32706.

Y finalmente para comprobar que el Apache Tomcat fue desplegado correctamente vamos a tomar el ingreso en la plataforma de IBM Cloud como se muestra en la imagen:

<img width="650" alt="10" src="https://user-images.githubusercontent.com/50923637/69654996-b1cbd400-1043-11ea-9559-c4b8b053bfef.png">

Y en el navegador debemos colocar el ingreso seguido del número del puesto en este caso sería: http://k8-demo-east.us-east.containers.appdomain.cloud:32706/.

<img width="650" alt="11" src="https://user-images.githubusercontent.com/50923637/69655053-cc05b200-1043-11ea-9325-4028c77e16c4.png">

De esta manera garantizamos que el servicio de Apache Tomcat fue desplegado correctamente en nuestro clúster usando el IBM Kubernetes Service y un entorno Ubuntu.
