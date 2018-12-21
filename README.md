# StegCom

StegCom is an easy way to broadcast messages by publishing images. Steganography is used to hide the message in an image. To enshure only you, your devices and your friends can read the message, AES is used to encrypt it. Since symmectric cryptographie does not provide any information about the author (everybody who can read your messages is also able to generate them), StegCom adds an RSA signature.
The idea for StegCom came when reading about a botnet that used twitter memes as a command and control server.
However, StegCom can also be used for other purposes. Due to the hidden communication channel, a use for bypassing censorship measures would be conceivable.
A long-term goal is a messenger that uses this hidden channel.

### Install

- Clone this repository: git clone https://github.com/schneebonus/StegCom.git
- Install requrenments: cd StegCom; pip3 install -r requirements --user
- Edit settings.py and set your personal secret (used for the aes encryption). Every device and person of your communication needs to know this secret.
- Put your pem certificates to keyfiles/me/ (expected: private_key.pem and my_pubkey.pem)
- Put trusted public keys from your other devices / other persons to keyfiles/others/ (example: john_doe.pem)
- Put your png images in in/ (during generation one image is randomly choosen)

### How to use

StegCom supports several operations. You can generate images containing your message, read messges from given images or crawl an url for images and read the conversation.

#### Hide messages in images

The first step while using StegCom is to generate an image with a hidden message.
This can be done by calling steg_png.py:

```bash
python3 steg_png.py "your message"
```
![Generating images](https://github.com/schneebonus/StegCom/raw/master/signal-2018-12-20-154357.png)

This command results in the following execution steps:
1. Creation of a RSA signature ( privatekey: keyfiles/me/private_key.pem ) for your message
1. A timestamp, the message and the signature are concatenated to a payload
1. An image from in/ is randomly choosen to serve as the carrier image
1. Encryption of the payload by using AES and the secret from settings.py
1. Base64 encoding of the encrypted payload
1. Insertion of the payload into the carrier image
1. Image is put to out/
1. Testing the result: Get the message and verify the signature

#### Get messages from an image

#### Get messages from an url

### Technical details

### Credits

- [Some unknown malware developer](https://techcrunch.com/2018/12/17/malware-commands-code-twitter-hidden-memes/?guccounter=1) for the idea
- [Stegano](https://pypi.org/project/Stegano/) for the steganography
- [simple-crypt](https://pypi.org/project/simple-crypt/) for the easy to use AES wrapper
- [pycrypto](https://pypi.org/project/pycrypto/) for the RSA signature
