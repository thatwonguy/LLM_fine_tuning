# LLM_fine_tuning
## What is fine-tuning and why do it?
**Imagine this problem:** *Your company hires you and wants you to make a genAI chatbot for the company that can answer domain-specific questions for internal users within the company, isolated from the outside world due to privacy concerns, giving your company an edge and streamlining the process for internal employees to access proprietary information and get results to out-side end-users. How to accomplish this?*

---

A lot of chat-gpt style models are out there and they are free and open-source. This is a big deal right now, as of 2024. Why do you ask?
1. Training a large language model from scratch requires huge amounts of data, well-over billions of prompt-style curated question and answer or plain text information obtained from the internet and other places.
2. A very large amount of time and effort cleaning and prepping this data to get it ready for a machine learning model to train itself on (unsupervised learning).
3. Massive amounts of compute power which requires a lot of time or a lot of money or both.

> [!NOTE]
> This is NOT 'prompt-engineering', which is basically interacting with the model as a user to try and get it to change its behaviour or teach it something new by having effective conversations with it. Fine-tuning requires much more coding expertise to accomplish proper > results.

Fortunately for us, there are already companies like google, meta, microsoft, hugging-face, etc that have already provided open-source base-line large language models, like BERT, T-5, GPT, etc, which are trained on huge amounts of general information about the world.  

What we can do now is take one of those base-line models, pull it to the side in our own special environment, take our own proprietary data as a company that only we might have access to and **FINE-TINE** the model on our data...essentially allowing us to add an extra layer of learning on top of the base model that will allow it to become more of an expert on the new information/domain that we have access to at our own company etc. Atleast a minimum of 1000 new pieces of data are required to see a boost in performance.

This is the idea of FINE-TUNING. 

<p align="center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/71634619-b190-49f6-8434-85482e74243d"></p>
