# Django_REST_API_with_OpenCV_on_HEROKU
Django_REST_API_with_OpenCV_on_HEROKU


## Seen below a Dump / Log of the process -- Dockerfile >> Django App >> OpenCv >> Heroku Install 
#
## Search with FART ---- date .....
### FART --- 16 APR 18 
#

dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ # No Venv as creating a Docker Image for Django REST API 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
[sudo] password for dhankar: 
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                     PORTS               NAMES
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                         upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                       stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                       sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                         kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                         focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                         gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                         nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker run hello-world
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.35/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ## Searching for Django images on DockerHub
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker search django
Warning: failed to get default registry endpoint from daemon (Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.35/info: dial unix /var/run/docker.sock: connect: permission denied). Using system default: https://index.docker.io/v1/
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.35/images/search?limit=25&term=django: dial unix /var/run/docker.sock: connect: permission denied
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker search django
[sudo] password for dhankar: 
NAME                                  DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
django                                Django is a free web application framework, …   651                 [OK]                
dockerfiles/django-uwsgi-nginx        Dockerfile and configuration files to build …   144                                     [OK]
camandel/django-wiki                  wiki engine based on django framework           21                                      [OK]
alang/django                          This image can be used as a starting point t…   11                                      [OK]
praekeltfoundation/django-bootstrap   Dockerfile for quickly running Django projec…   9                                       [OK]
cloudhotspot/sample-django-app-base   Sample Django Application Base Image            5                                       [OK]
divio/django-cms-preview              django CMS Preview                              3                                       [OK]
bynd/nginx-django                     Docker container with nginx for simple Djang…   2                                       [OK]
geonode/django                        Django base image for GeoNode                   1                                       [OK]
abstracttechnology/django             A base image for Django-based webapps           1                                       [OK]
edoburu/django-base-images            Python base images to create Django projects    1                                       [OK]
universitas/django                    django universitas.no                           1                                       [OK]
aexea/django-base                                                                     1                                       [OK]
torz/django                           django 1.9.1 with python 3.5                    1                                       [OK]
accent/rancher-django-proxy           Django nginx proxy to app and static files      1                                       [OK]
krixapolinario/django-project-one     Django Project One                              1                                       [OK]
openshiftkatacoda/blog-django-py      Sample blog application implemented using Py…   1                                       [OK]
budddddddha/depotica-django           depotica django                                 0                                       [OK]
pypi/django-restify-framework         django-restify-framework PyPi package based …   0                                       [OK]
telusgelp/django                      Django + uwsgi                                  0                                       [OK]
aexea/django-sklearn-base             django + sklearn + skflow                       0                                       [OK]
vikingco/django-buildpkg              VikingCo Django base image (Based on CentOS …   0                                       
wildfish/django                       Python 3, Node.js, bower, less, Python and D…   0                                       
showpass/python-django                Django images built by Showpass                 0                                       [OK]
bchabord/django-nginx                 Django Nginx base image used for ECS            0                                       [OK]
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ## Searching the -- am already logged in as -- ddrohit
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ## docker hub registry == https://hub.docker.com/
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker search ubuntu
[sudo] password for dhankar: 
NAME                                                      DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
ubuntu                                                    Ubuntu is a Debian-based Linux operating sys…   7513                [OK]                
dorowu/ubuntu-desktop-lxde-vnc                            Ubuntu with openssh-server and NoVNC            179                                     [OK]
rastasheep/ubuntu-sshd                                    Dockerized SSH service, built on top of offi…   140                                     [OK]
ansible/ubuntu14.04-ansible                               Ubuntu 14.04 LTS with ansible                   91                                      [OK]
ubuntu-upstart                                            Upstart is an event-based replacement for th…   85                  [OK]                
neurodebian                                               NeuroDebian provides neuroscience research s…   47                  [OK]                
ubuntu-debootstrap                                        debootstrap --variant=minbase --components=m…   37                  [OK]                
1and1internet/ubuntu-16-nginx-php-phpmyadmin-mysql-5      ubuntu-16-nginx-php-phpmyadmin-mysql-5          33                                      [OK]
nuagebec/ubuntu                                           Simple always updated Ubuntu docker images w…   22                                      [OK]
tutum/ubuntu                                              Simple Ubuntu docker images with SSH access     18                                      
ppc64le/ubuntu                                            Ubuntu is a Debian-based Linux operating sys…   12                                      
i386/ubuntu                                               Ubuntu is a Debian-based Linux operating sys…   12                                      
1and1internet/ubuntu-16-apache-php-7.0                    ubuntu-16-apache-php-7.0                        9                                       [OK]
eclipse/ubuntu_jdk8                                       Ubuntu, JDK8, Maven 3, git, curl, nmap, mc, …   5                                       [OK]
1and1internet/ubuntu-16-nginx-php-phpmyadmin-mariadb-10   ubuntu-16-nginx-php-phpmyadmin-mariadb-10       4                                       [OK]
1and1internet/ubuntu-16-nginx-php-5.6-wordpress-4         ubuntu-16-nginx-php-5.6-wordpress-4             3                                       [OK]
codenvy/ubuntu_jdk8                                       Ubuntu, JDK8, Maven 3, git, curl, nmap, mc, …   3                                       [OK]
darksheer/ubuntu                                          Base Ubuntu Image -- Updated hourly             3                                       [OK]
1and1internet/ubuntu-16-apache                            ubuntu-16-apache                                3                                       [OK]
pivotaldata/ubuntu                                        A quick freshening-up of the base Ubuntu doc…   1                                       
ossobv/ubuntu                                             Custom ubuntu image from scratch (based on o…   0                                       
pivotaldata/ubuntu-gpdb-dev                               Ubuntu images for GPDB development              0                                       
smartentry/ubuntu                                         ubuntu with smartentry                          0                                       [OK]
1and1internet/ubuntu-16-sshd                              ubuntu-16-sshd                                  0                                       [OK]
1and1internet/ubuntu-16-healthcheck                       ubuntu-16-healthcheck                           0                                       [OK]
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 

### FART --- ERROR --- as i copied the --- Dockerfile.devel --- from the TensorFlow Repo and changed the Content 
### Was then required to create another "Dockerfile"
###
###
###
 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker pull ubuntu:xenial
xenial: Pulling from library/ubuntu
d3938036b19c: Pull complete 
a9b30c108bda: Pull complete 
67de21feec18: Pull complete 
817da545be2b: Pull complete 
d967c497ce23: Pull complete 
Digest: sha256:9ee3b83bcaa383e5e3b657f042f4034c92cdd50c03f73166c145c9ceaea9ba7c
Status: Downloaded newer image for ubuntu:xenial
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
[sudo] password for dhankar: 
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                     PORTS               NAMES
c22d41606b1b        hello-world                        "/hello"                 4 hours ago         Exited (0) 4 hours ago                         condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                         upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                       stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                       sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                         kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                         focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                         gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                         nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ls
db.sqlite3  Dockerfile.devel  indexapp  info2  manage.py  Procfile  requirements.txt  static_in_pro
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker build –t dck1:latest .
"docker build" requires exactly 1 argument.
See 'docker build --help'.

Usage:  docker build [OPTIONS] PATH | URL | - [flags]

Build an image from a Dockerfile
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker build –t ddrohit/dck1 .
"docker build" requires exactly 1 argument.
See 'docker build --help'.

Usage:  docker build [OPTIONS] PATH | URL | - [flags]

Build an image from a Dockerfile
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker build .
unable to prepare context: unable to evaluate symlinks in Dockerfile path: lstat /media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI/Dockerfile: no such file or directory
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker build .
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.35/build?buildargs=%7B%7D&cachefrom=%5B%5D&cgroupparent=&cpuperiod=0&cpuquota=0&cpusetcpus=&cpusetmems=&cpushares=0&dockerfile=Dockerfile&labels=%7B%7D&memory=0&memswap=0&networkmode=default&rm=1&session=04fb7acda7da86c800829ba5ea5d0392d71ee4ab506b108439beb3105a39f802&shmsize=0&target=&ulimits=null: dial unix /var/run/docker.sock: connect: permission denied
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build .
[sudo] password for dhankar: 
Sending build context to Docker daemon  1.861MB
Step 1/10 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/10 : RUN apt-get update
 ---> Running in 648b4a2a87ae
Get:1 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial/universe Sources [9802 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [78.5 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [602 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [12.7 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [431 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3489 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1558 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [14.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [9827 kB]
^C
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                     PORTS               NAMES
c22d41606b1b        hello-world                        "/hello"                 5 hours ago         Exited (0) 5 hours ago                         condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                         upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                       stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                       sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                         kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                         focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                         gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                         nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
[sudo] password for dhankar: 
Sending build context to Docker daemon  1.861MB
Step 1/10 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/10 : RUN apt-get update
 ---> Running in e441f7955691
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
^C
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.862MB
Step 1/13 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/13 : RUN apt-get update
 ---> Running in 3c2b8afb92b4
Get:1 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial/universe Sources [9802 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [78.5 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [602 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [12.7 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [431 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1558 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3489 B]
Get:12 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [14.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [9827 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [176 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [253 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [979 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [13.1 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [799 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [18.5 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [5153 B]
Get:21 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages [7734 B]
Fetched 25.1 MB in 13s (1866 kB/s)
Reading package lists...
Removing intermediate container 3c2b8afb92b4
 ---> 6bc0d0de6516
Step 3/13 : RUN echo "updated the package manager..."
 ---> Running in aaa357a4703e
updated the package manager...
Removing intermediate container aaa357a4703e
 ---> 2fe01c0ad13d
Step 4/13 : RUN apt-get install -y python3 # install python3
 ---> Running in 95d0b459112c
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
  dh-python file libexpat1 libmagic1 libmpdec2 libpython3-stdlib
  libpython3.5-minimal libpython3.5-stdlib libsqlite3-0 libssl1.0.0
  mime-support python3-minimal python3.5 python3.5-minimal
Suggested packages:
  libdpkg-perl python3-doc python3-tk python3-venv python3.5-venv
  python3.5-doc binutils binfmt-support
The following NEW packages will be installed:
  dh-python file libexpat1 libmagic1 libmpdec2 libpython3-stdlib
  libpython3.5-minimal libpython3.5-stdlib libsqlite3-0 libssl1.0.0
  mime-support python3 python3-minimal python3.5 python3.5-minimal
0 upgraded, 15 newly installed, 0 to remove and 4 not upgraded.
Need to get 6431 kB of archives.
After this operation, 33.3 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libssl1.0.0 amd64 1.0.2g-1ubuntu4.11 [1082 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython3.5-minimal amd64 3.5.2-2ubuntu0~16.04.4 [523 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libexpat1 amd64 2.1.0-7ubuntu0.16.04.3 [71.2 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3.5-minimal amd64 3.5.2-2ubuntu0~16.04.4 [1597 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 python3-minimal amd64 3.5.1-3 [23.3 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 mime-support all 3.59ubuntu1 [31.0 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial/main amd64 libmpdec2 amd64 2.4.2-1 [82.6 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial/main amd64 libsqlite3-0 amd64 3.11.0-1ubuntu1 [396 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython3.5-stdlib amd64 3.5.2-2ubuntu0~16.04.4 [2132 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3.5 amd64 3.5.2-2ubuntu0~16.04.4 [165 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial/main amd64 libpython3-stdlib amd64 3.5.1-3 [6818 B]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 dh-python all 2.20151103ubuntu1.1 [74.1 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial/main amd64 python3 amd64 3.5.1-3 [8710 B]
Get:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 libmagic1 amd64 1:5.25-2ubuntu1 [216 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial/main amd64 file amd64 1:5.25-2ubuntu1 [21.2 kB]
debconf: delaying package configuration, since apt-utils is not installed
Fetched 6431 kB in 3s (1720 kB/s)
Selecting previously unselected package libssl1.0.0:amd64.
(Reading database ... 4768 files and directories currently installed.)
Preparing to unpack .../libssl1.0.0_1.0.2g-1ubuntu4.11_amd64.deb ...
Unpacking libssl1.0.0:amd64 (1.0.2g-1ubuntu4.11) ...
Selecting previously unselected package libpython3.5-minimal:amd64.
Preparing to unpack .../libpython3.5-minimal_3.5.2-2ubuntu0~16.04.4_amd64.deb ...
Unpacking libpython3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.4) ...
Selecting previously unselected package libexpat1:amd64.
Preparing to unpack .../libexpat1_2.1.0-7ubuntu0.16.04.3_amd64.deb ...
Unpacking libexpat1:amd64 (2.1.0-7ubuntu0.16.04.3) ...
Selecting previously unselected package python3.5-minimal.
Preparing to unpack .../python3.5-minimal_3.5.2-2ubuntu0~16.04.4_amd64.deb ...
Unpacking python3.5-minimal (3.5.2-2ubuntu0~16.04.4) ...
Selecting previously unselected package python3-minimal.
Preparing to unpack .../python3-minimal_3.5.1-3_amd64.deb ...
Unpacking python3-minimal (3.5.1-3) ...
Selecting previously unselected package mime-support.
Preparing to unpack .../mime-support_3.59ubuntu1_all.deb ...
Unpacking mime-support (3.59ubuntu1) ...
Selecting previously unselected package libmpdec2:amd64.
Preparing to unpack .../libmpdec2_2.4.2-1_amd64.deb ...
Unpacking libmpdec2:amd64 (2.4.2-1) ...
Selecting previously unselected package libsqlite3-0:amd64.
Preparing to unpack .../libsqlite3-0_3.11.0-1ubuntu1_amd64.deb ...
Unpacking libsqlite3-0:amd64 (3.11.0-1ubuntu1) ...
Selecting previously unselected package libpython3.5-stdlib:amd64.
Preparing to unpack .../libpython3.5-stdlib_3.5.2-2ubuntu0~16.04.4_amd64.deb ...
Unpacking libpython3.5-stdlib:amd64 (3.5.2-2ubuntu0~16.04.4) ...
Selecting previously unselected package python3.5.
Preparing to unpack .../python3.5_3.5.2-2ubuntu0~16.04.4_amd64.deb ...
Unpacking python3.5 (3.5.2-2ubuntu0~16.04.4) ...
Selecting previously unselected package libpython3-stdlib:amd64.
Preparing to unpack .../libpython3-stdlib_3.5.1-3_amd64.deb ...
Unpacking libpython3-stdlib:amd64 (3.5.1-3) ...
Selecting previously unselected package dh-python.
Preparing to unpack .../dh-python_2.20151103ubuntu1.1_all.deb ...
Unpacking dh-python (2.20151103ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up libssl1.0.0:amd64 (1.0.2g-1ubuntu4.11) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.22.1 /usr/local/share/perl/5.22.1 /usr/lib/x86_64-linux-gnu/perl5/5.22 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.22 /usr/share/perl/5.22 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base .) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Setting up libpython3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.4) ...
Setting up libexpat1:amd64 (2.1.0-7ubuntu0.16.04.3) ...
Setting up python3.5-minimal (3.5.2-2ubuntu0~16.04.4) ...
Setting up python3-minimal (3.5.1-3) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Selecting previously unselected package python3.
(Reading database ... 5744 files and directories currently installed.)
Preparing to unpack .../python3_3.5.1-3_amd64.deb ...
Unpacking python3 (3.5.1-3) ...
Selecting previously unselected package libmagic1:amd64.
Preparing to unpack .../libmagic1_1%3a5.25-2ubuntu1_amd64.deb ...
Unpacking libmagic1:amd64 (1:5.25-2ubuntu1) ...
Selecting previously unselected package file.
Preparing to unpack .../file_1%3a5.25-2ubuntu1_amd64.deb ...
Unpacking file (1:5.25-2ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up mime-support (3.59ubuntu1) ...
Setting up libmpdec2:amd64 (2.4.2-1) ...
Setting up libsqlite3-0:amd64 (3.11.0-1ubuntu1) ...
Setting up libpython3.5-stdlib:amd64 (3.5.2-2ubuntu0~16.04.4) ...
Setting up python3.5 (3.5.2-2ubuntu0~16.04.4) ...
Setting up libpython3-stdlib:amd64 (3.5.1-3) ...
Setting up libmagic1:amd64 (1:5.25-2ubuntu1) ...
Setting up file (1:5.25-2ubuntu1) ...
Setting up python3 (3.5.1-3) ...
running python rtupdate hooks for python3.5...
running python post-rtupdate hooks for python3.5...
Setting up dh-python (2.20151103ubuntu1.1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Removing intermediate container 95d0b459112c
 ---> cde60d61973a
Step 5/13 : RUN echo "installed python3..."
 ---> Running in 3fbf64b69d9f
installed python3...
Removing intermediate container 3fbf64b69d9f
 ---> 11681c422810
Step 6/13 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Running in 73b4532cc292
Reading package lists...
Building dependency tree...
Reading state information...
The following additional packages will be installed:
  binutils bzip2 ca-certificates cpp cpp-5 dpkg-dev fakeroot g++ g++-5 gcc
  gcc-5 ifupdown iproute2 isc-dhcp-client isc-dhcp-common
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan2 libatm1 libatomic1 libc-dev-bin libc6-dev libcc1-0 libcilkrts5
  libdns-export162 libdpkg-perl libexpat1-dev libfakeroot libffi6
  libfile-fcntllock-perl libgcc-5-dev libgdbm3 libgmp10 libgomp1
  libisc-export160 libisl15 libitm1 liblsan0 libmnl0 libmpc3 libmpfr4 libmpx0
  libperl5.22 libpython-all-dev libpython-dev libpython-stdlib libpython2.7
  libpython2.7-dev libpython2.7-minimal libpython2.7-stdlib libquadmath0
  libstdc++-5-dev libtsan0 libubsan0 libxtables11 linux-libc-dev make manpages
  manpages-dev netbase openssl patch perl perl-modules-5.22 python python-all
  python-all-dev python-minimal python-pip-whl python-pkg-resources
  python-setuptools python-wheel python2.7 python2.7-dev python2.7-minimal
  rename xz-utils
Suggested packages:
  binutils-doc bzip2-doc cpp-doc gcc-5-locales debian-keyring g++-multilib
  g++-5-multilib gcc-5-doc libstdc++6-5-dbg gcc-multilib autoconf automake
  libtool flex bison gdb gcc-doc gcc-5-multilib libgcc1-dbg libgomp1-dbg
  libitm1-dbg libatomic1-dbg libasan2-dbg liblsan0-dbg libtsan0-dbg
  libubsan0-dbg libcilkrts5-dbg libmpx0-dbg libquadmath0-dbg ppp rdnssd
  iproute2-doc resolvconf avahi-autoipd isc-dhcp-client-ddns apparmor
  glibc-doc libstdc++-5-doc make-doc man-browser ed diffutils-doc perl-doc
  libterm-readline-gnu-perl | libterm-readline-perl-perl python-doc python-tk
  python-setuptools-doc python2.7-doc binfmt-support
The following NEW packages will be installed:
  binutils build-essential bzip2 ca-certificates cpp cpp-5 dpkg-dev fakeroot
  g++ g++-5 gcc gcc-5 ifupdown iproute2 isc-dhcp-client isc-dhcp-common
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan2 libatm1 libatomic1 libc-dev-bin libc6-dev libcc1-0 libcilkrts5
  libdns-export162 libdpkg-perl libexpat1-dev libfakeroot libffi6
  libfile-fcntllock-perl libgcc-5-dev libgdbm3 libgmp10 libgomp1
  libisc-export160 libisl15 libitm1 liblsan0 libmnl0 libmpc3 libmpfr4 libmpx0
  libperl5.22 libpython-all-dev libpython-dev libpython-stdlib libpython2.7
  libpython2.7-dev libpython2.7-minimal libpython2.7-stdlib libquadmath0
  libstdc++-5-dev libtsan0 libubsan0 libxtables11 linux-libc-dev make manpages
  manpages-dev netbase openssl patch perl perl-modules-5.22 python python-all
  python-all-dev python-dev python-minimal python-pip python-pip-whl
  python-pkg-resources python-setuptools python-wheel python2.7 python2.7-dev
  python2.7-minimal rename xz-utils
0 upgraded, 81 newly installed, 0 to remove and 4 not upgraded.
Need to get 83.7 MB of archives.
After this operation, 259 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 libatm1 amd64 1:2.5.1-1.5 [24.2 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main amd64 libmnl0 amd64 1.0.3-5 [12.0 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgdbm3 amd64 1.8.3-13.1 [16.9 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 perl-modules-5.22 all 5.22.1-9ubuntu0.2 [2661 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libperl5.22 amd64 5.22.1-9ubuntu0.2 [3391 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 perl amd64 5.22.1-9ubuntu0.2 [237 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7-minimal amd64 2.7.12-1ubuntu0~16.04.3 [340 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python2.7-minimal amd64 2.7.12-1ubuntu0~16.04.3 [1261 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python-minimal amd64 2.7.12-1~16.04 [28.1 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial/main amd64 libffi6 amd64 3.2.1-4 [17.8 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7-stdlib amd64 2.7.12-1ubuntu0~16.04.3 [1880 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python2.7 amd64 2.7.12-1ubuntu0~16.04.3 [224 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython-stdlib amd64 2.7.12-1~16.04 [7768 B]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python amd64 2.7.12-1~16.04 [137 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgmp10 amd64 2:6.1.0+dfsg-2 [240 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial/main amd64 libmpfr4 amd64 3.1.4-1 [191 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial/main amd64 libmpc3 amd64 1.0.3-1 [39.7 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial/main amd64 bzip2 amd64 1.0.6-8 [32.7 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 iproute2 amd64 4.3.0-1ubuntu3.16.04.3 [522 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 ifupdown amd64 0.8.10ubuntu1.2 [54.9 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libisc-export160 amd64 1:9.10.3.dfsg.P4-8ubuntu1.10 [153 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdns-export162 amd64 1:9.10.3.dfsg.P4-8ubuntu1.10 [666 kB]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 isc-dhcp-client amd64 4.3.3-5ubuntu12.10 [224 kB]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 isc-dhcp-common amd64 4.3.3-5ubuntu12.10 [105 kB]
Get:25 http://archive.ubuntu.com/ubuntu xenial/main amd64 libxtables11 amd64 1.6.0-2ubuntu3 [27.2 kB]
Get:26 http://archive.ubuntu.com/ubuntu xenial/main amd64 netbase all 5.3 [12.9 kB]
Get:27 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 openssl amd64 1.0.2g-1ubuntu4.11 [492 kB]
Get:28 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 ca-certificates all 20170717~16.04.1 [168 kB]
Get:29 http://archive.ubuntu.com/ubuntu xenial/main amd64 manpages all 4.04-2 [1087 kB]
Get:30 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 binutils amd64 2.26.1-1ubuntu1~16.04.6 [2311 kB]
Get:31 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu10 [68.7 kB]
Get:32 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-119.143 [845 kB]
Get:33 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu10 [2079 kB]
Get:34 http://archive.ubuntu.com/ubuntu xenial/main amd64 libisl15 amd64 0.16.1-1 [524 kB]
Get:35 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 cpp-5 amd64 5.4.0-6ubuntu1~16.04.9 [7685 kB]
Get:36 http://archive.ubuntu.com/ubuntu xenial/main amd64 cpp amd64 4:5.3.1-1ubuntu1 [27.7 kB]
Get:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcc1-0 amd64 5.4.0-6ubuntu1~16.04.9 [38.8 kB]
Get:38 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgomp1 amd64 5.4.0-6ubuntu1~16.04.9 [55.0 kB]
Get:39 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libitm1 amd64 5.4.0-6ubuntu1~16.04.9 [27.4 kB]
Get:40 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libatomic1 amd64 5.4.0-6ubuntu1~16.04.9 [8882 B]
Get:41 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libasan2 amd64 5.4.0-6ubuntu1~16.04.9 [264 kB]
Get:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 liblsan0 amd64 5.4.0-6ubuntu1~16.04.9 [105 kB]
Get:43 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libtsan0 amd64 5.4.0-6ubuntu1~16.04.9 [244 kB]
Get:44 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libubsan0 amd64 5.4.0-6ubuntu1~16.04.9 [95.2 kB]
Get:45 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcilkrts5 amd64 5.4.0-6ubuntu1~16.04.9 [40.1 kB]
Get:46 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libmpx0 amd64 5.4.0-6ubuntu1~16.04.9 [9774 B]
Get:47 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libquadmath0 amd64 5.4.0-6ubuntu1~16.04.9 [131 kB]
Get:48 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgcc-5-dev amd64 5.4.0-6ubuntu1~16.04.9 [2242 kB]
Get:49 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 gcc-5 amd64 5.4.0-6ubuntu1~16.04.9 [8650 kB]
Get:50 http://archive.ubuntu.com/ubuntu xenial/main amd64 gcc amd64 4:5.3.1-1ubuntu1 [5244 B]
Get:51 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libstdc++-5-dev amd64 5.4.0-6ubuntu1~16.04.9 [1427 kB]
Get:52 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 g++-5 amd64 5.4.0-6ubuntu1~16.04.9 [8333 kB]
Get:53 http://archive.ubuntu.com/ubuntu xenial/main amd64 g++ amd64 4:5.3.1-1ubuntu1 [1504 B]
Get:54 http://archive.ubuntu.com/ubuntu xenial/main amd64 make amd64 4.1-6 [151 kB]
Get:55 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdpkg-perl all 1.18.4ubuntu1.4 [195 kB]
Get:56 http://archive.ubuntu.com/ubuntu xenial/main amd64 xz-utils amd64 5.1.1alpha+20120614-2ubuntu2 [78.8 kB]
Get:57 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 patch amd64 2.7.5-1ubuntu0.16.04.1 [90.5 kB]
Get:58 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 dpkg-dev all 1.18.4ubuntu1.4 [584 kB]
Get:59 http://archive.ubuntu.com/ubuntu xenial/main amd64 build-essential amd64 12.1ubuntu2 [4758 B]
Get:60 http://archive.ubuntu.com/ubuntu xenial/main amd64 libfakeroot amd64 1.20.2-1ubuntu1 [25.5 kB]
Get:61 http://archive.ubuntu.com/ubuntu xenial/main amd64 fakeroot amd64 1.20.2-1ubuntu1 [61.8 kB]
Get:62 http://archive.ubuntu.com/ubuntu xenial/main amd64 libalgorithm-diff-perl all 1.19.03-1 [47.6 kB]
Get:63 http://archive.ubuntu.com/ubuntu xenial/main amd64 libalgorithm-diff-xs-perl amd64 0.04-4build1 [11.0 kB]
Get:64 http://archive.ubuntu.com/ubuntu xenial/main amd64 libalgorithm-merge-perl all 0.08-3 [12.0 kB]
Get:65 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libexpat1-dev amd64 2.1.0-7ubuntu0.16.04.3 [115 kB]
Get:66 http://archive.ubuntu.com/ubuntu xenial/main amd64 libfile-fcntllock-perl amd64 0.22-3 [32.0 kB]
Get:67 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7 amd64 2.7.12-1ubuntu0~16.04.3 [1070 kB]
Get:68 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7-dev amd64 2.7.12-1ubuntu0~16.04.3 [27.8 MB]
Get:69 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython-dev amd64 2.7.12-1~16.04 [7840 B]
Get:70 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython-all-dev amd64 2.7.12-1~16.04 [1006 B]
Get:71 http://archive.ubuntu.com/ubuntu xenial/main amd64 manpages-dev all 4.04-2 [2048 kB]
Get:72 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python-all amd64 2.7.12-1~16.04 [996 B]
Get:73 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python2.7-dev amd64 2.7.12-1ubuntu0~16.04.3 [276 kB]
Get:74 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python-dev amd64 2.7.12-1~16.04 [1186 B]
Get:75 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 python-all-dev amd64 2.7.12-1~16.04 [1016 B]
Get:76 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 python-pip-whl all 8.1.1-2ubuntu0.4 [1110 kB]
Get:77 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 python-pip all 8.1.1-2ubuntu0.4 [144 kB]
Get:78 http://archive.ubuntu.com/ubuntu xenial/main amd64 python-pkg-resources all 20.7.0-1 [108 kB]
Get:79 http://archive.ubuntu.com/ubuntu xenial/main amd64 python-setuptools all 20.7.0-1 [169 kB]
Get:80 http://archive.ubuntu.com/ubuntu xenial/universe amd64 python-wheel all 0.29.0-1 [48.0 kB]
Get:81 http://archive.ubuntu.com/ubuntu xenial/main amd64 rename all 0.20-4 [12.0 kB]
debconf: delaying package configuration, since apt-utils is not installed
Fetched 83.7 MB in 40s (2089 kB/s)
Selecting previously unselected package libatm1:amd64.
(Reading database ... 5787 files and directories currently installed.)
Preparing to unpack .../libatm1_1%3a2.5.1-1.5_amd64.deb ...
Unpacking libatm1:amd64 (1:2.5.1-1.5) ...
Selecting previously unselected package libmnl0:amd64.
Preparing to unpack .../libmnl0_1.0.3-5_amd64.deb ...
Unpacking libmnl0:amd64 (1.0.3-5) ...
Selecting previously unselected package libgdbm3:amd64.
Preparing to unpack .../libgdbm3_1.8.3-13.1_amd64.deb ...
Unpacking libgdbm3:amd64 (1.8.3-13.1) ...
Selecting previously unselected package perl-modules-5.22.
Preparing to unpack .../perl-modules-5.22_5.22.1-9ubuntu0.2_all.deb ...
Unpacking perl-modules-5.22 (5.22.1-9ubuntu0.2) ...
Selecting previously unselected package libperl5.22:amd64.
Preparing to unpack .../libperl5.22_5.22.1-9ubuntu0.2_amd64.deb ...
Unpacking libperl5.22:amd64 (5.22.1-9ubuntu0.2) ...
Selecting previously unselected package perl.
Preparing to unpack .../perl_5.22.1-9ubuntu0.2_amd64.deb ...
Unpacking perl (5.22.1-9ubuntu0.2) ...
Selecting previously unselected package libpython2.7-minimal:amd64.
Preparing to unpack .../libpython2.7-minimal_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking libpython2.7-minimal:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package python2.7-minimal.
Preparing to unpack .../python2.7-minimal_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking python2.7-minimal (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package python-minimal.
Preparing to unpack .../python-minimal_2.7.12-1~16.04_amd64.deb ...
Unpacking python-minimal (2.7.12-1~16.04) ...
Selecting previously unselected package libffi6:amd64.
Preparing to unpack .../libffi6_3.2.1-4_amd64.deb ...
Unpacking libffi6:amd64 (3.2.1-4) ...
Selecting previously unselected package libpython2.7-stdlib:amd64.
Preparing to unpack .../libpython2.7-stdlib_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking libpython2.7-stdlib:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package python2.7.
Preparing to unpack .../python2.7_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking python2.7 (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package libpython-stdlib:amd64.
Preparing to unpack .../libpython-stdlib_2.7.12-1~16.04_amd64.deb ...
Unpacking libpython-stdlib:amd64 (2.7.12-1~16.04) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libpython2.7-minimal:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Setting up python2.7-minimal (2.7.12-1ubuntu0~16.04.3) ...
Linking and byte-compiling packages for runtime python2.7...
Setting up python-minimal (2.7.12-1~16.04) ...
Selecting previously unselected package python.
(Reading database ... 8324 files and directories currently installed.)
Preparing to unpack .../python_2.7.12-1~16.04_amd64.deb ...
Unpacking python (2.7.12-1~16.04) ...
Selecting previously unselected package libgmp10:amd64.
Preparing to unpack .../libgmp10_2%3a6.1.0+dfsg-2_amd64.deb ...
Unpacking libgmp10:amd64 (2:6.1.0+dfsg-2) ...
Selecting previously unselected package libmpfr4:amd64.
Preparing to unpack .../libmpfr4_3.1.4-1_amd64.deb ...
Unpacking libmpfr4:amd64 (3.1.4-1) ...
Selecting previously unselected package libmpc3:amd64.
Preparing to unpack .../libmpc3_1.0.3-1_amd64.deb ...
Unpacking libmpc3:amd64 (1.0.3-1) ...
Selecting previously unselected package bzip2.
Preparing to unpack .../bzip2_1.0.6-8_amd64.deb ...
Unpacking bzip2 (1.0.6-8) ...
Selecting previously unselected package iproute2.
Preparing to unpack .../iproute2_4.3.0-1ubuntu3.16.04.3_amd64.deb ...
Unpacking iproute2 (4.3.0-1ubuntu3.16.04.3) ...
Selecting previously unselected package ifupdown.
Preparing to unpack .../ifupdown_0.8.10ubuntu1.2_amd64.deb ...
Unpacking ifupdown (0.8.10ubuntu1.2) ...
Selecting previously unselected package libisc-export160.
Preparing to unpack .../libisc-export160_1%3a9.10.3.dfsg.P4-8ubuntu1.10_amd64.deb ...
Unpacking libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1.10) ...
Selecting previously unselected package libdns-export162.
Preparing to unpack .../libdns-export162_1%3a9.10.3.dfsg.P4-8ubuntu1.10_amd64.deb ...
Unpacking libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1.10) ...
Selecting previously unselected package isc-dhcp-client.
Preparing to unpack .../isc-dhcp-client_4.3.3-5ubuntu12.10_amd64.deb ...
Unpacking isc-dhcp-client (4.3.3-5ubuntu12.10) ...
Selecting previously unselected package isc-dhcp-common.
Preparing to unpack .../isc-dhcp-common_4.3.3-5ubuntu12.10_amd64.deb ...
Unpacking isc-dhcp-common (4.3.3-5ubuntu12.10) ...
Selecting previously unselected package libxtables11:amd64.
Preparing to unpack .../libxtables11_1.6.0-2ubuntu3_amd64.deb ...
Unpacking libxtables11:amd64 (1.6.0-2ubuntu3) ...
Selecting previously unselected package netbase.
Preparing to unpack .../archives/netbase_5.3_all.deb ...
Unpacking netbase (5.3) ...
Selecting previously unselected package openssl.
Preparing to unpack .../openssl_1.0.2g-1ubuntu4.11_amd64.deb ...
Unpacking openssl (1.0.2g-1ubuntu4.11) ...
Selecting previously unselected package ca-certificates.
Preparing to unpack .../ca-certificates_20170717~16.04.1_all.deb ...
Unpacking ca-certificates (20170717~16.04.1) ...
Selecting previously unselected package manpages.
Preparing to unpack .../manpages_4.04-2_all.deb ...
Unpacking manpages (4.04-2) ...
Selecting previously unselected package binutils.
Preparing to unpack .../binutils_2.26.1-1ubuntu1~16.04.6_amd64.deb ...
Unpacking binutils (2.26.1-1ubuntu1~16.04.6) ...
Selecting previously unselected package libc-dev-bin.
Preparing to unpack .../libc-dev-bin_2.23-0ubuntu10_amd64.deb ...
Unpacking libc-dev-bin (2.23-0ubuntu10) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../linux-libc-dev_4.4.0-119.143_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-119.143) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../libc6-dev_2.23-0ubuntu10_amd64.deb ...
Unpacking libc6-dev:amd64 (2.23-0ubuntu10) ...
Selecting previously unselected package libisl15:amd64.
Preparing to unpack .../libisl15_0.16.1-1_amd64.deb ...
Unpacking libisl15:amd64 (0.16.1-1) ...
Selecting previously unselected package cpp-5.
Preparing to unpack .../cpp-5_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking cpp-5 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package cpp.
Preparing to unpack .../cpp_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking cpp (4:5.3.1-1ubuntu1) ...
Selecting previously unselected package libcc1-0:amd64.
Preparing to unpack .../libcc1-0_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libcc1-0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libgomp1:amd64.
Preparing to unpack .../libgomp1_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libgomp1:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libitm1:amd64.
Preparing to unpack .../libitm1_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libitm1:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libatomic1:amd64.
Preparing to unpack .../libatomic1_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libatomic1:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libasan2:amd64.
Preparing to unpack .../libasan2_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libasan2:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package liblsan0:amd64.
Preparing to unpack .../liblsan0_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking liblsan0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libtsan0:amd64.
Preparing to unpack .../libtsan0_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libtsan0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libubsan0:amd64.
Preparing to unpack .../libubsan0_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libubsan0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libcilkrts5:amd64.
Preparing to unpack .../libcilkrts5_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libcilkrts5:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libmpx0:amd64.
Preparing to unpack .../libmpx0_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libmpx0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libquadmath0:amd64.
Preparing to unpack .../libquadmath0_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libquadmath0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package libgcc-5-dev:amd64.
Preparing to unpack .../libgcc-5-dev_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libgcc-5-dev:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package gcc-5.
Preparing to unpack .../gcc-5_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking gcc-5 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package gcc.
Preparing to unpack .../gcc_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking gcc (4:5.3.1-1ubuntu1) ...
Selecting previously unselected package libstdc++-5-dev:amd64.
Preparing to unpack .../libstdc++-5-dev_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package g++-5.
Preparing to unpack .../g++-5_5.4.0-6ubuntu1~16.04.9_amd64.deb ...
Unpacking g++-5 (5.4.0-6ubuntu1~16.04.9) ...
Selecting previously unselected package g++.
Preparing to unpack .../g++_4%3a5.3.1-1ubuntu1_amd64.deb ...
Unpacking g++ (4:5.3.1-1ubuntu1) ...
Selecting previously unselected package make.
Preparing to unpack .../archives/make_4.1-6_amd64.deb ...
Unpacking make (4.1-6) ...
Selecting previously unselected package libdpkg-perl.
Preparing to unpack .../libdpkg-perl_1.18.4ubuntu1.4_all.deb ...
Unpacking libdpkg-perl (1.18.4ubuntu1.4) ...
Selecting previously unselected package xz-utils.
Preparing to unpack .../xz-utils_5.1.1alpha+20120614-2ubuntu2_amd64.deb ...
Unpacking xz-utils (5.1.1alpha+20120614-2ubuntu2) ...
Selecting previously unselected package patch.
Preparing to unpack .../patch_2.7.5-1ubuntu0.16.04.1_amd64.deb ...
Unpacking patch (2.7.5-1ubuntu0.16.04.1) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../dpkg-dev_1.18.4ubuntu1.4_all.deb ...
Unpacking dpkg-dev (1.18.4ubuntu1.4) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../build-essential_12.1ubuntu2_amd64.deb ...
Unpacking build-essential (12.1ubuntu2) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20.2-1ubuntu1_amd64.deb ...
Unpacking fakeroot (1.20.2-1ubuntu1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../libalgorithm-diff-perl_1.19.03-1_all.deb ...
Unpacking libalgorithm-diff-perl (1.19.03-1) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Preparing to unpack .../libalgorithm-diff-xs-perl_0.04-4build1_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl (0.04-4build1) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../libalgorithm-merge-perl_0.08-3_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-3) ...
Selecting previously unselected package libexpat1-dev:amd64.
Preparing to unpack .../libexpat1-dev_2.1.0-7ubuntu0.16.04.3_amd64.deb ...
Unpacking libexpat1-dev:amd64 (2.1.0-7ubuntu0.16.04.3) ...
Selecting previously unselected package libfile-fcntllock-perl.
Preparing to unpack .../libfile-fcntllock-perl_0.22-3_amd64.deb ...
Unpacking libfile-fcntllock-perl (0.22-3) ...
Selecting previously unselected package libpython2.7:amd64.
Preparing to unpack .../libpython2.7_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking libpython2.7:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package libpython2.7-dev:amd64.
Preparing to unpack .../libpython2.7-dev_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking libpython2.7-dev:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package libpython-dev:amd64.
Preparing to unpack .../libpython-dev_2.7.12-1~16.04_amd64.deb ...
Unpacking libpython-dev:amd64 (2.7.12-1~16.04) ...
Selecting previously unselected package libpython-all-dev:amd64.
Preparing to unpack .../libpython-all-dev_2.7.12-1~16.04_amd64.deb ...
Unpacking libpython-all-dev:amd64 (2.7.12-1~16.04) ...
Selecting previously unselected package manpages-dev.
Preparing to unpack .../manpages-dev_4.04-2_all.deb ...
Unpacking manpages-dev (4.04-2) ...
Selecting previously unselected package python-all.
Preparing to unpack .../python-all_2.7.12-1~16.04_amd64.deb ...
Unpacking python-all (2.7.12-1~16.04) ...
Selecting previously unselected package python2.7-dev.
Preparing to unpack .../python2.7-dev_2.7.12-1ubuntu0~16.04.3_amd64.deb ...
Unpacking python2.7-dev (2.7.12-1ubuntu0~16.04.3) ...
Selecting previously unselected package python-dev.
Preparing to unpack .../python-dev_2.7.12-1~16.04_amd64.deb ...
Unpacking python-dev (2.7.12-1~16.04) ...
Selecting previously unselected package python-all-dev.
Preparing to unpack .../python-all-dev_2.7.12-1~16.04_amd64.deb ...
Unpacking python-all-dev (2.7.12-1~16.04) ...
Selecting previously unselected package python-pip-whl.
Preparing to unpack .../python-pip-whl_8.1.1-2ubuntu0.4_all.deb ...
Unpacking python-pip-whl (8.1.1-2ubuntu0.4) ...
Selecting previously unselected package python-pip.
Preparing to unpack .../python-pip_8.1.1-2ubuntu0.4_all.deb ...
Unpacking python-pip (8.1.1-2ubuntu0.4) ...
Selecting previously unselected package python-pkg-resources.
Preparing to unpack .../python-pkg-resources_20.7.0-1_all.deb ...
Unpacking python-pkg-resources (20.7.0-1) ...
Selecting previously unselected package python-setuptools.
Preparing to unpack .../python-setuptools_20.7.0-1_all.deb ...
Unpacking python-setuptools (20.7.0-1) ...
Selecting previously unselected package python-wheel.
Preparing to unpack .../python-wheel_0.29.0-1_all.deb ...
Unpacking python-wheel (0.29.0-1) ...
Selecting previously unselected package rename.
Preparing to unpack .../archives/rename_0.20-4_all.deb ...
Unpacking rename (0.20-4) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Setting up libatm1:amd64 (1:2.5.1-1.5) ...
Setting up libmnl0:amd64 (1.0.3-5) ...
Setting up libgdbm3:amd64 (1.8.3-13.1) ...
Setting up perl-modules-5.22 (5.22.1-9ubuntu0.2) ...
Setting up libperl5.22:amd64 (5.22.1-9ubuntu0.2) ...
Setting up perl (5.22.1-9ubuntu0.2) ...
update-alternatives: using /usr/bin/prename to provide /usr/bin/rename (rename) in auto mode
Setting up libffi6:amd64 (3.2.1-4) ...
Setting up libpython2.7-stdlib:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Setting up python2.7 (2.7.12-1ubuntu0~16.04.3) ...
Setting up libpython-stdlib:amd64 (2.7.12-1~16.04) ...
Setting up python (2.7.12-1~16.04) ...
Setting up libgmp10:amd64 (2:6.1.0+dfsg-2) ...
Setting up libmpfr4:amd64 (3.1.4-1) ...
Setting up libmpc3:amd64 (1.0.3-1) ...
Setting up bzip2 (1.0.6-8) ...
Setting up iproute2 (4.3.0-1ubuntu3.16.04.3) ...
Setting up ifupdown (0.8.10ubuntu1.2) ...
Creating /etc/network/interfaces.
Setting up libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1.10) ...
Setting up libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1.10) ...
Setting up isc-dhcp-client (4.3.3-5ubuntu12.10) ...
Setting up isc-dhcp-common (4.3.3-5ubuntu12.10) ...
Setting up libxtables11:amd64 (1.6.0-2ubuntu3) ...
Setting up netbase (5.3) ...
Setting up openssl (1.0.2g-1ubuntu4.11) ...
Setting up ca-certificates (20170717~16.04.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
Setting up manpages (4.04-2) ...
Setting up binutils (2.26.1-1ubuntu1~16.04.6) ...
Setting up libc-dev-bin (2.23-0ubuntu10) ...
Setting up linux-libc-dev:amd64 (4.4.0-119.143) ...
Setting up libc6-dev:amd64 (2.23-0ubuntu10) ...
Setting up libisl15:amd64 (0.16.1-1) ...
Setting up cpp-5 (5.4.0-6ubuntu1~16.04.9) ...
Setting up cpp (4:5.3.1-1ubuntu1) ...
Setting up libcc1-0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libgomp1:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libitm1:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libatomic1:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libasan2:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up liblsan0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libtsan0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libubsan0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libcilkrts5:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libmpx0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libquadmath0:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up libgcc-5-dev:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up gcc-5 (5.4.0-6ubuntu1~16.04.9) ...
Setting up gcc (4:5.3.1-1ubuntu1) ...
Setting up libstdc++-5-dev:amd64 (5.4.0-6ubuntu1~16.04.9) ...
Setting up g++-5 (5.4.0-6ubuntu1~16.04.9) ...
Setting up g++ (4:5.3.1-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up make (4.1-6) ...
Setting up libdpkg-perl (1.18.4ubuntu1.4) ...
Setting up xz-utils (5.1.1alpha+20120614-2ubuntu2) ...
update-alternatives: using /usr/bin/xz to provide /usr/bin/lzma (lzma) in auto mode
Setting up patch (2.7.5-1ubuntu0.16.04.1) ...
Setting up dpkg-dev (1.18.4ubuntu1.4) ...
Setting up build-essential (12.1ubuntu2) ...
Setting up libfakeroot:amd64 (1.20.2-1ubuntu1) ...
Setting up fakeroot (1.20.2-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.03-1) ...
Setting up libalgorithm-diff-xs-perl (0.04-4build1) ...
Setting up libalgorithm-merge-perl (0.08-3) ...
Setting up libexpat1-dev:amd64 (2.1.0-7ubuntu0.16.04.3) ...
Setting up libfile-fcntllock-perl (0.22-3) ...
Setting up libpython2.7:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Setting up libpython2.7-dev:amd64 (2.7.12-1ubuntu0~16.04.3) ...
Setting up libpython-dev:amd64 (2.7.12-1~16.04) ...
Setting up libpython-all-dev:amd64 (2.7.12-1~16.04) ...
Setting up manpages-dev (4.04-2) ...
Setting up python-all (2.7.12-1~16.04) ...
Setting up python2.7-dev (2.7.12-1ubuntu0~16.04.3) ...
Setting up python-dev (2.7.12-1~16.04) ...
Setting up python-all-dev (2.7.12-1~16.04) ...
Setting up python-pip-whl (8.1.1-2ubuntu0.4) ...
Setting up python-pip (8.1.1-2ubuntu0.4) ...
Setting up python-pkg-resources (20.7.0-1) ...
Setting up python-setuptools (20.7.0-1) ...
Setting up python-wheel (0.29.0-1) ...
Setting up rename (0.20-4) ...
update-alternatives: using /usr/bin/file-rename to provide /usr/bin/rename (rename) in auto mode
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ca-certificates (20170717~16.04.1) ...
Updating certificates in /etc/ssl/certs...
148 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
Removing intermediate container 73b4532cc292
 ---> e5736d40d355
Step 7/13 : WORKDIR /home/dck1
Removing intermediate container a30c13db876e
 ---> 915a550e0913
Step 8/13 : COPY /media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI /home/dck1
COPY failed: stat /var/lib/docker/tmp/docker-builder976552389/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI: no such file or directory
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
[sudo] password for dhankar: 
Sending build context to Docker daemon  1.862MB
Step 1/13 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/13 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/13 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/13 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/13 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/13 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/13 : WORKDIR /usr/src/app
Removing intermediate container 4cad66d8bf7a
 ---> 30f3aa605e5e
Step 8/13 : COPY requirements.txt ./
 ---> f460bb313bd8
Step 9/13 : RUN pip install --no-cache-dir -r requirements.txt
 ---> Running in 8dad44dceddd
Collecting bokeh==0.12.13 (from -r requirements.txt (line 1))
  Downloading bokeh-0.12.13.tar.gz (15.4MB)
^C
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/13 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/13 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/13 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/13 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/13 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/13 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/13 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 30f3aa605e5e
Step 8/13 : COPY requirements.txt ./
 ---> a1906bf9cd7b
Step 9/13 : RUN pip install --no-cache-dir -r requirements.txt
 ---> Running in 67c7d9b8a98f
Collecting certifi==2017.11.5 (from -r requirements.txt (line 1))
  Downloading certifi-2017.11.5-py2.py3-none-any.whl (330kB)
Collecting chardet==3.0.4 (from -r requirements.txt (line 2))
  Downloading chardet-3.0.4-py2.py3-none-any.whl (133kB)
Collecting dj-database-url==0.4.2 (from -r requirements.txt (line 3))
  Downloading dj_database_url-0.4.2-py2.py3-none-any.whl
Collecting dj-static==0.0.6 (from -r requirements.txt (line 4))
  Downloading dj-static-0.0.6.tar.gz
Collecting Django==1.11 (from -r requirements.txt (line 5))
  Downloading Django-1.11-py2.py3-none-any.whl (6.9MB)
Collecting django-crispy-forms==1.7.0 (from -r requirements.txt (line 6))
  Downloading django_crispy_forms-1.7.0-py2.py3-none-any.whl (104kB)
Collecting django-toolbelt==0.0.1 (from -r requirements.txt (line 7))
  Downloading django-toolbelt-0.0.1.tar.gz
Collecting djangorestframework==3.7.3 (from -r requirements.txt (line 8))
  Downloading djangorestframework-3.7.3-py2.py3-none-any.whl (1.5MB)
Collecting gunicorn==19.7.1 (from -r requirements.txt (line 9))
  Downloading gunicorn-19.7.1-py2.py3-none-any.whl (111kB)
Collecting idna==2.6 (from -r requirements.txt (line 10))
  Downloading idna-2.6-py2.py3-none-any.whl (56kB)
Collecting Jinja2==2.10 (from -r requirements.txt (line 11))
  Downloading Jinja2-2.10-py2.py3-none-any.whl (126kB)
Collecting lml==0.0.1 (from -r requirements.txt (line 12))
  Downloading lml-0.0.1-py2.py3-none-any.whl
Collecting MarkupSafe==1.0 (from -r requirements.txt (line 13))
  Downloading MarkupSafe-1.0.tar.gz
Collecting numpy==1.13.3 (from -r requirements.txt (line 14))
  Downloading numpy-1.13.3-cp27-cp27mu-manylinux1_x86_64.whl (16.6MB)
Collecting opencv-python==3.4.0.12 (from -r requirements.txt (line 15))
  Downloading opencv_python-3.4.0.12-cp27-cp27mu-manylinux1_x86_64.whl (24.9MB)
Collecting pandas==0.21.0 (from -r requirements.txt (line 16))
  Downloading pandas-0.21.0-cp27-cp27mu-manylinux1_x86_64.whl (24.3MB)
Collecting Pillow==4.3.0 (from -r requirements.txt (line 17))
  Downloading Pillow-4.3.0-cp27-cp27mu-manylinux1_x86_64.whl (5.8MB)
Collecting psycopg2==2.7.3.2 (from -r requirements.txt (line 18))
  Downloading psycopg2-2.7.3.2-cp27-cp27mu-manylinux1_x86_64.whl (2.7MB)
Collecting python-dateutil==2.6.1 (from -r requirements.txt (line 19))
  Downloading python_dateutil-2.6.1-py2.py3-none-any.whl (194kB)
Collecting pytz==2017.3 (from -r requirements.txt (line 20))
  Downloading pytz-2017.3-py2.py3-none-any.whl (511kB)
Collecting PyYAML==3.12 (from -r requirements.txt (line 21))
  Downloading PyYAML-3.12.tar.gz (253kB)
Collecting requests==2.18.4 (from -r requirements.txt (line 22))
  Downloading requests-2.18.4-py2.py3-none-any.whl (88kB)
Collecting six==1.11.0 (from -r requirements.txt (line 23))
  Downloading six-1.11.0-py2.py3-none-any.whl
Collecting static3==0.7.0 (from -r requirements.txt (line 24))
  Downloading static3-0.7.0.tar.gz
Collecting texttable==1.1.1 (from -r requirements.txt (line 25))
  Downloading texttable-1.1.1.tar.gz
Collecting tornado==4.5.2 (from -r requirements.txt (line 26))
  Downloading tornado-4.5.2.tar.gz (483kB)
Collecting urllib3==1.22 (from -r requirements.txt (line 27))
  Downloading urllib3-1.22-py2.py3-none-any.whl (132kB)
Collecting whitenoise==3.3.1 (from -r requirements.txt (line 28))
  Downloading whitenoise-3.3.1-py2.py3-none-any.whl
Collecting xlrd==1.1.0 (from -r requirements.txt (line 29))
  Downloading xlrd-1.1.0-py2.py3-none-any.whl (108kB)
Collecting xlwt==1.3.0 (from -r requirements.txt (line 30))
  Downloading xlwt-1.3.0-py2.py3-none-any.whl (99kB)
Collecting olefile (from Pillow==4.3.0->-r requirements.txt (line 17))
  Downloading olefile-0.45.1.zip (112kB)
Collecting singledispatch (from tornado==4.5.2->-r requirements.txt (line 26))
  Downloading singledispatch-3.4.0.3-py2.py3-none-any.whl
Collecting backports_abc>=0.4 (from tornado==4.5.2->-r requirements.txt (line 26))
  Downloading backports_abc-0.5-py2.py3-none-any.whl
Installing collected packages: certifi, chardet, dj-database-url, static3, dj-static, pytz, Django, django-crispy-forms, psycopg2, gunicorn, django-toolbelt, djangorestframework, idna, MarkupSafe, Jinja2, lml, numpy, opencv-python, six, python-dateutil, pandas, olefile, Pillow, PyYAML, urllib3, requests, texttable, singledispatch, backports-abc, tornado, whitenoise, xlrd, xlwt
  Running setup.py install for static3: started
    Running setup.py install for static3: finished with status 'done'
  Running setup.py install for dj-static: started
    Running setup.py install for dj-static: finished with status 'done'
  Running setup.py install for django-toolbelt: started
    Running setup.py install for django-toolbelt: finished with status 'done'
  Running setup.py install for MarkupSafe: started
    Running setup.py install for MarkupSafe: finished with status 'done'
  Running setup.py install for olefile: started
    Running setup.py install for olefile: finished with status 'done'
  Running setup.py install for PyYAML: started
    Running setup.py install for PyYAML: finished with status 'done'
  Running setup.py install for texttable: started
    Running setup.py install for texttable: finished with status 'done'
  Running setup.py install for tornado: started
    Running setup.py install for tornado: finished with status 'done'
Successfully installed Django-1.11 Jinja2-2.10 MarkupSafe-1.0 Pillow-4.3.0 PyYAML-3.12 backports-abc-0.5 certifi-2017.11.5 chardet-3.0.4 dj-database-url-0.4.2 dj-static-0.0.6 django-crispy-forms-1.7.0 django-toolbelt-0.0.1 djangorestframework-3.7.3 gunicorn-19.7.1 idna-2.6 lml-0.0.1 numpy-1.13.3 olefile-0.45.1 opencv-python-3.4.0.12 pandas-0.21.0 psycopg2-2.7.3.2 python-dateutil-2.6.1 pytz-2017.3 requests-2.18.4 singledispatch-3.4.0.3 six-1.11.0 static3-0.7.0 texttable-1.1.1 tornado-4.5.2 urllib3-1.22 whitenoise-3.3.1 xlrd-1.1.0 xlwt-1.3.0
You are using pip version 8.1.1, however version 10.0.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Removing intermediate container 67c7d9b8a98f
 ---> 92c1a55b901d
Step 10/13 : RUN echo "pip installed requirements.txt..."
 ---> Running in ca45360c8474
pip installed requirements.txt...
Removing intermediate container ca45360c8474
 ---> 3a07453ee15f
Step 11/13 : EXPOSE 8000
 ---> Running in 2ba7cda0d24c
Removing intermediate container 2ba7cda0d24c
 ---> 6c5f9deadaa9
Step 12/13 : RUN python manage.py migrate
 ---> Running in d5cb528230b7
python: can't open file 'manage.py': [Errno 2] No such file or directory
The command '/bin/sh -c python manage.py migrate' returned a non-zero code: 2
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/12 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/12 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/12 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/12 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/12 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/12 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/12 : WORKDIR /usr/src/app
 ---> Using cache
 ---> 30f3aa605e5e
Step 8/12 : COPY requirements.txt ./
 ---> Using cache
 ---> a1906bf9cd7b
Step 9/12 : RUN pip install --no-cache-dir -r requirements.txt
 ---> Using cache
 ---> 92c1a55b901d
Step 10/12 : RUN echo "pip installed requirements.txt..."
 ---> Using cache
 ---> 3a07453ee15f
Step 11/12 : EXPOSE 8000
 ---> Using cache
 ---> 6c5f9deadaa9
Step 12/12 : CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
 ---> Running in 57d08f579c80
Removing intermediate container 57d08f579c80
 ---> 7e7097df2185
Successfully built 7e7097df2185
Successfully tagged ddrohit/dck1:latest
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ docker run -p 8888:8000 --name dck1 ddrohit/dck1
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.35/containers/create?name=dck1: dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker run -p 8888:8000 --name dck1 ddrohit/dck1
python: can't open file 'manage.py': [Errno 2] No such file or directory
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/13 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/13 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/13 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/13 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/13 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/13 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/13 : WORKDIR ./
Removing intermediate container 934c23f4a52b
 ---> d69540b3ed6f
Step 8/13 : COPY requirements.txt ./
 ---> 2720b3ff737a
Step 9/13 : RUN pip install --no-cache-dir -r requirements.txt
 ---> Running in 93008866b560
Collecting certifi==2017.11.5 (from -r requirements.txt (line 1))
  Downloading certifi-2017.11.5-py2.py3-none-any.whl (330kB)
Collecting chardet==3.0.4 (from -r requirements.txt (line 2))
  Downloading chardet-3.0.4-py2.py3-none-any.whl (133kB)
Collecting dj-database-url==0.4.2 (from -r requirements.txt (line 3))
  Downloading dj_database_url-0.4.2-py2.py3-none-any.whl
Collecting dj-static==0.0.6 (from -r requirements.txt (line 4))
  Downloading dj-static-0.0.6.tar.gz
Collecting Django==1.11 (from -r requirements.txt (line 5))
  Downloading Django-1.11-py2.py3-none-any.whl (6.9MB)
Collecting django-crispy-forms==1.7.0 (from -r requirements.txt (line 6))
  Downloading django_crispy_forms-1.7.0-py2.py3-none-any.whl (104kB)
Collecting django-toolbelt==0.0.1 (from -r requirements.txt (line 7))
  Downloading django-toolbelt-0.0.1.tar.gz
Collecting djangorestframework==3.7.3 (from -r requirements.txt (line 8))
  Downloading djangorestframework-3.7.3-py2.py3-none-any.whl (1.5MB)
Collecting gunicorn==19.7.1 (from -r requirements.txt (line 9))
  Downloading gunicorn-19.7.1-py2.py3-none-any.whl (111kB)
Collecting idna==2.6 (from -r requirements.txt (line 10))
  Downloading idna-2.6-py2.py3-none-any.whl (56kB)
Collecting Jinja2==2.10 (from -r requirements.txt (line 11))
  Downloading Jinja2-2.10-py2.py3-none-any.whl (126kB)
Collecting lml==0.0.1 (from -r requirements.txt (line 12))
  Downloading lml-0.0.1-py2.py3-none-any.whl
Collecting MarkupSafe==1.0 (from -r requirements.txt (line 13))
  Downloading MarkupSafe-1.0.tar.gz
Collecting numpy==1.13.3 (from -r requirements.txt (line 14))
  Downloading numpy-1.13.3-cp27-cp27mu-manylinux1_x86_64.whl (16.6MB)
^C
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/13 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/13 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/13 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/13 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/13 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/13 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/13 : WORKDIR ./
 ---> Using cache
 ---> d69540b3ed6f
Step 8/13 : COPY requirements.txt ./
 ---> Using cache
 ---> 2720b3ff737a
Step 9/13 : RUN pip install -r requirements.txt
 ---> Running in 26633d4b7946
Collecting certifi==2017.11.5 (from -r requirements.txt (line 1))
  Downloading certifi-2017.11.5-py2.py3-none-any.whl (330kB)
Collecting chardet==3.0.4 (from -r requirements.txt (line 2))
  Downloading chardet-3.0.4-py2.py3-none-any.whl (133kB)
Collecting dj-database-url==0.4.2 (from -r requirements.txt (line 3))
  Downloading dj_database_url-0.4.2-py2.py3-none-any.whl
Collecting dj-static==0.0.6 (from -r requirements.txt (line 4))
  Downloading dj-static-0.0.6.tar.gz
Collecting Django==1.11 (from -r requirements.txt (line 5))
  Downloading Django-1.11-py2.py3-none-any.whl (6.9MB)
Collecting django-crispy-forms==1.7.0 (from -r requirements.txt (line 6))
  Downloading django_crispy_forms-1.7.0-py2.py3-none-any.whl (104kB)
Collecting django-toolbelt==0.0.1 (from -r requirements.txt (line 7))
  Downloading django-toolbelt-0.0.1.tar.gz
Collecting djangorestframework==3.7.3 (from -r requirements.txt (line 8))
  Downloading djangorestframework-3.7.3-py2.py3-none-any.whl (1.5MB)
Collecting gunicorn==19.7.1 (from -r requirements.txt (line 9))
  Downloading gunicorn-19.7.1-py2.py3-none-any.whl (111kB)
Collecting idna==2.6 (from -r requirements.txt (line 10))
  Downloading idna-2.6-py2.py3-none-any.whl (56kB)
Collecting Jinja2==2.10 (from -r requirements.txt (line 11))
  Downloading Jinja2-2.10-py2.py3-none-any.whl (126kB)
Collecting lml==0.0.1 (from -r requirements.txt (line 12))
  Downloading lml-0.0.1-py2.py3-none-any.whl
Collecting MarkupSafe==1.0 (from -r requirements.txt (line 13))
  Downloading MarkupSafe-1.0.tar.gz
Collecting numpy==1.13.3 (from -r requirements.txt (line 14))
  Downloading numpy-1.13.3-cp27-cp27mu-manylinux1_x86_64.whl (16.6MB)
Collecting opencv-python==3.4.0.12 (from -r requirements.txt (line 15))
  Downloading opencv_python-3.4.0.12-cp27-cp27mu-manylinux1_x86_64.whl (24.9MB)
Collecting pandas==0.21.0 (from -r requirements.txt (line 16))
  Downloading pandas-0.21.0-cp27-cp27mu-manylinux1_x86_64.whl (24.3MB)
Collecting Pillow==4.3.0 (from -r requirements.txt (line 17))
  Downloading Pillow-4.3.0-cp27-cp27mu-manylinux1_x86_64.whl (5.8MB)
Collecting psycopg2==2.7.3.2 (from -r requirements.txt (line 18))
  Downloading psycopg2-2.7.3.2-cp27-cp27mu-manylinux1_x86_64.whl (2.7MB)
Collecting python-dateutil==2.6.1 (from -r requirements.txt (line 19))
  Downloading python_dateutil-2.6.1-py2.py3-none-any.whl (194kB)
Collecting pytz==2017.3 (from -r requirements.txt (line 20))
  Downloading pytz-2017.3-py2.py3-none-any.whl (511kB)
Collecting PyYAML==3.12 (from -r requirements.txt (line 21))
  Downloading PyYAML-3.12.tar.gz (253kB)
Collecting requests==2.18.4 (from -r requirements.txt (line 22))
  Downloading requests-2.18.4-py2.py3-none-any.whl (88kB)
Collecting six==1.11.0 (from -r requirements.txt (line 23))
  Downloading six-1.11.0-py2.py3-none-any.whl
Collecting static3==0.7.0 (from -r requirements.txt (line 24))
  Downloading static3-0.7.0.tar.gz
Collecting texttable==1.1.1 (from -r requirements.txt (line 25))
  Downloading texttable-1.1.1.tar.gz
Collecting tornado==4.5.2 (from -r requirements.txt (line 26))
  Downloading tornado-4.5.2.tar.gz (483kB)
Collecting urllib3==1.22 (from -r requirements.txt (line 27))
  Downloading urllib3-1.22-py2.py3-none-any.whl (132kB)
Collecting whitenoise==3.3.1 (from -r requirements.txt (line 28))
  Downloading whitenoise-3.3.1-py2.py3-none-any.whl
Collecting xlrd==1.1.0 (from -r requirements.txt (line 29))
  Downloading xlrd-1.1.0-py2.py3-none-any.whl (108kB)
Collecting xlwt==1.3.0 (from -r requirements.txt (line 30))
  Downloading xlwt-1.3.0-py2.py3-none-any.whl (99kB)
Collecting olefile (from Pillow==4.3.0->-r requirements.txt (line 17))
  Downloading olefile-0.45.1.zip (112kB)
Collecting singledispatch (from tornado==4.5.2->-r requirements.txt (line 26))
  Downloading singledispatch-3.4.0.3-py2.py3-none-any.whl
Collecting backports_abc>=0.4 (from tornado==4.5.2->-r requirements.txt (line 26))
  Downloading backports_abc-0.5-py2.py3-none-any.whl
Building wheels for collected packages: dj-static, django-toolbelt, MarkupSafe, PyYAML, static3, texttable, tornado, olefile
  Running setup.py bdist_wheel for dj-static: started
  Running setup.py bdist_wheel for dj-static: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/b1/84/4e/fb5706a7cfa7603abc69cc5343b4c3da7f6495f2362e7341cb
  Running setup.py bdist_wheel for django-toolbelt: started
  Running setup.py bdist_wheel for django-toolbelt: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/28/50/35/d9bfc969dc1266fd9c38cd57472e67626b968e5e469780af0a
  Running setup.py bdist_wheel for MarkupSafe: started
  Running setup.py bdist_wheel for MarkupSafe: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/88/a7/30/e39a54a87bcbe25308fa3ca64e8ddc75d9b3e5afa21ee32d57
  Running setup.py bdist_wheel for PyYAML: started
  Running setup.py bdist_wheel for PyYAML: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/2c/f7/79/13f3a12cd723892437c0cfbde1230ab4d82947ff7b3839a4fc
  Running setup.py bdist_wheel for static3: started
  Running setup.py bdist_wheel for static3: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/3b/36/04/bb7140607a5fc479d180ba4eff9ed11fe141588eb24d562c60
  Running setup.py bdist_wheel for texttable: started
  Running setup.py bdist_wheel for texttable: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/17/fd/d8/46366c309918d2a7e7d44782d6e7e8a1b05c071d58a56fd605
  Running setup.py bdist_wheel for tornado: started
  Running setup.py bdist_wheel for tornado: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/b3/47/3a/96e12476829cb196adabc879fedb72f1bb2c8613b6961e78e7
  Running setup.py bdist_wheel for olefile: started
  Running setup.py bdist_wheel for olefile: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/75/f2/18/9f073aab5b308aaccec50c17d4afb33dffc3265254e7962d67
Successfully built dj-static django-toolbelt MarkupSafe PyYAML static3 texttable tornado olefile
Installing collected packages: certifi, chardet, dj-database-url, static3, dj-static, pytz, Django, django-crispy-forms, psycopg2, gunicorn, django-toolbelt, djangorestframework, idna, MarkupSafe, Jinja2, lml, numpy, opencv-python, six, python-dateutil, pandas, olefile, Pillow, PyYAML, urllib3, requests, texttable, singledispatch, backports-abc, tornado, whitenoise, xlrd, xlwt
Successfully installed Django-1.11 Jinja2-2.10 MarkupSafe-1.0 Pillow-4.3.0 PyYAML-3.12 backports-abc-0.5 certifi-2017.11.5 chardet-3.0.4 dj-database-url-0.4.2 dj-static-0.0.6 django-crispy-forms-1.7.0 django-toolbelt-0.0.1 djangorestframework-3.7.3 gunicorn-19.7.1 idna-2.6 lml-0.0.1 numpy-1.13.3 olefile-0.45.1 opencv-python-3.4.0.12 pandas-0.21.0 psycopg2-2.7.3.2 python-dateutil-2.6.1 pytz-2017.3 requests-2.18.4 singledispatch-3.4.0.3 six-1.11.0 static3-0.7.0 texttable-1.1.1 tornado-4.5.2 urllib3-1.22 whitenoise-3.3.1 xlrd-1.1.0 xlwt-1.3.0
You are using pip version 8.1.1, however version 10.0.0 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
Removing intermediate container 26633d4b7946
 ---> 577b7b8ad93a
Step 10/13 : RUN echo "pip installed requirements.txt..."
 ---> Running in 6a0e5bc612e1
pip installed requirements.txt...
Removing intermediate container 6a0e5bc612e1
 ---> 9781fbd0c622
Step 11/13 : EXPOSE 8000
 ---> Running in 2f24d451fc48
Removing intermediate container 2f24d451fc48
 ---> 4b29563e9f24
Step 12/13 : RUN python manage.py migrate
 ---> Running in 7c3184b1dcc4
python: can't open file 'manage.py': [Errno 2] No such file or directory
The command '/bin/sh -c python manage.py migrate' returned a non-zero code: 2
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/14 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/14 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/14 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/14 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/14 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/14 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/14 : WORKDIR ./
 ---> Using cache
 ---> d69540b3ed6f
Step 8/14 : COPY requirements.txt ./
 ---> Using cache
 ---> 2720b3ff737a
Step 9/14 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> 577b7b8ad93a
Step 10/14 : RUN echo "pip installed requirements.txt..."
 ---> Using cache
 ---> 9781fbd0c622
Step 11/14 : EXPOSE 8000
 ---> Using cache
 ---> 4b29563e9f24
Step 12/14 : RUN echo pwd
 ---> Running in ed0ed25e9dd3
pwd
Removing intermediate container ed0ed25e9dd3
 ---> bc13b1f94fb2
Step 13/14 : RUN python manage.py migrate
 ---> Running in fa2601fb8002
python: can't open file 'manage.py': [Errno 2] No such file or directory
The command '/bin/sh -c python manage.py migrate' returned a non-zero code: 2
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/14 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/14 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/14 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/14 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/14 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/14 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/14 : WORKDIR ./
 ---> Using cache
 ---> d69540b3ed6f
Step 8/14 : COPY requirements.txt ./
 ---> Using cache
 ---> 2720b3ff737a
Step 9/14 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> 577b7b8ad93a
Step 10/14 : RUN echo "pip installed requirements.txt..."
 ---> Using cache
 ---> 9781fbd0c622
Step 11/14 : EXPOSE 8000
 ---> Using cache
 ---> 4b29563e9f24
Step 12/14 : RUN pwd
 ---> Running in c254b6e1ecdf
/
Removing intermediate container c254b6e1ecdf
 ---> 9f5585537ce2
Step 13/14 : RUN python manage.py migrate
 ---> Running in 2114652beb42
python: can't open file 'manage.py': [Errno 2] No such file or directory
The command '/bin/sh -c python manage.py migrate' returned a non-zero code: 2
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/15 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/15 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/15 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/15 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/15 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/15 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/15 : WORKDIR ./
 ---> Using cache
 ---> d69540b3ed6f
Step 8/15 : COPY requirements.txt ./
 ---> Using cache
 ---> 2720b3ff737a
Step 9/15 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> 577b7b8ad93a
Step 10/15 : RUN echo "pip installed requirements.txt..."
 ---> Using cache
 ---> 9781fbd0c622
Step 11/15 : EXPOSE 8000
 ---> Using cache
 ---> 4b29563e9f24
Step 12/15 : RUN pwd
 ---> Using cache
 ---> 9f5585537ce2
Step 13/15 : RUN ls
 ---> Running in 85a4ffc05446
bin
boot
dev
etc
home
lib
lib64
media
mnt
opt
proc
requirements.txt
root
run
sbin
srv
sys
tmp
usr
var
Removing intermediate container 85a4ffc05446
 ---> 754fc165415b
Step 14/15 : RUN python manage.py migrate
 ---> Running in 1908f31f6727
python: can't open file 'manage.py': [Errno 2] No such file or directory
The command '/bin/sh -c python manage.py migrate' returned a non-zero code: 2
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
[sudo] password for dhankar: 
Sorry, try again.
[sudo] password for dhankar: 
Sending build context to Docker daemon  1.861MB
Step 1/16 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/16 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/16 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/16 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/16 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/16 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/16 : WORKDIR ./
 ---> Using cache
 ---> d69540b3ed6f
Step 8/16 : COPY requirements.txt ./
 ---> Using cache
 ---> 2720b3ff737a
Step 9/16 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> 577b7b8ad93a
Step 10/16 : RUN echo "pip installed requirements.txt..."
 ---> Using cache
 ---> 9781fbd0c622
Step 11/16 : EXPOSE 8000
 ---> Using cache
 ---> 4b29563e9f24
Step 12/16 : RUN pwd
 ---> Using cache
 ---> 9f5585537ce2
Step 13/16 : RUN ls
 ---> Using cache
 ---> 754fc165415b
Step 14/16 : RUN find manage.py
 ---> Running in 6229b5c2a1e2
find: 'manage.py': No such file or directory
The command '/bin/sh -c find manage.py' returned a non-zero code: 1
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker build -t ddrohit/dck1 .
Sending build context to Docker daemon  1.861MB
Step 1/17 : FROM ubuntu:xenial
 ---> c9d990395902
Step 2/17 : RUN apt-get update
 ---> Using cache
 ---> 6bc0d0de6516
Step 3/17 : RUN echo "updated the package manager..."
 ---> Using cache
 ---> 2fe01c0ad13d
Step 4/17 : RUN apt-get install -y python3 # install python3
 ---> Using cache
 ---> cde60d61973a
Step 5/17 : RUN echo "installed python3..."
 ---> Using cache
 ---> 11681c422810
Step 6/17 : RUN apt-get install -y python-pip python-dev build-essential
 ---> Using cache
 ---> e5736d40d355
Step 7/17 : WORKDIR ./
 ---> Using cache
 ---> d69540b3ed6f
Step 8/17 : COPY requirements.txt ./
 ---> Using cache
 ---> 2720b3ff737a
Step 9/17 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> 577b7b8ad93a
Step 10/17 : RUN echo "pip installed requirements.txt..."
 ---> Using cache
 ---> 9781fbd0c622
Step 11/17 : EXPOSE 8000
 ---> Using cache
 ---> 4b29563e9f24
Step 12/17 : RUN pwd
 ---> Using cache
 ---> 9f5585537ce2
Step 13/17 : RUN ls
 ---> Using cache
 ---> 754fc165415b
Step 14/17 : RUN find requirements.txt
 ---> Running in b3a82034046f
requirements.txt
Removing intermediate container b3a82034046f
 ---> 0d81a8d81b4f
Step 15/17 : RUN find manage.py
 ---> Running in c9f4231ca79f
find: 'manage.py': No such file or directory
The command '/bin/sh -c find manage.py' returned a non-zero code: 1
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                         PORTS               NAMES
c9f4231ca79f        0d81a8d81b4f                       "/bin/sh -c 'find ma…"   12 minutes ago      Exited (1) 12 minutes ago                          upbeat_murdock
6229b5c2a1e2        754fc165415b                       "/bin/sh -c 'find ma…"   14 minutes ago      Exited (1) 14 minutes ago                          mystifying_jackson
1908f31f6727        754fc165415b                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       modest_leakey
2114652beb42        9f5585537ce2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       pedantic_shirley
fa2601fb8002        bc13b1f94fb2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       awesome_hodgkin
7c3184b1dcc4        4b29563e9f24                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       affectionate_mahavira
2c4026fa625a        ddrohit/dck1                       "python manage.py ru…"   About an hour ago   Exited (2) About an hour ago                       dck1
d5cb528230b7        6c5f9deadaa9                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       sad_cori
c22d41606b1b        hello-world                        "/hello"                 7 hours ago         Exited (0) 7 hours ago                             condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                             upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                             kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                             focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              0d81a8d81b4f        12 minutes ago      855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker

Usage:	docker COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default "/home/dhankar/.docker")
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket(s) to connect to
  -l, --log-level string   Set the logging level ("debug"|"info"|"warn"|"error"|"fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/home/dhankar/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/home/dhankar/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/home/dhankar/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  config      Manage Docker configs
  container   Manage containers
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  trust       Manage trust on Docker images (experimental)
  volume      Manage volumes

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker COMMAND --help' for more information on a command.
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              0d81a8d81b4f        17 minutes ago      855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f 0d81a8d81b4f
Deleted: sha256:0d81a8d81b4f1dd5dd20bc692c0439f8342acbfd2e21c10461f0c98058ec7252
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              754fc165415b        About an hour ago   855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f 754fc165415b
Deleted: sha256:754fc165415ba8ff2443b6ab3bf50ee5ebca53eaffd5c22b24d5c53397027aac
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              9f5585537ce2        About an hour ago   855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ### Need to REMOVE Containers - Not IMAGES 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                         PORTS               NAMES
c9f4231ca79f        0d81a8d81b4f                       "/bin/sh -c 'find ma…"   20 minutes ago      Exited (1) 20 minutes ago                          upbeat_murdock
6229b5c2a1e2        754fc165415b                       "/bin/sh -c 'find ma…"   21 minutes ago      Exited (1) 21 minutes ago                          mystifying_jackson
1908f31f6727        754fc165415b                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       modest_leakey
2114652beb42        9f5585537ce2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       pedantic_shirley
fa2601fb8002        bc13b1f94fb2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       awesome_hodgkin
7c3184b1dcc4        4b29563e9f24                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       affectionate_mahavira
2c4026fa625a        ddrohit/dck1                       "python manage.py ru…"   About an hour ago   Exited (2) About an hour ago                       dck1
d5cb528230b7        6c5f9deadaa9                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       sad_cori
c22d41606b1b        hello-world                        "/hello"                 7 hours ago         Exited (0) 7 hours ago                             condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                             upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                             kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                             focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rm c9f4231ca79f
c9f4231ca79f
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ #sudo docker rm c9f4231ca79f ## rm NOT rm1 AND CONTAINER ID
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rm 6229b5c2a1e2
6229b5c2a1e2
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                         PORTS               NAMES
1908f31f6727        754fc165415b                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       modest_leakey
2114652beb42        9f5585537ce2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       pedantic_shirley
fa2601fb8002        bc13b1f94fb2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       awesome_hodgkin
7c3184b1dcc4        4b29563e9f24                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       affectionate_mahavira
2c4026fa625a        ddrohit/dck1                       "python manage.py ru…"   About an hour ago   Exited (2) About an hour ago                       dck1
d5cb528230b7        6c5f9deadaa9                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       sad_cori
c22d41606b1b        hello-world                        "/hello"                 7 hours ago         Exited (0) 7 hours ago                             condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                             upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                             kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                             focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rm 1908f31f6727
1908f31f6727
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              9f5585537ce2        About an hour ago   855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rm d5cb528230b7 ## name == ddrohit/dck1
d5cb528230b7
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              9f5585537ce2        About an hour ago   855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                         PORTS               NAMES
2114652beb42        9f5585537ce2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       pedantic_shirley
fa2601fb8002        bc13b1f94fb2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       awesome_hodgkin
7c3184b1dcc4        4b29563e9f24                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       affectionate_mahavira
2c4026fa625a        ddrohit/dck1                       "python manage.py ru…"   About an hour ago   Exited (2) About an hour ago                       dck1
c22d41606b1b        hello-world                        "/hello"                 7 hours ago         Exited (0) 7 hours ago                             condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                             upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                             kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                             focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rm 2c4026fa625a ## name == ddrohit/dck1
2c4026fa625a
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker ps -a
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS                         PORTS               NAMES
2114652beb42        9f5585537ce2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       pedantic_shirley
fa2601fb8002        bc13b1f94fb2                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       awesome_hodgkin
7c3184b1dcc4        4b29563e9f24                       "/bin/sh -c 'python …"   About an hour ago   Exited (2) About an hour ago                       affectionate_mahavira
c22d41606b1b        hello-world                        "/hello"                 7 hours ago         Exited (0) 7 hours ago                             condescending_hoover
44ada9c5e1d3        dhankar/tensorflow-serving-devel   "/bin/bash"              11 days ago         Exited (0) 11 days ago                             upbeat_mccarthy
fc107394f848        a01b86204c33                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           stupefied_meitner
8f5ea764d4b7        dd7ddf7eb0f1                       "bash"                   3 weeks ago         Exited (127) 3 weeks ago                           sleepy_northcutt
82d279189cbf        ubuntu                             "bash"                   3 weeks ago         Exited (0) 3 weeks ago                             kind_hugle
91761424a8d7        hello-world                        "/hello"                 3 weeks ago         Exited (0) 3 weeks ago                             focused_chatterjee
74bc5baaad36        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             gifted_knuth
5adb571f280a        c52dc19f7cb8                       "/bin/sh -c /start.sh"   3 weeks ago         Exited (1) 3 weeks ago                             nostalgic_kare
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              9f5585537ce2        About an hour ago   855MB
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f 9f5585537ce2
Deleted: sha256:9f5585537ce22a99778d930e9dfde006b0cef92b8a44c2cdc07709c6bf540135
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              bc13b1f94fb2        About an hour ago   855MB
ddrohit/dck1                       latest              7e7097df2185        About an hour ago   769MB
<none>                             <none>              f460bb313bd8        About an hour ago   448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ## Not sure probably- DELETE Containers before IMAGES
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f bc13b1f94fb2
Deleted: sha256:bc13b1f94fb2fe7f23e0e0d643cdd8d33ede04f848dbf53932f0a1e37eabcad5
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f 7e7097df2185
Untagged: ddrohit/dck1:latest
Deleted: sha256:7e7097df2185188435be37b4ca932550e9d4565e1a57a3cb35a9ff5a97411452
Deleted: sha256:6c5f9deadaa9a47ae931fbf0e739f6f37236f6671faa42f6d2ff7c6cda659ff6
Deleted: sha256:3a07453ee15f02e9aad6b95d190d8c86c8acb6384eaa610abde4e6e3af0f4590
Deleted: sha256:92c1a55b901d5046d0982e474cfadd6fa12cd1ca7ebb4bb506f73059deae825e
Deleted: sha256:3b8acc6b8bf26be8692f4d3688e8e88341cb0995cf77ec701ddf5f65acd1b911
Deleted: sha256:a1906bf9cd7bca43ee594eae4f4164fee53b2740719cf3e1dc2235334524d389
Deleted: sha256:1c7e536c0c9783f7e6efab289b28b6595c9fdf0b9181ebfd1e8ae84c6c862184
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
<none>                             <none>              4b29563e9f24        About an hour ago   855MB
<none>                             <none>              f460bb313bd8        2 hours ago         448MB
<none>                             <none>              915a550e0913        2 hours ago         448MB
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f 4b29563e9f24
Deleted: sha256:4b29563e9f24d50399af287ed341299cec6997afdd604b396111fa943b4618dd
Deleted: sha256:9781fbd0c62286e072729c8a88cded056e365d2e083c722bce113407a5546528
Deleted: sha256:577b7b8ad93a1c9588317fcc4c0260a40509f73ad328b50c07cd132c15e5a544
Deleted: sha256:2720b3ff737a8021d1d8de333302bd7dafd7e30affa4f66eeac00040f125be5c
Deleted: sha256:d69540b3ed6f0a626b02b44eb71b584b024e5e864f5328f5706af1dc2ba5a92d
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f f460bb313bd8
Deleted: sha256:f460bb313bd8f0447f44856deb7635f1b66e0e452559a2fbee25a9f6a8b7d455
Deleted: sha256:7e275d15a1c33dc288643da5067cdab8b09b4cd99f048e44e994c217125eb91b
Deleted: sha256:30f3aa605e5ea86292a945aa5bac6a3a507c39b2a77441a15d32cbc6c578c724
Deleted: sha256:d4f54003a15cfd72e1dbaabf94be507c26636c7847e55492323b83ca5088b68d
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker rmi -f 915a550e0913
Deleted: sha256:915a550e091308a0726a36f586cc4bbdcdac658c6011986e13611cf415eb1135
Deleted: sha256:5d6a225a0279eb9c60b14f628f7e3ddcfdc9a2d19e8cbe05403f646e77047f1a
Deleted: sha256:e5736d40d355ca31b966f35cd34d01742dd370239f6e8017e7f4691dd3120fa9
Deleted: sha256:11681c4228102818c7bec5aa8591097a956585fe0dfed3ad509f7ed9086b76bd
Deleted: sha256:cde60d61973aa7f3b9d1c4ad0e7c086a0c00a6ac40b360d937da24e36f0e31ae
Deleted: sha256:2fe01c0ad13d9aa2cba53ada7f47ab98fd77e4dd8ee8651b83863b86e26a2965
Deleted: sha256:6bc0d0de65169ead3fadff96dcc81a91f15b2032201da675545c3e4dddec0eb5
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ sudo docker images
REPOSITORY                         TAG                 IMAGE ID            CREATED             SIZE
ubuntu                             xenial              c9d990395902        3 days ago          113MB
dhankar/tensorflow-serving-devel   latest              69e7c3fa252a        11 days ago         1.1GB
ubuntu                             16.04               f975c5035748        5 weeks ago         112MB
ubuntu                             latest              f975c5035748        5 weeks ago         112MB
hello-world                        latest              f2a91732366c        4 months ago        1.85kB
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ## Seen above --- IMAGE ID == c9d990395902 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ ## Is the IMAGE ID we are Building upon.
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 
dhankar@dhankar-VPCEB44EN:/media/dhankar/Dhankar_1/a2_18/a2___DC_API/aa___Docker_RESTAPI$ 





### FART --- 16 APR 18 
#

bokeh==0.12.13
certifi==2017.11.5
chardet==3.0.4
dj-database-url==0.4.2
dj-static==0.0.6
Django==1.11
django-crispy-forms==1.7.0
django-toolbelt==0.0.1
djangorestframework==3.7.3
gunicorn==19.7.1
idna==2.6
Jinja2==2.10
lml==0.0.1
MarkupSafe==1.0
numpy==1.13.3
opencv-python==3.4.0.12
pandas==0.21.0
Pillow==4.3.0
psycopg2==2.7.3.2
pyexcel==0.5.6
pyexcel-io==0.5.4
pyexcel-webio==0.1.4
pyexcel-xls==0.5.4
python-dateutil==2.6.1
pytz==2017.3
PyYAML==3.12
requests==2.18.4
six==1.11.0
static3==0.7.0
texttable==1.1.1
tornado==4.5.2
urllib3==1.22
whitenoise==3.3.1
xlrd==1.1.0
xlwt==1.3.0

#
#






### FART -- 16 APR 18 
#
2 options ---
1st/  ceate a base image with Ubuntu Docker iameg as base and then start Django install etc on top of it 
2nd/ create a Django app on top of django image from docker - which should have preinstalled Ubuntu and on top of that ADD Opencv or opencv-python from [with - pip install ]  




### FART below -- not used -- Dockerfile example for Django 
##
FROM ubuntu:16.04
MAINTAINER Hugo Herter

RUN apt-get -y update && apt-get install -y python3-virtualenv virtualenv
RUN virtualenv -p python3 /opt/venv-hellodjango

# Install requirements
ADD requirements.txt /opt/requirements.txt
RUN /opt/venv-hellodjango/bin/pip install -r /opt/requirements.txt

ADD hellodjango /opt/hellodjango
WORKDIR /opt/hellodjango/

EXPOSE 8000
CMD ["/opt/hellodjango/run.sh"]







##
## Source --- https://fmgdata.kinja.com/using-docker-with-conda-environments-1790901398
##

FROM continuumio/miniconda3

# Set the ENTRYPOINT to use bash
# (this is also where you’d set SHELL,
# if your version of docker supports this)
ENTRYPOINT [ “/bin/bash”, “-c” ]

EXPOSE 5000

# Conda supports delegating to pip to install dependencies
# that aren’t available in anaconda or need to be compiled
# for other reasons. In our case, we need psycopg compiled
# with SSL support. These commands install prereqs necessary
# to build psycopg.
RUN apt-get update && apt-get install -y \
 libpq-dev \
 build-essential \
&& rm -rf /var/lib/apt/lists/*

# Use the environment.yml to create the conda environment.
ADD environment.yml /tmp/environment.yml
WORKDIR /tmp
RUN [ “conda”, “env”, “create” ]

ADD . /code

# Use bash to source our new environment for setting up
# private dependencies—note that /bin/bash is called in
# exec mode directly
WORKDIR /code/shared
RUN [ “/bin/bash”, “-c”, “source activate your-environment && python setup.py develop” ]

WORKDIR /code
RUN [ “/bin/bash”, “-c”, “source activate your-environment && python setup.py develop” ]

# We set ENTRYPOINT, so while we still use exec mode, we don’t
# explicitly call /bin/bash
CMD [ “source activate your-environment && exec python application.py” ]

##
##
##

