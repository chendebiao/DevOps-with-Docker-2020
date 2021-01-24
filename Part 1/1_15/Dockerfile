FROM nginx
ENV AUTHOR=Cheng

WORKDIR /usr/share/nginx/html

RUN apt-get update && apt-get install -y git

RUN git clone https://github.com/chendebiao/Folium_Map_Visualization /usr/share/nginx/html/project

RUN cd project && cp index.html /usr/share/nginx/html

CMD cd /usr/share/nginx/html && nginx -g 'daemon off;'
