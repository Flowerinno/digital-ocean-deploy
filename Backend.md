#Backend is hosted via Droplet

Virtual Machine like EC2 with Ubuntu OS. We will install everything by hand and configure load balancer, SSL certificates, NGNIX and firewall rules.

### Create -> Droplet

1. Configure region
2. Choose CPU options (Regular -> 24$ is chosen by me)
3. Auth via SSH key, add your id_rsa.pub key
   In terminal `cat ~/.ssh/id_rsa.pub`
4. Hostname -> your domain example.au !!important!!
5. You can create your database while creating the droplet or later in the database section (managed DB)

### Go to your created droplet
1. Create reserved ip to have a consistent ip
2. 

