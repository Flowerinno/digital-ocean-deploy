1. Add public SSH key from the server to GitHub deploy key
2. Create `SSH_PRIVATE_KEY` GitHub secret with your private ssh key
3. Copy contents from this command - `ssh-keyscan SERVER_IP` and paster in another Github secret called - `SSH_KNOWN_HOSTS` 
