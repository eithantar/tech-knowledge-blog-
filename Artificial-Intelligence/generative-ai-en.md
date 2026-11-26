# Generative AI (Gen-AI)

> Read in: **English** | [မြန်မာ](generative-ai-mm.md)

## 1. What Is Generative AI (Gen-AI)?

- **Subset of Deep Learning:** Generative AI is a subset of Deep Learning. This means it is built on some of the most advanced technologies in Artificial Intelligence (AI).
- **Generate new data:** Its special ability is creating new data.
- **Similar to the data it was trained on:** Gen-AI doesn't create things out of nothing. It produces new content that is similar in style and pattern to the data it was trained on.

### What Can Gen-AI Create?

Generative AI can produce the following types of output:

- **Text:** For example, writing emails, telling stories, and answering questions (like ChatGPT).
- **Image:** For example, creating brand-new paintings or photos from a simple text instruction.
- **Audio:** For example, composing new songs or reading text aloud in a human-like voice.
- **Code:** For example, writing programming code for developers.
- **Video:** For example, creating short video clips based on a text description.

### What's the Difference Between Traditional AI and Gen-AI? (A Simple Example)

- **Traditional AI:** Looks at a photo and only classifies or predicts — "Is this a cat or a dog?"
- **Generative AI:** When you say "Draw me a picture of a cat," it creates a brand-new cat image that never existed before.

> **AWS Exam Tip:** For the AWS AI Practitioner exam, remember the key fact: **"Gen-AI is a subset of Deep Learning."**

## 2. What Is a Foundation Model (FM)?

You can think of a Foundation Model as the "foundation" or the "knowledge base" of AI.

- **Reliance on Foundation Model:** To generate new data, we must rely on a Foundation Model. Gen-AI cannot work without one.
- **Trained on wide variety of data:** These models are trained on a huge amount of data from the internet, such as books, articles, images, and code. That's why they know about so many topics.
- **Costly to train:** Building a model this large requires enormous computing power, so training costs can reach millions of dollars.

### Examples and Companies

- **Example (GPT-4o):** The "brain" (Foundation Model) behind ChatGPT is GPT-4o.
- **Major Providers:** Today, major global companies have built their own Foundation Models.

| Company | Models |
|---|---|
| OpenAI | GPT models |
| Meta (Facebook) | Llama models |
| Amazon | Titan models |
| Google | Gemini / BERT models |
| Anthropic | Claude models |

### Two License Types

This is important to know for the exam. Models can be divided into two types:

- **Open-source (free):** Anyone can use and modify them. For example, Meta's Llama or Google's BERT.
- **Commercial License:** You pay a fee or use them under specific terms. For example, models from OpenAI and Anthropic.

### Summary

A Foundation Model is like a university graduate. Because it already has broad general knowledge, we can ask it to do the tasks we need — like writing text or writing code.

## 3. What Is an LLM?

An LLM (Large Language Model) is a type of model ("brain") in the Generative AI world that is built to understand and write text like a human.

- **Generate coherent human-like text:** The main job of an LLM is to create text that sounds human, makes sense, and flows logically.
- **Trained on large corpus of text data:** It's called "Large" because it is trained on a huge amount of data — it has read almost all the websites, books, and articles on the internet.
- **Billions of parameters:** This is a technical term. Parameters measure a model's "learning capacity," and LLMs contain billions of them. (Generally, the more parameters, the more capable the model.)

### What Can an LLM Do? (Language Tasks)

LLMs are skilled at almost any task related to language:

- **Translation:** Translating naturally from one language to another.
- **Summarization:** Shortening long documents so only the key points remain.
- **Question answering:** Answering our questions with facts.
- **Content creation:** Writing emails, social media posts, stories, and more.

### A Well-Known Example

- **GPT-4:** An LLM built by OpenAI and the main technology behind ChatGPT.

> **AWS Exam Tip:** If the exam asks about LLMs, remember that they are based on **"Text Data"** and perform **"Language Tasks."**

## 4. How Generative Language Models Work

**1. Giving a Prompt**

The instruction text we give an LLM when we talk to it or ask it to do something is called a **Prompt**. For example, "Write a paragraph about Myanmar" is a prompt.

**2. Leverage Learned Content**

When we give a prompt, the model uses everything it has learned to generate the answer we want as **new content**. It doesn't search for existing text — it writes something new.

**3. Non-deterministic**

This is an important point. **Non-deterministic** means "hard to predict" or "not always the same output."

- Even if two people give the exact same prompt (for example, "Write a poem"), the LLM's answers can be different.
- Giving a different answer each time is the natural behavior of LLMs.

### Key Takeaway

- **Prompt:** The instruction text we give to the AI.
- **Non-deterministic:** Even when asked the same question, the answer may change and is not always identical.

This non-deterministic nature is also why AI is considered more **creative**.

## 5. How an LLM Chooses Words (Word Selection Process)

**1. Potential Words Alongside Probabilities**

When an LLM builds a sentence, it doesn't write the next word perfectly in one go. First, it calculates a **list of potential next words** and the **probability** of each one.

For example, imagine the sentence: **"The cat sat on the…"**

The AI might calculate the next word like this:

| Word | Probability |
|---|---|
| Mat | 80% |
| Floor | 10% |
| Chair | 5% |
| Cloud | 0.01% |

**2. Algorithm Selects a Word**

Once it has this list of probabilities, an algorithm selects one word. It usually picks the word with the highest probability, but sometimes it picks a less likely word to be more creative.

### Why Is This Important to Know?

This is the reason behind the **non-deterministic** behavior mentioned earlier.

Because the algorithm doesn't always pick the most likely word (depending on the **Temperature** setting), we can get different answers even when we ask the same question.

### Key Point

An LLM can be described as a **"Next-word prediction engine."** Rather than simply understanding the meaning of words, it chooses each word based on mathematical **probability**.
