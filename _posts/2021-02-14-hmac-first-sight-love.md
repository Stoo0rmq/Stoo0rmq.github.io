---
layout:     post
title:      HMAC. Love at first sight
date:       2021-02-14 17:32:18
summary:    HMAC and its impact in society.
categories: security
thumbnail: jekyll
tags:
 - security
 - web
 - cryptography
---

# Introduction
The human being is an animal that has been living in society since the early stages. It is no secret either that the main reason to cooperate and socialize was precisely the survival. It was indeed needed to effectively develop a common basic way of information exchange which we called communication. Communication has been the cornerstone of our progress. Without communication, vacciones ,technology and even mammoth hunting would have not been possible. With the evolution of the human, the needs of the communications increased in the same direction. With the new ways of data exchange a vast amount of new problems were discovered:

- How could I transfer this information in a safe way?
- How do I know if the message that I received yesterday is from the original transmitter?
- What if the message that I am sending does not arrive entirely or if it's get partially?

Do any of these problems ring a bell? These exact problems have not been deprecated yet and **modern cryptography** still need to liaise with.


# The Wax
If we thought about the general ideas of the previously mentioned problems, we could easily link them with our habitual technical slang: it is clear that the issues approached were: **authentication** (who are you?) and **integrity** (is this what I should have received?) , core concepts that every sec person should dominate. 
Back in the (old) days the ancient people created a solution that *potentially* solved our two problems: Seal Wax Stamps.

![Wax stamp on an envelope](https://github.com/Stoo0rmq/Stoo0rmq.github.io/blob/master/images/hmac-love/wax-seal-letter_0.jpg?raw=true)

Seal Wax Stamps provided a valid (at that time) method of authentication, as the stamps contained signs or figures in an unique way in order to represent the identification of a person or a family. The interested person would put his letter within an envelope and would seal it using the wax and protecting the integrity of the letter. Through this operation, the receiver could be certain of the authenticity of the letter as well as the integrity (if the receiver had found the seal broken, the integrity would then have been compromised and if the stamp was a generic, the receiver could not be either sure about the authorship of the letter.

It is very interesting to observe how security paradigms have evolved, in particular, the same idea that accompanies the wax stamp can be found nowadays in almost every secure protocol, one of the 21st century wax stamp is called HMAC and today we will analyse its importance. 

# HMAC the new wax stamp

MAC or Message Authentication Code is a small code which let us verify a message, is a way of getting a proof of the authenticity and integrity of a message (like our Wax Stamp). HMAC was the great result of implementing authentication codes using hash functions as MD5 or SHA1.

The idea after HMAC was to provide a robust integrity/authorization mechanism as it entirely relies in the same security principles found on a regular hash function. A regular use case would look as it follows:
- Dennis wants to communicate with Maria. They both shared a secret key called ^^S^^
- Dennis wants to send an important message that contains the date of an important appoinment. They message is called ==M==.
- Dennis generates a HMAC which will combine the secret key  ==S== that they both know as well as the message  
- Maria receives the message ==M== with a small note next to it: the HMAC value
- As Maria knows the secrey key ==S== and the message ==M== she is perfectly able to recreate the HMAC value to verify that it was indeed sent by Dennis and that its content was not modified.


From a mathematical perspective, in order to build a secure HMAC the following items are needed:
- A secret key K which will be shared among the involved parties interested on the transaction
- A message M  (the message which will be transmitted)
- A Hash function H()
- Two strings, each of those is a different padding string. 

> Padding is required in hash functions as they divide the data to be hashed in different blocks of fixed size. In order to keep the consistency it is necessary to "fill" the empty spaces. This is done using padding.

![](https://raw.githubusercontent.com/Stoo0rmq/Stoo0rmq.github.io/master/images/hmac-love/hmac.png)

As it has been seen, the theoretical implementation is not rocket science. HMAC provides an easy and trustful way of validating authentication and integrity.

# HMAC in the real world

It is no secret that HMAC performs its task very well. This is the reason why you can find an implementation of HMAC in some of the most important protocols/applications used nowadays:
- TLS therefore any protocol implementing it as HTTPS , SMTPS, SIPS , MySQL ...
- SSH , SCP and SFTP
- IPsec (VPNs)
- Routing protocols as BGP or OSPF
- JWT (HMAC can be used to signed the token)
- Google Authenticator
- Amazon SimpleDB


In light of the above, it becomes clear the success of HMAC in modern security. HMAC is available in many different languages, but, as it is natural, it is important to understand the limitations of HMAC:

HMAC can save resources and agilise processes. For example, on web servers where HMAC can be used in order to protect CSRF tokens , sessions,  information or actions that might require a verification of that the specified value was originated from the expected server. By using HMAC we are adding a state into the protected resource. In the case of the CSRF tokens it would not be needed to waste resources by storing CSRF tokens nor veryfing its authenticity, using HMAC a server with the key could quickly check it out. 

In SSH HMAC plays a fundamental role: SSH is an extremely (and useful!) complex and secure protocol where the Secret key is obtained from the symmetrical shared secret. Once the connection is established, the protocol appends on the cleartext part of every block a hmac which will be verified upon arrival. If any of these blocks does not match on the HMAC verification, it will be discarded.

Even though HMAC provides a solid solution, there are security concerns that should take into account before using them:
- The authenticity/integrity is safe as long as the secret key is safe: this secret key should be securely generated and distributed to exact number of peers that might need verify the HMAC. A key exchange algorithm might be useful here. If an attacker is able to guess/crack the secret key he will be able to create valid and verified HMAC
- The security of HMAC highly relies on the hash function used: if a hash function is vulnerable to collision, the HMAC will inheritates the same vulnerability.
- HMAC solves the lenght extension attack that could be performed over a MAC implemented using SHA1 or MD5. A legnth extension attack allows you to create a valid MAC as long as:
   1. You know the lenght of the secret key S
   2. You know the message M
   3. The hash function used is MD5/SHA1/SHA2
   4. The MAC is the result of   H (Secret|Message)

>The main idea after length extension attacks is the *internal state* a value that the hash function returns for every block. At the end of its process, the hash function uses this *internal state* against the last  block of data to create the hash, we can interrupt the hash creation process and deceive it in order to add another block. The result? A completely valid HASH will be created. Fortunately, this problem is solved by HMAC as it performs a two iterations hashing applying a padding on each iteration.

- HMAC does not implement by itself protection against replay attacks. This can addressed by adding a nonce at the end of the message M


As a colophon I would like to remark the importance of (in my opinion) the use of a properly implemented HMAC values these days. We all use HMACs even when we do not think we are using them! The idea of this post was to let the reader realise how not everything in cryptography has to be hard to digest.

Thanks a lot:)


