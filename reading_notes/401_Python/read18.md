# Reading 18 Cryptography
> what is Cryptography 
- Cryptography, or the art and science of encrypting sensitive information,
- was once exclusive to the realms of government,
- academia, and the military. However, with recent technological advancements, cryptography has begun to permeate all facets of everyday life.

> Understanding Ciphers: The Basis of All Cryptography
- Cryptography, at its most fundamental level, requires two steps: encryption and decryption. The encryption process uses a cipher in order to encrypt plaintext and turn it into ciphertext.
- Decryption, on the other hand, applies that same cipher to turn the ciphertext back into plaintext.
- example
![image](https://thebestvpn.com/wp-content/uploads/2017/06/tFnX1co-640x335.jpg)
- By applying this cipher, our plaintext “Hello” turns into the ciphertext “Khoor”


> Why Does Cryptography Matter?
- It means that, in order to transmit a secure message, you must hold back some of the information required to understand the message.
- Which, by default, means it would only take one person with knowledge of the original message to divulge the missing pieces to the public.
- With cryptography, a specific key and numerous calculations are required.
- Even if someone knew the encryption method used, 
- they wouldn’t be able to decrypt the message without the corresponding key,making your information much more secure.


> Types of Cryptography
- Hashing
  - Hashing is a type of cryptography that changes a message into an unreadable string of text for the purpose of verifying the message’s contents, not hiding the message itself.
  - This type of cryptography is most commonly used to protect the transmission of software and large files where the publisher of the files or software offers them for download.
  - The reason for this is that, while it is easy to calculate the hash,
    - it is extremely difficult to find an initial input that will provide an exact match for the desired value.
- Symmetric Cryptography 
  - Symmetric Cryptography, likely the most traditional form of cryptography, is also the system with which you are probably most familiar.  
  - This type of cryptography uses a single key to encrypt a message and then decrypt that message upon delivery.
  - Since symmetric cryptography requires that you have a secure channel for delivering the crypto key to the recipient,
  -  this type of cryptography is all but useless for transmitting data (after all, if you have a secure way to deliver the key, why not deliver the message in the same manner?). 
![image](https://thebestvpn.com/wp-content/uploads/2017/06/0ce8dfd.jpg)

- Asymmetric Cryptography
  - Asymmetric cryptography (as the name suggests) uses two different keys for encryption and decryption, as opposed to the single key used in symmetric cryptography.
  - The first key is a public key used to encrypt a message, and the second is a private key which is used to decrypt them.
  -  The great part about this system is that only the private key can be used to decrypt encrypted messages sent from a public key.

- Key Exchange Algorithms
  - Although this particular type of cryptography isn’t particularly applicable for individuals outside of the cyber-security realm
  - A key exchange algorithm, like Diffie-Hellman, is used to safely exchange encryption keys with an unknown party.
![image](https://thebestvpn.com/wp-content/uploads/2017/06/n4jBE-1-426x640.png)


> The 4 Types of Cryptographic Functions
- Authentication
  - When we use the right cryptographic system, we can establish the identity of a remote user or system quite easily.
  - The go-to example of this is the SSL certificate of a web server which provides proof to the user that they are connected to the right server.  
![image](https://thebestvpn.com/wp-content/uploads/2017/06/unnamed-640x384.jpg)
- Nonrepudiation
  - This concept is especially important for anyone using or developing financial or e-commerce applications.
  - One of the big problems that e-commerce pioneers faced was the pervasive nature of users who would refute transactions once they had already occurred.
  - Cryptographic tools were created to ensure that each unique user had indeed made a transaction request that would be irrefutable at a later time.
- Confidentiality
  - With information leaks and a seemingly endless number of privacy scandals making the headlines,
  - keeping your private information
  - private is probably one of your biggest concerns. This is the exact function for which cryptographic systems were originally developed.  
  - With the right encryption tools, users can guard sensitive company data, personal medical records, or just lock their computer with a simple password.
- Integrity
  - Another important use of cryptography is to ensure that data is not viewed or altered during transmission or storage.
  - The most common way to do accomplish data integrity through cryptography is by using cryptographic hashes to safeguard information with a secure checksum.


> Caesar cipher
- In cryptography, a Caesar cipher, also known as Caesar's cipher, the shift cipher, Caesar's code or Caesar shift,
- is one of the simplest and most widely known encryption techniques.
- It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet
- The method is named after Julius Caesar, who used it in his private correspondence
  - The encryption step performed by a Caesar cipher is often incorporated as part of more complex schemes
  - such as the Vigenère cipher
  - still has modern application in the ROT13 system. As with all single-alphabet substitution ciphers
  - the Caesar cipher is easily broken and in modern practice offers essentially no communications security.
- example
```
Plain	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z
Cipher	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W

encrypttion -->  E_{n}(x)=(x+n)\mod {26}.
decrypttion -->  D_{n}(x)=(x-n)\mod {26}.

Plaintext:  THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG
Ciphertext: QEB NRFZH YOLTK CLU GRJMP LSBO QEB IXWV ALD

```

> Resources 
- https://en.wikipedia.org/wiki/Caesar_cipher
- https://www.khanacademy.org/computing/computers-and-internet/xcae6f4a7ff015e7d:online-data-security/xcae6f4a7ff015e7d:data-encryption-techniques/a/encryption-decryption-and-code-cracking
- https://thebestvpn.com/cryptography/
- https://www.howtogeek.com/183051/htg-explains-how-computers-generate-random-numbers/

