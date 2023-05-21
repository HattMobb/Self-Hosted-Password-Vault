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
- On top of the APP_FULL_BASE_URL, passbolt requires you to set email settings to receive notifications and for recovery purposes. They can be completed as follows:


![Screenshot 2023-05-21 121656](https://github.com/HattMobb/Self-Hosted-Password-Vault/assets/134090089/9eaa93ae-b985-426c-9cc7-02e9cc91fea6)
