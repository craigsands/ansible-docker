FROM philm/ansible_playbook

RUN mkdir /root/.ssh
ADD ./ssh_host_rsa_key /root/.ssh/ssh_host_rsa_key
RUN chmod 700 /root/.ssh/ssh_host_rsa_key
RUN echo "[centos]" > /etc/ansible/hosts && \
    echo "centos01 ansible_user=user" >> /etc/ansible/hosts && \
    echo "centos02 ansible_user=user" >> /etc/ansible/hosts

WORKDIR /ansible/playbooks

ENV ANSIBLE_GATHERING smart
ENV ANSIBLE_HOST_KEY_CHECKING false
ENV ANSIBLE_RETRY_FILES_ENABLED false
ENV ANSIBLE_ROLES_PATH /ansible/playbooks/roles
ENV ANSIBLE_SSH_PIPELINING True
ENV PATH /ansible/bin:$PATH
ENV PYTHONPATH /ansible/lib

ENTRYPOINT ["ansible-playbook"]