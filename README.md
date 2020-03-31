# ansible-docker

Generate public/private keypair
```
ssh-keygen -t rsa -b 4096 -f ssh_host_rsa_key -N ""
mv ssh_host_rsa_key ansible/ssh_host_rsa_key
mv ssh_host_rsa_key.pub centos/ssh_host_rsa_key.pub
```

Start CentOS containers
```
docker-compose -f centos/docker-compose.yml up
```

Run Ansible container
```
docker-compose -f ansible/docker-compose.yml up
```

Shell into ansible container (for debugging)
```
docker exec -it ansible_ansible_1 /bin/sh
```

Retrieve IP address from running container
```
docker inspect -f "{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}" centos_centos01_1
```

SSH from host
```
ssh -i ansible/ssh_host_rsa_key user@localhost -p 2222
```