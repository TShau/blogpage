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
![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/github-copilot.png){: .align-center}
GitHub Copilot has been the talk of the programming community in the past few months, creating both awe and fear among us. 
If you haven’t heard of it, Copilot is an AI assistant that helps you code faster. 
It was launched in June 2021 and has become very popular, even though it is still in an early-access stage.

Copilot is powered by OpenAI Codex, an artificial intelligence model that is trained to understand and generate both natural language and, more importantly, source code.
Many programmers haven’t had the chance to try Copilot, yet. That’s why I want to share the current state of Copilot and also my thoughts on how it has changed my workflow.

## What Copilot can do
Copilot analyzes your source code and makes suggestions accordingly. However, this statement is very vague and doesn’t actually include any detail on how it affects your workflow.
First of all, Copilot knows popular APIs and frameworks and how to use them. Because of this, you can simply describe the task through a comment, or just let Copilot guess your intentions, and let it take care of writing the proper API calls.
In my experience, this feature mostly works smoothly. However, the code hints don’t fully match your purpose and it might introduce subtle bugs in your software, either because of unwanted side effects of some operations or also because of some specific data structures it doesn’t know how to handle.

<!--make gifs on how copilot generates code through comments-->
Furthermore, Copilot can also suggest popular algorithm implementations in various programming languages. 
E.g. you have to sort a list of items, you can just tell Copilot what you are trying to do and it will write the code for you. 
To get even more suitable results, you might also specify the algorithm name in a comment.
For example, you could tell your code writing assistant to sort a list of numbers using merge sort or bubble sort.
<!--make gifs on how copilot generates code through comments-->

<!-- Messaeg Suggestion-->

## What Copilot cannot do
Copilot has many capabilities, but it is far from being able to replace a human programmer or build a complex system on its own.

One of the main limitations of Copilot is handling multiple files in a single codebase. It often confuses names and data types when importing from other files. Rather than looking aat the whole codebase, the copilot is currently focusing at the current file only. This can lead up to calling methods that are not imported, and must therefore be added by a human.

As previously mentioned Copilot sometimes my introdice bugs in your code. It may offer code completions that look right or even clever but can cause subtle, hard to find errors instead. That’s why you should always review Copilot’s suggestions for hidden bugs or potential unwanted consequences. Remember, Copilot is as the name suggests, just an assistant and you are the one responsible for developing software.

Last but not least, we are still talking about AI generating your code. There might be an issue with Code ownership and intellectual property. If your code was mainly generated by GitHub Copilot, do you truly have the rights of the code then? Since Copilot was trained on code that was contributed by other people, could there be a violation of intellectual property, if you were to use it commercially? 
THose questions can be concerning especially for companies, who want to stay compliant to these topics.

## My Experience with Copilot so far
Less time on websearching : While coding, I often find myself on situations where I have to websearch to find the correct syntax, or algorithms. With GitHub Copilot, I am able to skip a lot of it by typing a few words on describing the function + ´´Tab´´. It was then able to correctly fill some line of codes with patterns that work well with corresponding frameworks and libraries. A great time saver!
Because of that it is also great for working with new APIs and frameworks. 
Copilot often recognizes the technologies I use and can suggest whole lines of code or patterns that fit the specific context I’m in. This helps me focus more on coding rather than looking up the API documentation. I would still advise reading the documentation for structures and calls that are not so clear. Especially since they may have some implementation details that Copilot does not know about.

In conclusion, Copilot is a great tool for developers that helps you boost your productivity by offering smart code completions based on the context. It usually does a good job and greatly reduces your writing time. However it cannot build a system on its own or guarantee that its suggestions are always correct. That’s why you should always review the code completions for possible bugs and unwanted consequences. Remember, it’s just an AI assistant and you are the one responsible for developing the software.
