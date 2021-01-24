FROM ubuntu:16.04 

WORKDIR /mydir
RUN apt-get update && apt-get install -y curl
COPY local_script .
CMD ["/bin/bash","local_script"]
