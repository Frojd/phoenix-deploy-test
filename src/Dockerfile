FROM ubuntu:16.04

RUN apt-get update && apt-get -y install wget
RUN wget https://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb
RUN dpkg -i erlang-solutions_1.0_all.deb
RUN apt-get update \
    && apt-get -y install esl-erlang elixir=1.5.2-1 \
    && apt-get -y install locales netcat inotify-tools vim \
    && rm -rf /var/lib/apt/lists/*

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN mix local.hex --force
RUN mix local.rebar --force

RUN mix archive.install --force https://github.com/phoenixframework/archives/raw/master/phx_new-1.3.0.ez

WORKDIR /app
ADD . /app

ENV SCAFFOLD_APP_NAME=phoenix_app

ENTRYPOINT ["./docker-entrypoint.sh"]
CMD ["server"]
