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


# The issue
If we particularly thought about the central ideas of the previously mentioned problems, we could easily linked them with our habitual technical slang: it is clear that the issues approached are **authentication** (who are you?) and **integrity** (is this what I should have received?) , core concepts that every IT-sec person should dominate. 
Bringing back the past, I feel forced to bring you the most interesting example of a solution that *potentially* solved our two problems: Seal Wax Stamps.
![]()

Seal Wax Stamps provided a  valid method of authentication, as the stamps contained signs or figures in an unique way in order to represent the sign of a person or a family. The interested person would put his letter within an envelope and     would subsequently seal it using the wax protecting the integrity of the letter. Throught this operation, the receiver could be certain of the authenticity of the letter as well as the integrity (if the receiver had found the seal broken, the integrity would then have been compromised and if the stamp was a generic, the receiver could not be either sure about the authorship of the letter.

It is very interesting to observe how security paradigms have evolved, in particular, the same idea that accompanies the wax stamp can be found nowadays in almost every internet service that takes security into account, the 21st century wax stamp is called HMAC and we will understand its importance. 

Desire

Action


