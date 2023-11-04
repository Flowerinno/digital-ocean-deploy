# Backend is hosted via Droplet

No github action for now. Deploying via command `pm2 deploy production`

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
   7. `sudo apt update
       sudo apt install nginx`
   8.  `sudo ufw default deny incoming
       sudo ufw default allow outgoing`
   9. `sudo ufw allow 'Nginx HTTP'`
   10. `sudo ufw allow 'Nginx HTTPS'`
   11. `sudo ufw allow ssh`
   12. `sudo ufw allow 8080`
   13. `sudo ufw allow http`
   14. `sudo ufw allow https`
   15. `sudo ufw enable`
   16. `sudo ufw status` you will see allowed http traffic
   17. `systemctl status nginx` see if ngnix is running
   18. `nano /etc/nginx/sites-enabled/default` (Ctrl + K to remove by line)
       Remove all contents and paste [this code](https://pastecode.dev/s/oc3EyiLl)
   19. `sudo systemctl restart nginx`   

4. Generate ssh key `ssh-keygen` skip all
   1. `cat .ssh/id_rsa.pub` copy and paste to github deploy key no name required

5. `mkdir test` -> `cd test` -> Clone your repo to add ssh key to known -> `cd ..` -> `rm -rf test`

   ### Create Firewall

1. Networking -> Firewalls -> Create with some name
2. <img width="1147" alt="image" src="https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/9e54187a-ccbf-45ee-b805-1ad0f35ea7fd">
3. Assign to your droplet

   ### Create load balancer

1. Choose correct region (the same as for droplet)
2. Number of nodes = 1
3. Configure forwarding rules, add SSL certificate
   Add `A` record to your hosted zone with:
   Name: api    Value: Choose Droplet's reserved api
   
 <img width="1035" alt="image" src="https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/1a8e2cf0-eb2a-4b01-8d75-6a1056d9435a">

4. Configure health check , redirect http to https
   
<img width="986" alt="image" src="https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/11952fae-15f2-4a4a-b4e4-77e14a56ee25">

After creation add `A` record: Name: api - Value: load balancer

5. Configure your aws secret with appropriate env variables

6. Configure your ecosystem.config.js like this

   <img width="627" alt="image" src="https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/2ba9dd4f-343a-48e4-9b48-7af934ab69ca">

8. Navigate to your local server directory and run `pm2 deploy production setup`
9. `pm2 deploy production`


