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

