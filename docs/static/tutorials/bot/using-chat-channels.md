---
title: Using Chat Channels
permalink: /tutorials/bot/using-chat-channels/
---

{% include under-construction.html %}

The Chat Channels are used for Conversational chat with the AI. This is useful when your inputs are **small** to **medium** in length.

### Channels
The **Chat Channels** in many servers come in a few varieties. We are currently on Version 4 of the **Stupid AI Stuff - Chat**, and all supporting channels will be marked as such.

### Chat Reset
The `/chat reset` command is an *oft* overlooked and extremely useful command. This command resets the point in time where chat messages cut off. The first message sent after this command in a channel will be equivalent of the chat having no history.


### Technical Interaction
The bot uses the [Chat Completions]({% static/concepts/open-ai/chat-completions.md %}) interface <sup>[[1]](#security)</sup>.

In order to do this efficiently, all messages sent to and from a **Chat Channel** are stored in a database.

