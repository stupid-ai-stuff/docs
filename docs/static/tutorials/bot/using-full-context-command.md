---
title: Retriveal Augmented Generation
permalink: /tutorials/bot/using-full-context-command/
---

![Service Icon](https://dcbadge.vercel.app/api/server/9Q5Y5WB9UX?style=flat&theme=default-inverted)

## Synopsis
This article will cover the use of the `/gpt4 full_context` command in discord. This command uses the [Discord Application Command Interface](https://discord.com/developers/docs/interactions/application-commands) to interact with the user. This means that all interactions begin with a `/` character.

{:toc}

## Command Use
The `/gpt4 full_context` command is intended for a more exact approach to interacting with the AI. It is not designed to run conversationally, and responses will not be stored in the history of the chat. 

> **It is highly recommended not to use `/` commands inside of a chat channel other than `/chat *` commands**

The expectation for use of the `/gpt4 full_context` is that the user will pre-prepare a text file (`.txt` or `.md`) for use with the bot. While conversion from Word and other formats is supported, it does not yeild expected results at this time. 

![An image of the Discord Inteface showing the basic use of the Full Context Command](../../../assets/images/using-full-context-command/1-first-display.png)

By default, the command will only **require** you to input the [System Message](../../concepts/open-ai/chat-completions.md#system-message), however this is **not an effective way to use the command**. For short / simple queries - it is best / most intuitive to use the Chat interface. It is highly recommended that you fill out all the other parameters.

### System Message (`system_msg`)
The System Message sets the 'global rules' of the interaction. Often when working with a pre-prepared document with this command, it is not necessary to include a complex system message. If you find yourself processing *many* different files and including the same prompt fragments in them (for example "`Format the output as Markdown.`"), you can place these fragments in the System Message. Please see the [Chat Completions](../../concepts/open-ai/chat-completions.md#system-message) article for more information on how the **System Message** differes from **User Messages** and **Assistant Messages**.

For processing most prompts where most of the information is included in the uploaded file, the System Message can be set to "`You are a helpful AI Assistant. Follow all instructions from the user.`". By using this system message, you are ensuring the the user message (the uploaded file) is unrestricted in its instructions. 

### Language Model (`model`)

![An image of the Discord Inteface showing the basic use of the Full Context Command](../../../assets/images/using-full-context-command/2-selecting-a-model.png)

It is **always** recommended to use the `Azure Secured: core-gpt-4` model. The `32k` variant of the model does not include additional performance, it is designed to handle enormous queries, and is thusly priced higher. Usage of the `32k` variant for small queries is unnecessary. 

### Token Budget (`max_tokens`)
The `max_tokens` argument is used to set a **maximum** budget, in [tokens](../../concepts/open-ai/tokens.md), for the produced content. This is most used for limiting the size of your produced content. For example for LLM queries that produce a `yes`/`no` output, the `max_tokens` parameter can be set to `3`. For an essay length output, the `max_tokens` parameter might be set to `2000`. 

#### Billing Implications
Please Note that billing only occurs for **used tokens** not the maximum budget. For example, the prompt `say hello` with a max tokens of `6000` will only use a total of `12` tokens (`10` for prompt, `2` for completion.

![An image of the Discord Inteface showing the use of the MAX TOKENS parameter](../../../assets/images/using-full-context-command/3-short-prompt-high-budget-max-tokens.png)


![An image of the Discord Inteface showing the use of the MAX TOKENS parameter](../../../assets/images/using-full-context-command/4-short-prompt-high-budget-max-tokens-result.png){:width="500px"}


In addition, the output of the `/gpt4 full_context` command will show the billing usage of each invocations. If you are using this tool to craft prompts for programatic use, you can consume this information to better prepare your `max_tokens` parameter.

#### Doing Math 😲
For each of the models, you have a fixed and finite **maximum** token budget to work from. The formula to compute your `max_token` remaining budget is simple.

```
model_limit - prompt_tokens = remaining_tokens
```
