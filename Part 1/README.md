# Part 1 Answer
## 1.1 Answer
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
**Password: basics**  
**Secret message is: "This is the secret message"**

## 1.4 Answer
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
cheng@linux:~$ docker run -d -p 1234:80 devopsdockeruh/ports_exercise
c4a6e2711b1f6298f694cd6bad68076dd2be7cc30fd8d30f3a26eeb3f6235a47

cheng@linux:~$ docker container port c4a6
80/tcp -> 0.0.0.0:1234

cheng@linux:~$ curl http://localhost:1234/
Ports configured correctly!!
```

## 1.10 Answer
## 1.11 Answer
## 1.12 Answer
## 1.13 Answer
## 1.14 Answer
## 1.15 Answer
## 1.16 Answer
## 1.17 Answer

