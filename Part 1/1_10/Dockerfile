FROM ubuntu:16.04

WORKDIR /mydir 

# Prerequisites
RUN apt-get update && apt-get install -y git curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt-get install -y nodejs

# Clone the project form https://github.com/docker-hy/frontend-example-docker
RUN git clone https://github.com/docker-hy/frontend-example-docker .
RUN npm install

# Expose port 5000
EXPOSE 5000

ENTRYPOINT ["npm"]
CMD ["start"]
