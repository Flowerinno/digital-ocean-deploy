1. Add public SSH key from the server to GitHub deploy key
2. Create `SSH_PRIVATE_KEY` GitHub secret with your private ssh key
3. `ssh-keyscan SERVER_IP` and create another secret called - `SSH_KNOWN_HOST`
