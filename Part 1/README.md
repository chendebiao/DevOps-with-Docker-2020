# Part 1 Answer
## 1.1 Answer
### Commands
the output for `docker container ls -a`:
```
cheng@linux:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                     PORTS     NAMES
c09c81f94a66   nginx     "/docker-entrypoint.…"   32 seconds ago   Up 31 seconds              80/tcp    flamboyant_saha
0fc8493f9f08   nginx     "/docker-entrypoint.…"   34 seconds ago   Exited (0) 7 seconds ago             fervent_snyder
185af2c1a43c   nginx     "/docker-entrypoint.…"   35 seconds ago   Exited (0) 7 seconds ago             distracted_lumiere
```
## 1.2 Answer
```
cheng@linux:~$ docker container ls -as
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES     SIZE
cheng@linux:~$ docker image ls
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
cheng@linux:~$ 

```
## 1.3 Answer
```
cheng@linux:~$ docker container run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete 
5e2195587d10: Pull complete 
6f595b2fc66d: Pull complete 
165f32bf4e94: Pull complete 
67c4f504c224: Pull complete 
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```
### Secret message  
**Password: basics**  
**Secret message is: "This is the secret message"**

## 1.4 Answer
### Commands
```
cheng@linux:~$ docker container exec -it quizzical_meitner bash
root@c0939e3ab049:/usr/app# tail -f ./logs.txt
"Docker is easy"
Sat, 23 Jan 2021 11:08:40 GMT
Sat, 23 Jan 2021 11:08:43 GMT
Sat, 23 Jan 2021 11:08:46 GMT
Sat, 23 Jan 2021 11:08:49 GMT
Secret message is:
"Docker is easy"
Sat, 23 Jan 2021 11:08:55 GMT
```
### Secret message
**Secret message is: "Docker is easy"**

## 1.5 Answer
Seems I don't need to fix anything, the command ran smoothly at the first time.  
```
cheng@linux:~$ sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>

```
## 1.6 Answer
### Dockerfile  
[Exercise 1.6 Dockerfile](https://github.com/chendebiao/DevOps-with-Docker-2020/blob/main/Part%201/1_6/Dockerfile)

### Command  
```
cheng@linux:~/1_6$ docker build -t docker-clock .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM devopsdockeruh/overwrite_cmd_exercise
 ---> 3d2b622b1849
Step 2/2 : CMD ["--triangle 12"]
 ---> Using cache
 ---> a1b506aa07f9
Successfully built a1b506aa07f9
Successfully tagged docker-clock:latest
cheng@linux:~/1_6$ docker container run docker-clock

*
**
* *
*  *
*   *
*    *
*     *
*      *
*       *
*        *
*         *
************
```

## 1.7 Answer
Dockerfile and script file on my local machine are in the folder ['1_7']()
```
cheng@linux:~/1_7$ docker build -t curler .
Sending build context to Docker daemon  3.072kB
Step 1/5 : FROM ubuntu:16.04
 ---> 8185511cd5ad
Step 2/5 : WORKDIR /mydir
 ---> Using cache
 ---> 42775c892a07
Step 3/5 : RUN apt-get update && apt-get install -y curl
 ---> Using cache
 ---> d0fb5825f29b
Step 4/5 : COPY local_script .
 ---> Using cache
 ---> 9e3d550cc4c9
Step 5/5 : CMD ["/bin/bash","local_script"]
 ---> Using cache
 ---> ae1fc4034ea9
Successfully built ae1fc4034ea9
Successfully tagged curler:latest
```

```
cheng@linux:~/1_7$ docker container run -it curler
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
```

## 1.8 Answer
```
cheng@linux:~/1_8$ docker run -it -v $(pwd)/logs.txt:/usr/app/logs.txt devopsdockeruh/first_volume_exercise
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
...
```

In the log.txt we have 
```
Sat, 23 Jan 2021 12:21:49 GMT
Sat, 23 Jan 2021 12:21:52 GMT
Sat, 23 Jan 2021 12:21:55 GMT
Sat, 23 Jan 2021 12:21:58 GMT
Secret message is:
"Volume bind mount is easy"
Sat, 23 Jan 2021 12:22:04 GMT
Sat, 23 Jan 2021 12:22:07 GMT
Sat, 23 Jan 2021 12:22:10 GMT
Sat, 23 Jan 2021 12:22:13 GMT
Secret message is:
"Volume bind mount is easy"
...
```

**Secret message is: "Volume bind mount is easy"**


## 1.9 Answer
```
cheng@linux:~$ docker run -d -p 80:80 devopsdockeruh/ports_exercise
c18c6f738572f350f25e150fb59442a5e821cdca258487720bbcff601f2f23eb
```
```
cheng@linux:~$ docker container port c18c
80/tcp -> 0.0.0.0:80
```
```
cheng@linux:~$ curl http://localhost:80
Ports configured correctly!!
```

## 1.10 Answer
```
cheng@linux:~/1_10$ docker build -t webexample .
Sending build context to Docker daemon  2.048kB
...
Successfully built 25344abd7dc4
Successfully tagged webexample:latest
```
```
cheng@linux:~/1_10$ docker run -d -p 5000:5000 webexample
34a730d76b8d773a3a7180e38f1dd2f7b98e41783b3603f499730e309a3a6a34
```
```
cheng@linux:~/1_10$ curl http://localhost:5000/
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta content="ie=edge" http-equiv="x-ua-compatible">
    <title>Webpack App</title>
    <link href="vendors~main-1.css" rel="stylesheet" />
    <link href="main.css" rel="stylesheet" />
  </head>
  <body>
    <div id="root">
    </div>
    <script src="vendors~main.js" type="text/javascript"></script>
    <script src="main.js" type="text/javascript"></script>
  </body>
</html>
```
On the http://localhost:5000/ webpage:  
**Part 1  
Exercise 1.10: Congratulations! You configured your ports correctly!**

![1_10_result](https://github.com/chendebiao/DevOps-with-Docker-2020/blob/main/Part%201/1_12/1_12_result.jpg)

## 1.11 Answer
```
cheng@linux:~/1_11$ docker build -t webserver .
Sending build context to Docker daemon  3.072kB
...
Successfully built 64e927d375a8
Successfully tagged webserver:latest
```
```
cheng@linux:~/1_11$ docker run -d -v $(pwd)/logs.txt:/logs.txt -p 8000:8000 webserver
57deccde07587f9519ce0932f3cb222751bb363bbabcce85f34ca422312e79f9
```
```
cheng@linux:~/1_11$ curl http://localhost:8000
Port configured correctly, generated message in logs.txt
```

In log.txt:
```
1/23/2021, 3:04:48 PM: Connection received in root
1/23/2021, 3:04:49 PM: Connection received in root
1/23/2021, 3:04:50 PM: Connection received in root
1/23/2021, 3:04:50 PM: Connection received in root
```
## 1.12 Answer
```
cheng@linux:~/1_12$ docker build -f Dockerfile_front -t front .
Sending build context to Docker daemon  3.584kB
...
Successfully built 69680903c498
Successfully tagged front:latest

cheng@linux:~/1_12$ docker build -f Dockerfile_back  -t back .
Sending build context to Docker daemon  3.584kB
...
Successfully built 631f9e7a96f5
Successfully tagged back:latest
```
```
cheng@linux:~/1_12$ docker run -d -p 5000:5000 front
d9a2f1d35a1b01e44f03ad786bc734557eab7631d37a52c9e81888eae004a7ca

cheng@linux:~/1_12$ docker run -d -p 8000:8000 back
cca62e13186f21bd3d7da7210a8848f552ec98e3474ec864113b96a416679ee8
```
On the http://localhost:5000/ webpage:  
**Exercise 1.12: Working!**

![1_12_result](https://github.com/chendebiao/DevOps-with-Docker-2020/blob/main/Part%201/1_12/1_12_result.jpg)

## 1.13 Answer
```
cheng@linux:~/1_13$ docker build -t javaspring .
Sending build context to Docker daemon  2.048kB
...
Successfully built 2071245b6a41
Successfully tagged javaspring:latest
```

```
cheng@linux:~/1_13$ docker run -d -p 8080:8080 javaspring
668992f31d712a340dba6c86b722bca720466189d9dcf88d4cf257f58c3eea7c
```
On the http://localhost:8080/ webpage:  
**Success**

![1_13_result](https://github.com/chendebiao/DevOps-with-Docker-2020/blob/main/Part%201/1_13/1_13_result.jpg)
## 1.14 Answer
```
cheng@linux:~/1_14$ docker build -t rails .
Sending build context to Docker daemon  2.048kB
...
Successfully built c9f34f2fbad4
Successfully tagged rails:latest
```
```
cheng@linux:~/1_14$ docker run -d -p 3000:3000 rails
7c6b5e7f2b5dfc8f00032916bf68b3d40380ceaf15241776b3195500a8120aee
```
On the http://localhost:3000/ webpage:  
**New Press  
Total presses: 1  
Press was successfully created.  
List presses**

![1_14_result](https://github.com/chendebiao/DevOps-with-Docker-2020/blob/main/Part%201/1_14/1_14_result.jpg)
## 1.15 Answer

I write a simple Docker.
It will get a static html website from my project on github, then map it to the container's local port.
### The docker link:
https://hub.docker.com/repository/docker/chendebiao/my_first_docker
### The github project link:
https://github.com/chendebiao/Folium_Map_Visualization

Can be run with following code:
```
docker run -d -p 1234:80 chendebiao/my_first_docker:v1.0
```
Result:
![1_15_result](https://github.com/chendebiao/DevOps-with-Docker-2020/blob/main/Part%201/1_15/1_15_result.jpg)

## 1.16 Answer
```
cheng@linux:~/1_16$ heroku login
cheng@linux:~/1_16$ heroku container:login

cheng@linux:~/1_16$ docker tag devopsdockeruh/heroku-example:latest registry.heroku.com/chendebiao-docker-1-16/web

cheng@linux:~/1_16$ docker push registry.heroku.com/chendebiao-docker-1-16/web

cheng@linux:~/1_16$ heroku container:release -a chendebiao-docker-1-16 web
```

### **The url in which the released application is**
https://chendebiao-docker-1-16.herokuapp.com/
## 1.17 Answer
Skipped.

