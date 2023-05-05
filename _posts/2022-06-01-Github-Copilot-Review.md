---
title:  "Github Copilot Review"
last_modified_at:   2022-06-01 23:57:17
categories: 
  - Developing
tags:
  - AI
  - Developing
description: "Github Copilot Review"

toc: true
toc_label: "Github Copilot Review"
---

GitHub Copilot has been the talk of the programming community in the past few months, creating both awe and fear among us. 
If you haven’t heard of it, Copilot is an AI assistant that helps you code faster. 
It was launched in June 2021 and has become very popular, even though it is still in an early-access stage.

Copilot is powered by OpenAI Codex, an artificial intelligence model that is trained to understand and generate both natural language and, more importantly, source code.
Many programmers haven’t had the chance to try Copilot, yet. That’s why I want to share the current state of Copilot and also my thoughts on how it has changed my workflow.

**What Copilot can do**
Copilot analyzes your source code and makes suggestions accordingly. However, this statement is very vague and doesn’t actually include any detail on how it affects your workflow.
First of all, Copilot knows popular APIs and frameworks and how to use them. Because of this, you can simply describe the task through a comment, or just let Copilot guess your intentions, and let it take care of writing the proper API calls.
In my experience, this feature mostly works smoothly. However, the code hints don’t fully match your purpose and it might introduce subtle bugs in your software, either because of unwanted side effects of some operations or also because of some specific data structures it doesn’t know how to handle.
<!--make gifs on how copilot generates code through comments-->
Furthermore, Copilot can also suggest popular algorithm implementations in various programming languages. 
E.g. you have to sort a list of items, you can just tell Copilot what you are trying to do and it will write the code for you. 
To get even more suitable results, you might also specify the algorithm name in a comment.
For example, you could tell your code writing assistant to sort a list of numbers using merge sort or bubble sort.
<!--make gifs on how copilot generates code through comments-->

**What Copilot cannot do**
