#docker build -t 01_dockerfiles-ex02 .
#docker run -it --rm -p 3000:3000 docker 01_dockerfiles-ex02 

FROM ruby:2.5.1

RUN apt-get update && \
    apt-get install -y build-essential libpq-dev nodejs && \
    mkdir /opt/app

EXPOSE 3000

# Copy application
ONBUILD COPY app/ /opt/app

# Install the stuff
ONBUILD RUN bundle install && \
	rake db:migrate && \
	rake db:setup && \
	rake db:seed

ONBUILD ADD			Gemfile /opt/app
ONBUILD ADD			Gemfile.lock /opt/app
ONBUILD ADD 		. /opt/app


# Set the workdir
WORKDIR /opt/app