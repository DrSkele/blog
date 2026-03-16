---
url: https://medium.com/beyond-localhost/i-thought-i-knew-system-design-until-i-met-a-google-l7-interviewer-239385b24881
tags:
  - backend
  - article
publish: true
---
# [Article : I Thought I Knew System Design Until I Met a Google L7 Interviewer](https://medium.com/beyond-localhost/i-thought-i-knew-system-design-until-i-met-a-google-l7-interviewer-239385b24881)

This article is about what author noticed and learned during his interview. It was about revealing what the interviewee knows and thoughts behind the decisions. In the interview, he managed to answer well on what he *knew*, but not on *why* that knowledge solves the problem.

## Reflex for patterns

The author is warning the readers about developers applying the patterns subconsciously. Letting the design the way it is because you saw it in a book or have done that way previously, without really thinking about the *why* behind the architecture or design being needed in the first place. This is a bad reflex that develops when you do not reason for the decisions you make.

## Think of the trade off

Every pattern has its trade-offs. Without considering them thoroughly on it will only make the system complex. The author suggests to training the thinking process by trying to remove the existing component from the system you designed. If the system still works well without it, you don't actually need it. If not, you should explain what metric proves its necessity.

## Personal thoughts

This article, I truly agree with it. I once studied the architectures and design patterns and used it because *other projects used it*. But then when applied to my project, it did not feel quite right. It only increased complexity and I was just writing another boilerplate. 

That's when I started to look deeper and find out the decisions behind the design. At first, the clean architecture was nothing more than a separation of directories. After learning the thoughts and background history behind the finding of clean architecture, I started to use the architecture with my own decisions. I decided to make the model, use cases, and repositories, becasue I sought them to model user flow.

Although I am an Android developer and the article is about system design that I did not have experience with, but the core message still applies to every developer. Because designing patterns and architecture are not limited to a single field.
