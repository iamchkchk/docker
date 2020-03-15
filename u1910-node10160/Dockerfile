FROM ubuntu:19.10
ENV DEBIAN_FRONTEND="noninteractive"
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y \
					curl \
					cron \
					unzip \
					git \
					openssl \
					wget
					
#https://stackoverflow.com/questions/25899912/how-to-install-nvm-in-docker
# Install nvm with node and npm
    
SHELL ["/bin/bash", "--login", "-i", "-c"]

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
RUN source /root/.bashrc && nvm install 10.16.0



#npm cache clean
RUN npm cache clean --force

#upate npm
RUN npm install -g npm@latest --force

#npm cache clean
RUN npm cache clean --force

SHELL ["/bin/bash", "--login", "-c"]


##RUN chmod +x /usr/local/bin/run

#EXPOSE 3000
#EXPOSE 80
#EXPOSE 443
##CMD ["/usr/local/bin/run"]