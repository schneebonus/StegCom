# StegCom

StegCom is an easy way to broadcast messages by publishing images. Steganography is used to hide the message in an image. To enshure only you, your devices and your friends can read the message, AES is used to encrypt it. Since symmectric cryptographie does not provide any information about the author (everybody who can read your messages is also able to generate them), StegCom adds an RSA signature.
The idea for StegCom came when reading about a botnet that used twitter memes as a command and control server.
However, StegCom can also be used for other purposes. Due to the hidden communication channel, a use for bypassing censorship measures would be conceivable.
A long-term goal is a messenger that uses this hidden channel.

### Install

- Clone this repository: ToDo
- Install requrenments: ToDo
- Edit settings.py and set your personal secret (used for the aes encryption). Every device and person of your communication needs to know this secret.
- Put your pem certificates to keyfiles/me/ (expected: private_key.pem and my_pubkey.pem)
- Put trusted public keys from your other devices / other persons to keyfiles/others/ (example: john_doe.pem)
- Put your png images in in/ (during generation one image is randomly choosen)

### How to use

StegCom supports several operations. You can generate images containing your message, read messges from given images or crawl an url for images and read the conversation.

#### Hide messages in images

#### Get messages from an image

#### Get messages from an url
