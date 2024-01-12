1. Add public SSH key from the server to GitHub deploy key
2. Create `SSH_PRIVATE_KEY` GitHub secret with your private ssh key
3. Copy contents from this command - `ssh-keyscan SERVER_IP` and paster in another Github secret called - `SSH_KNOWN_HOSTS` 
4. Update ecosystemconfig
![image](https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/78117973-ab96-40d5-a8ba-8e604ba70580)


