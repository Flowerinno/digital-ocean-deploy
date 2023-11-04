# Backend is hosted via Droplet

Virtual Machine like EC2 with Ubuntu OS. We will install everything by hand and configure load balancer, SSL certificates, NGNIX and firewall rules.
ENVs are managed through AWS secrets as before, so you'll just need to create your secret in Secrets Manager and add all variables. Notify you client about this.

### Create -> Droplet

1. Configure region
2. Choose CPU options (Regular -> 24$ is chosen by me)
3. Auth via SSH key, add your id_rsa.pub key
   In terminal `cat ~/.ssh/id_rsa.pub`
4. Hostname -> your domain example.au !!important!!
5. You can create your database while creating the droplet or later in the database section (managed DB)

### Go to your created droplet
1. Create reserved ip to have a consistent ip
2. Connect to your droplet with command: `ssh root@droplet-reserved-ip`
3. Installing necessary packages:

   1. [Node + npm](https://github.com/nodesource/distributions/blob/master/README.md#debian-and-ubuntu-based-distributions)
   2. `sudo npm i pm2 -g`
   3. `sudo apt install -y jq`
   4. `sudo apt install unzip`
   5. [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
   6. Run command `aws configure` and paste Access key and Secret Access Key and region
   7. 
   

