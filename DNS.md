1. You can create your hosted zone -> Create (green button)
2. Exactly how you managed your dns records in other services (like Route 53)
3. Copy NS (Name Server) records to your DNS provider (transip, marcaria etc.) it will redirect traffic to digital ocean hosted zone
4. Move existing DNS records to this zone
5. If client is already deployed on app platform, configure your domain, it will automatically add A/AAAA records to the zone
6. Proceed with your droplet to deploy backend (if not deployed)
