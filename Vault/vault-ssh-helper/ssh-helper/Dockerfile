FROM ubuntu:16.04

RUN mkdir /var/run/sshd && \
    apt-get update && \
    apt-get install -y openssh-server && \
    sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    apt-get install -y unzip && \
    apt-get install -y curl && \
    curl -LO https://releases.hashicorp.com/vault-ssh-helper/0.1.4/vault-ssh-helper_0.1.4_linux_amd64.zip && \
    unzip vault-ssh-helper_0.1.4_linux_amd64.zip && \
    mv vault-ssh-helper /usr/local/bin && \
    rm vault-ssh-helper_0.1.4_linux_amd64.zip
    
EXPOSE 22

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

CMD ["/usr/sbin/sshd", "-D"]