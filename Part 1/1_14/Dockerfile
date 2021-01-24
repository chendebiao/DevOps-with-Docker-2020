FROM ruby:2.6.0

WORKDIR /mydir

RUN apt-get update && apt-get install -y git

RUN git clone https://github.com/docker-hy/rails-example-project .

RUN apt-get update && apt-get -y install nodejs

RUN bundle install

RUN rails db:migrate

ENTRYPOINT ["rails"]
CMD ["s"]
