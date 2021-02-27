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
 - python
 - cryptography
---

# Introduction
Atention

The human being is an animal that has been living in society since the early stages. It is no secret either that the main reason to cooperate and socialize was precisely the survival. It was indeed needed to effectively develop a common basic way of information exchange which we called communication. Communication has been the cornerstone of our progress. Without communication, vacciones ,technology and even mammoth hunting would have not been possible. With the evolution of the human, the needs of the communications increased in the same direction. With the new ways of data exchange a vast amount of new problems were discovered: 
- How could I transfer this information in a safe way?
- How do I know if the message that I received yesterday is from the original transmitter?
- What if the message that I am sending does not arrive entirely or if it's get partially?

Do any of these problems ring a bell in your head? Do you realise that these problems have not been deprecated yet and **modern cryptography** still need to liaise with?


# The Wax
If we particularly thought about the central ideas of the previously mentioned problems, we could easily linked them with our habitual technical slang: it is clear that the issues approached are **authentication** (who are you?) and **integrity** (is this what I should have received?) , core concepts that every sec person should dominate. 
Bringing back the past, I feel forced to bring you the most interesting example of a solution that *potentially* solved our two problems: Seal Wax Stamps.
![]()

Seal Wax Stamps provided a  valid (at that time) method of authentication, as the stamps contained signs or figures in an unique way in order to represent the sign of a person or a family. The interested person would put his letter within an envelope and would subsequently seal it using the wax protecting the integrity of the letter. Throught this operation, the receiver could be certain of the authenticity of the letter as well as the integrity (if the receiver had found the seal broken, the integrity would then have been compromised and if the stamp was a generic, the receiver could not be either sure about the authorship of the letter.

It is very interesting to observe how security paradigms have evolved, in particular, the same idea that accompanies the wax stamp can be found nowadays in almost every secure protocol, the 21st century wax stamp is called HMAC and today we will analyze its importance. 

# HMAC the new wax stamp

MAC or Message Authentication Code is a small code which let us verify the authenticity of a message, in other words is a way of getting a proof of the authenticity and integrity of a message (like our Wax Stamp) . HMAC was the great result of implementing authentication codes using hash functions as MD5 or SHA1.





The idea after HMAC was to provide a robust integrity/authorization mechanisms as it entirely relies in the same security principles found on a regular hash function. A regular use case would look as it follows:
- Dennis wants to communicate with Maria. They both shared a secret key called S
- Dennis wants to send an important message that contains the date of an important appoinment. They message is called M.
- Dennis generates a HMAC which will combine the secret key  S that they both know as well as the message M 
- Maria receives the message M with a small note next to it: the HMAC value
- As Maria knows the secrey key S and the message M she is perfectly able to recreate the HMAC value to verify that it was indeed sent by Dennis and that its content was not modified.



From a mathematical perspective, in order to build a secure HMAC the following items are needed:
- A secret key K which will be shared among the involved parties interested on the transaction
- A message M  (the message which will be transmitted)
- A Hash function H()
- Two strings, each of those is a different padding string. 
```
NOTE: Padding is required in hash functions as they divide the data to be hashed in different blocks of fixed size. In order to keep the consistency it is necessary to "fill" the empty spaces. This is done using padding.
```
INTRODUCE HERE FORMULA


As it has been seen, the theoretical implementation is not rocket science. In the following sections we will see actual implementations of the HMAC as well as


# HMAC as a good idea: real world applications
You probably don't 


HMAC 


## SSH
SSH is an outstanding protocol used worldwide. Incorporates

## TLS 





# HMAC as a bad idea


TTTTT


