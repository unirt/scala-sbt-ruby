FROM hseeberger/scala-sbt:8u222_1.3.2_2.12.10

USER root
ENV PGSSLMODE disable

RUN apt update && apt upgrade -y --allow-unauthenticated
RUN apt install wget ca-certificates software-properties-common -y
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3B4FE6ACC0B21F32 40976EAF437D05B5
RUN bash -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
RUN add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
RUN apt update && apt upgrade -y --allow-unauthenticated
RUN apt install libicu55 libpq-dev postgresql-10 git gcc make rbenv ruby-build -y  --allow-unauthenticated

RUN echo 'eval "$(rbenv init -)"' >> ~/.bashrc
RUN bash -c 'source ~/.bashrc'
RUN rbenv install 2.4.0
RUN rbenv global 2.4.0
RUN rbenv exec gem install bundler

RUN sbt version
