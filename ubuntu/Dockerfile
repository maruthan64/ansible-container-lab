FROM ubuntu:latest

ARG USERNAME=kimyk
EXPOSE 22

# Apt update & apt install required packages
RUN apt update && apt -y install openssh-server sudo net-tools less ansible vim


# Add a non-root user
RUN useradd -ms /bin/bash $USERNAME

# Remove no-needed packages
RUN apt -y autoremove && apt -y autoclean && apt -y clean

# Create the ssh directory and authorized_keys file
USER $USERNAME
RUN mkdir /home/$USERNAME/.ssh
COPY keycontainer.pub /home/$USERNAME/.ssh/authorized_keys
COPY keycontainer /home/$USERNAME/.ssh/keycontainer

USER root
RUN chown $USERNAME /home/$USERNAME/.ssh/authorized_keys && \
chmod 600 /home/$USERNAME/.ssh/authorized_keys
RUN chown $USERNAME /home/$USERNAME/.ssh/keycontainer && \
chmod 600 /home/$USERNAME/.ssh/keycontainer
RUN echo "${USERNAME} ALL=(ALL) NOPASSWD: ALL " >> /etc/sudoers

# create ansible lab files
RUN mkdir /home/$USERNAME/ansible
COPY inventory_example.yml /home/$USERNAME/ansible/inventory.yml
RUN chown -R $USERNAME:$USERNAME /home/$USERNAME/ansible/ && \
chmod -R 755 /home/$USERNAME/ansible/
# Run ssh service
RUN service ssh start

CMD ["/usr/sbin/sshd","-D"]
