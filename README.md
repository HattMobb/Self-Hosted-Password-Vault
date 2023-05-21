# Self-Hosted-Password-Vault
Personally hosted vault using open source Passbolt
---
Technologies used:
- Docker
- Passbolt

Many traditional password managers use a master password  to grant access to the password vault. This means that vault security is only as strong as the password and MFA in place (if any, but of course some type of MFA should be enabled). Passbolt uses a "master" password along with challenge based authentication which means that even if someone gains access to your master password, they won't be simply granted access to your vault. The process is as follows:
- Passbolt uses OpenPGP encryption to randomly create a pub/priv key pair.(This randomness is important as other password managers sometimes generate your key from your password which means that it is not necessarily "random" and is more vunlerable to brute force.
- Your private key is stored on your local device and the public key is stored with Passbolt.
- Your master password (something you know) is used to decrypt your private key on your device (something you have) which is used to unlock your personal password vault.

Self hosting allows increased security, privacy and control (assuming your systems /devices are properly secured in the first place) and passbolt includes features that let you create & store new accounts on the fly.


For a run down of features, functions and capabilities of Passbolt, head to: https://www.passbolt.com/ or https://github.com/passbolt 


## How to

- Begin by installing Docker desktop from https://www.docker.com/products/docker-desktop/
- Download the .yaml config file


![Screenshot 2023-05-21 115227](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/99fa7362-2a19-43b9-ab03-da5dc7b4bb85)

- Opening the config file allows us to edit the contents for our needs


![Screenshot 2023-05-21 115601](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/2f0a4ba4-f731-427c-922a-6f52b7d1b3b9)

- The APP_FULL_BASE_URL environment variable is set by default to https://passbolt.local but I'm changing it to https://localhost due to it being self hosted.
- PASSBOLT_SSL_FORCE can be set to 'false' as it is being hosted within it's own container apassvault includes it's own self signed cert.
- On top of the APP_FULL_BASE_URL, passbolt requires you to set email settings to receive notifications and for recovery purposes. They can be completed as follows:


![Screenshot 2023-05-21 121656](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/9eaa93ae-b985-426c-9cc7-02e9cc91fea6)

- Finally, change the host port from 80 to 8080 (Docker port)

![Screenshot 2023-05-21 122447](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/26b55b65-2f88-4a6d-a020-fdc1827d18c2)

- Create your container via `docker-compose -f docker-compose-ce.yaml up -d`

- Create your admin account via `docker-compose -f docker-compose-ce.yaml exec passbolt su -m -c "/usr/share/php/passbolt/bin/cake passbolt register_user -u EMAIL -f FIRSTNAME -l LASTNAME -r admin" -s /bin/sh www-data` 

- You'll see the screen below, under which is a link you copy into your browser 

![Screenshot 2023-05-21 154408](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/fbae4e68-9960-48bc-a844-f2a7897f3547)

- Create your master password (obviously don't lose this  and  you're good to go! Don't forget to download the Passbolt extension for your browser of choice). 

- You cana now create passwords for any account of your choice

 ![Screenshot 2023-05-21 154735](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/513d6fbd-f367-44ac-be5e-b507308de58c)





