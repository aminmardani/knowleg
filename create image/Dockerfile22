FROM 192.168.25.203:8080/library/maven:3.3.9-jdk-8

# Install docker-engine
# According to Petazzoni's article:
# ---------------------------------
# "Former versions of this post advised to bind-mount the docker binary from
# the host to the container. This is not reliable anymore, because the Docker
# Engine is no longer distributed as (almost) static libraries."

# correct server version
ARG docker_version=1.11.2


RUN echo "deb [check-valid-until=no] http://archive.debian.org/debian jessie-backports main" > /etc/apt/sources.list.d/jessie-backports.list
RUN echo "deb [check-valid-until=no] http://deb.debian.org/debian/ jessie main" > /etc/apt/sources.list.d/jessie-backports.list
RUN echo "deb [check-valid-until=no] http://security.debian.org/ jessie/updates main" > /etc/apt/sources.list.d/jessie-backports.list

RUN sed -i '/deb http:\/\/deb.debian.org\/debian jessie-updates main/d' /etc/apt/sources.list

RUN apt-get -o Acquire::Check-Valid-Until=false update

RUN curl -sSL https://get.docker.com/ | sh && \
    apt-get install docker-ce

# Install kubectl
RUN curl -O https://storage.googleapis.com/kubernetes-release/release/v1.18.6/bin/linux/amd64/kubectl \
    && chmod +x kubectl \
    && cp kubectl /usr/local/bin/kubectl