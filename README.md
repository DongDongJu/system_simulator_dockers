# system_simulator_dockers
docker files for Multi core system simulators.


## for build 

in the simulator folder
~~~
docker build -t 'image-name-what-you-want' .
~~~

## for running docker image

~~~
docker run -it -d -t 'image-name' /bin/bash
check the container id from `docker ps`
docker exec -it 'container-name' /bin/bash
~~~
