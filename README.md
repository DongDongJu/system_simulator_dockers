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

## volume

if you want to connect the host folder to the folder inside docker container then 

add `-v /host/directory:/container/directory` option when you running the docker container.



### MaxSim

~~~
./scripts/buildMaxSim<Debug|Product>.sh
./scripts/runMaxSimDacapo.sh <output directory> <ZSim template configuration> <number of runs>
~~~

### sniper
the version of the sniper is 7.2.
sniper.tgz modified for compiling (fix some bug). 

sniper run example
~~~
go to test/fft
make run
~~~

~~~
in the host
docker run -it -v /path/to/example/sniper:/usr/src/sniper_example sniper-opencv2 ./run-sniper -- python /usr/src/sniper_example/class3.py /usr/src/sniper_example/noisy.avi /usr/src/sniper_example/output.avi
~~~
### GEM5

now this dockerfile build the version of ARM simulator
if you want to change the architecture or build setting then check the build.bash file in folder

gem5 run example 
~~~
./build/ARM/gem5.opt ./configs/example/se.py -c ./tests/test-progs/hello/bin/arm/linux/hello 
~~~

TODO: need to add download fs image file
ref) http://www.gem5.org/dist/current/arm/?C=M;O=A
