# Use official Ruby image as a parent image
FROM ruby:3.2.8-slim

RUN apt-get update -qq && \
    apt-get install -y build-essential libsqlite3-dev nodejs npm curl

RUN npm install --global yarn

WORKDIR /src

RUN gem install rails -v 7.0.0

COPY Gemfile Gemfile.lock ./

RUN if [ -f Gemfile ]; then bundle install; fi

COPY . .

EXPOSE 3000

CMD ["bash", "-c", "bundle install && rails server -b 0.0.0.0"]
