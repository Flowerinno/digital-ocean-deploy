1. Add public SSH key from the server to GitHub deploy key
2. Create `SSH_PRIVATE_KEY` GitHub secret with your private ssh key
3. Copy contents from this command - `ssh-keyscan SERVER_IP` and paster in another Github secret called - `SSH_KNOWN_HOSTS` 
4. Update ecosystemconfig
![image](https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/7dc37b72-9766-444a-b8f2-064c7e069b9a)

