---
{"dg-publish":true,"permalink":"/wiki/technology/ai/auto-gpt-as-a-coding-assistant/","tags":["technology","artificialintelligence"],"created":"Apr 18, 2023, 10:33 PM"}
---


ChatGPT can [self prompt](https://www.facebook.com/reel/264409342607687/), think, and reason with itself before presenting you with a finished product! While it's not fully autonomous and a bit glitchy, we can start to see what the future may look like when we ask A.I. to do a task and it actually thinks like a human.

- [GitHub AutoGPT](https://github.com/Significant-Gravitas/Auto-GPT)
- [AgentGPT](https://agentgpt.reworkd.ai/)
- [Godmode](https://godmode.space/)
- [GitHub Copilot · Your AI pair programmer](https://github.com/features/copilot)

#### AI Agents For Total Development Lifecycle

This guy created a whole website giving voice commands to ChatGPT 4 in 5 minutes for under $1.
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">This is just insane…<br><br>My GPT-4 coding assistant can now:<br>- build and design a frontend<br>- create a backend with working db<br>- correctly hook them up<br>- upload code to GitHub<br>- deploy it to Vercel<br><br>I can now build *complete* apps with nothing more than my voice.<br><br>The future is here! <a href="https://t.co/PrEnCsKY2L">pic.twitter.com/PrEnCsKY2L</a></p>&mdash; Mckay Wrigley (@mckaywrigley) <a href="https://twitter.com/mckaywrigley/status/1644034309253394433?ref_src=twsrc%5Etfw">April 6, 2023</a></blockquote>

https://www.codewand.co/

# The Future Of AI

[Auto-GPT Tutorial - Create Your Personal AI Assistant](https://www.youtube.com/watch?v=jn8n212l3PQ)

ChatGPT is old news. AutoGPT is the new thing. You can give it a set of goals and then it will start to use the GPT4 language model using the open AI API to iteratively prompt the API, get results back, and then use that again to evaluate it and and then come up with the next prompt to reach all the goals you set for it. This is the future of AI. We will all have a personal AI assistant that can basically do tasks for us.

![](https://i.imgur.com/drt9otY.png)

# Create Virtual Environment

```bash
# Create Virtual Environment
$ python -m venv venv
# Activate Environment
$ .\venv\Scripts\activate
# Or if using bash...
$ source venv/Scripts/activate
# Install dependencies in virtual environment
$ pip install -r requirements.txt
# Run the program
$ python -m autogpt
```

To run it:

```bash
source venv/Scripts/activate
python -m autogpt
```

# Actual Experience

https://github.com/Significant-Gravitas/Auto-GPT/discussions/1349

# BabyAGI

There is another repo called [BabyAGI](https://github.com/yoheinakajima/babyagi). Together these two repos are the top 2 most popular GitHub repositories of all time.