FROM debian

RUN export DEBIAN_FRONTEND=noninteractive \
&& apt-get update -y && apt-get upgrade -y \
&& apt-get install curl -y \
&& apt-get install bzip2 -y

EXPOSE 9987/udp \
	10011/tcp \
	30033/tcp

ENV TS3SERVER_LICENSE accept
RUN mkdir /home/ts3 
RUN useradd ts3
RUN chown ts3: /home/ts3
WORKDIR /home/ts3

RUN curl https://files.teamspeak-services.com/releases/server/3.6.1/teamspeak3-server_linux_amd64-3.6.1.tar.bz2 > ts3-serv.tar.bz2
RUN tar -xjvf ts3-serv.tar.bz2
WORKDIR /home/ts3/teamspeak3-server_linux_amd64
ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh"]

# How to run ?

# build the image with :
# docker build -t ex01img /path/to/Dockerfile/.

# Run the image with :
# docker run --name ex01container -dti -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01img
