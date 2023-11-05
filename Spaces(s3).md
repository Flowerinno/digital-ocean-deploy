# S3 compatible spaces on Digital Ocean

Almost completely compatible to S3, no re-write was needed for me, just needed to replace key, secret-key and add origin url from spaces.

### Create -> Spaces

1. Configure creation no CDN required
2. Copy origin url (without your bucket's name) after creation and add to your s3 client in the code like this
<img width="339" alt="image" src="https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/3f56488c-a38e-42cb-8591-06eb5d8c997d">

<br/>

   
<img width="495" alt="image" src="https://github.com/Flowerinno/digital-ocean-deploy/assets/93313212/d2c4fbe6-eb0d-46b4-b893-fa3a9a25f9b4">

3. Key and secret-key can be created in API -> Spaces Keys

