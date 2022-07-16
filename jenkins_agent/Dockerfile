FROM jenkins/ssh-agent:jdk11

RUN apt-get update

RUN mkdir -p /etc/apt/keyrings
RUN apt-get install curl gpg git -y
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu focal stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

# Change the group Id to match your host machine docker group!
RUN groupadd -g 998 docker 

RUN apt-get update
RUN apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y

RUN usermod -aG docker jenkins
