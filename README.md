# OVERVIEW - LLM_fine_tuning
## What is fine-tuning and why do it?
**Imagine this problem:** *Your company hires you and wants you to make a genAI chatbot for the company that can answer domain-specific questions for internal users within the company, isolated from the outside world due to privacy concerns, giving your company an edge and streamlining the process for internal employees to access proprietary information and get results to out-side end-users. How to accomplish this?*

---

A lot of chat-gpt style models are out there and they are free and open-source. This is a big deal right now, as of 2024. Why do you ask?
1. Training a large language model from scratch requires huge amounts of data, well-over billions of prompt-style curated question and answer or plain text information obtained from the internet and other places.
2. A very large amount of time and effort cleaning and prepping this data to get it ready for a machine learning model to train itself on (unsupervised learning).
3. Massive amounts of compute power which requires a lot of time or a lot of money or both.

> [!NOTE]
> This is NOT 'prompt-engineering', which is basically interacting with the model as a user to try and get it to change its behaviour or teach it something new by having effective conversations with it. Fine-tuning requires much more coding expertise to accomplish proper results.

Fortunately for us, there are already companies like google, meta, microsoft, hugging-face, etc that have already provided open-source base-line large language models, like BERT, T-5, GPT-3, etc, which are trained on huge amounts of general information about the world.  

What we can do now is take one of those base-line models, pull it to the side in our own special environment, take our own proprietary data as a company that only we might have access to and **FINE-TINE** the model on our data...essentially allowing us to add an extra layer of learning on top of the base model that will allow it to become more of an expert in the domain and on the private data at our company. Atleast a minimum of 1000 new pieces of data are required to see a boost in performance.

This is the idea of FINE-TUNING. 

<p align="center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/71634619-b190-49f6-8434-85482e74243d"></p>

There are 3 general ways one can fine-tune the base model:
1. **Pytorch / Tensorflow** (libraries that allow you to get deep into the specifics of the model and dissect it like a surgeon)
2. **HuggingFace** (library developed by huggingface providing a mid-level amount of control to go in and obtain and modify the base-models and fine-tune and use them)
3. **Llama (Lamina)** library (another library that provides a very abstracted and high level approach to accomplish fine-tuning with very little amount of code)

If you look at `01_Why_finetuning.ipynb` you will find a demo, with code, of the difference between a base-model and the results it would provide compared to another model that is fine-tuned on the base model, which clearly provides much better results.

# How to fine-tune?
Take a look at  `02_Where_finetuning_fits_in.ipynb`. The Lamina library is being used for quick demonstration purposes. You can see that Lamina company data is being used to fine-tune a pre-trained base model and the output of the model is being saved as a `jsonl` (each line is a json object) format or saved back into huggingface for the world to use by pulling from the cloud.

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/fff2a9c2-14ec-4896-85af-dbf8621544d5"></p>

# "Instruction" fine-tuning and why?  
This type of fine-tuning technique is needed and was actually utilized to turn the GPT-3 model into chatgpt, and allowed it to obtain its "chatting" powers. This step will allow your model to go from being used by only geeks and nerds at your company to everyone at your company wanting to use it and then-some. It provides a better user-interface, better model-interaction, and impresses all the big-wig-C-suite-executives at your company. 

If you take a look at `03_Instruction_tuning.ipynb` you can see some code on how these chat powers were obtained with *instruction fine-tuning*.

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/e61d885b-f185-41cd-8ee9-c559a1c997e8"></p>

# Data Preparation
The type of data you need to prepare is very important. Everybody at this point understands and knows the saying ***"garbage in = garbage out"***. This still holds true with large language models. Find a quick and concise break down of the kind of data you want to start prepping for fine-tuning:

| Better                                           | Worse                                          |
|---------------------|------------------|
| High Quality | Lower Quality |
| Diversity in the data | homogenous and no diversity in data
| Real actual data | fake pretend data used just to create more data
| More data in general (the more the better) | Less data or not enough data

The other thing to take into consideration is tokenization. This is a key concept to understand and implement. You have to convert the words in the language you are using into "tokens" for the machine learning algorithm to process correctly and learn from. The words are decoded into number values and the decoded back into the english language for the end-user.

Take a look at notebook `04_Data_preparation.ipynb` to see this data prep step in action with real code.

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/2343e3b5-ba63-49ca-a0ab-667c7c80f3f9"></p>

# Training Process (putting the above together)

Take a look at `05_Training_combining_01_to_04.ipynb` and you can see how it all comes together. 

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/c1915eb0-f241-4151-b7e6-0d8522f220e6"></p>

The first few cells of the notebook code uses pytorch and hugging face libraries to fine_tune a small model using CPU power (with demonstration of how to call GPU power if it is available to dramatically speed up the process). The final few cells of the notebook code show how you can achieve the same thing with a highly abstracted lamina-library approach with just a few lines of code. You can see that it also provides a neat output of the results for some preliminary evaluation.

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/144036e2-d895-4362-a1e4-cba857d326c0"></p>

Dive into `05_Training_combining_01_to_04.ipynb` and you can also spot how censorship and moderation is achieved. You simply train the model to respond and refuse to provide answers to specific types of questions.

# Evaluation and Iteration  
This brings us to the next step of the process, which is also important, and that is, how to evaluate and iterate over your fine-tuning process/model in order to make it better. Why? Because bad results are useless ultimately right `😜`?

You need good test data to carry out proper evaluation. See below:

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/e8945c71-959e-4fcc-a0c4-2cae357cd269"></p>

An approach to model evaluation for LLMs is to use established benchmarks and take the average. A few are shown below:

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/82e680df-8e55-43d6-929d-9241e4d2e169"></p>

Improving the model after obtaining the evaluation of the data with the test data is an ITERATIVE process. You will run an error analysis of the evaluation, categorize the errors and fix those errors as shown below:

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/54aea5b7-8f08-490d-b6bc-624a03920ceb"></p>

Take a look at `06_Evaluation.ipynb` for the example notebook showing actual code to carry out what was described above.

# Considerations on getting started

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/f21f08bc-8a83-489e-8537-feb2b48d8ad8"></p>

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/e8b21837-449d-42fc-a0be-e7d0e2f5eec2"></p>

For those who are more experienced with training machine learning models and deploying online, you understand better than most that memory and computational power are necessary in being able to properly train and use these models. The below chart is a useful breakdown of what would typically be required to achieve this for a large langauge model, based on what kind of data you are working with:

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/dfcf205e-7eaf-4ae7-9fa1-436892a2c34c"></p>

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/dca2fc45-0632-48af-a6e9-f69f8232b2f6"></p>

A high level view of a very effective method of fine-tuning a model is to take the base model that is already pre-trained and available on platform like hugging-face and freeze the main layers of the model, and only train the outer layers before merging with the base model layer at the inference stage:

<p align = "center"><img src="https://github.com/thatwonguy/LLM_fine_tuning/assets/78534460/981de2a9-081a-477d-91df-3c0d25be47e7"></p>

# Conclusion 

This was meant to be a quick high level overview with real working code on how to fine-tune a large language model. Of course there is much more detail that can be expanded upon such as utilizing pytorch and tensorflow to really get into the details of the large language models and neural networks and freeze base layers and work on outer hidden layers etc...but, none-the-less, hopefully this provides a solid starting point into understanding how to fine-tune an LLM and create your own "ChatGPT"! 
