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


### GEM5

now this dockerfile build the version of ARM simulator
if you want to change the architecture or build setting then check the build.bash file in folder

gem5 run example 
~~~
./build/ARM/gem5.opt ./configs/example/se.py -c ./tests/test-progs/hello/bin/arm/linux/hello 
~~~
