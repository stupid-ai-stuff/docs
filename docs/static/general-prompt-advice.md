---
title: General Prompt Advice
layout: page
permalink: /prompt-general/
---


## Overview
This document will cover the basics of writing good prompts - with a focus on real world scenarios. 

* Do not remove this line (it will not be displayed)
{:toc}

<!-- TODO: More content needs to go here -->

## Writing Effective Prompts
Writing an effective prompt is not the same as a *google query*. A *google query* is looking for document that 'contain' that term or a relevant term, and return those documents to you. It is not completing a task. The use of GenerativeAI / LLMs is a completely different matter. You are asking a machine to complete the entire task. 

When writing a prompt, I find it helpful to position yourself as writing instructions to complete a task, where the person completing the task cannot interact with you until the task is fully complete. If you were asking a human to do this, you would provide adequate instructions to ensure that they could complete the task. Common examples for this include: 

### Example Scenarios

#### Intensive Care Scenarios
Often in healthcare settings, an intensive care procedure and therapy may span multiple shifts. During 'Rounds' care practicioners often will provide detailed instructions and references to any procedures completed, steps take, and future steps expected. While they may refer to 'common medical knowledge' for certain tasks, such as applying a bandage, **all** additional detail is welcomed, as it may provide specific care instructions for that patient. 

#### Critical Equipment Scenarios
Many industries such as Power Generation where mistakes can be instantly fatal, due to the nature of the work. When humans are inspecting this equipment the instructions provided are exact without any detail left out, to ensure that safety is achieved. Due the amount of electricity passing through power generation equipment, a detail left out of a safety procedure can and often will cause a technician to lose their life. Because of this, safety instructions are written in such a way that they assume that the reader has access to no other knowledge than the document they are reading, as well as 'common knowledge.

### Common Knowledge
The AI has been trained on more information, and is able to recite more knowledge than any human is capable of. However, similar to a human, its knowledge on all of these things is not perfect. It is likely to produce fuzzy results, especially with numeric values. We will discuss some of the categories that it struggles with as well as it accels with.

#### Numerics
The AI does not have access to factual / up to date information on any subject relating to numerics. This Includes sports stats, stock market information, financial reports, and weather. This information is best collected before interacting with the AI and passed along via [In Context Information](#in-context-information). For a deep dive on this concept please see [Retrieval Augmented Generation]({% link retrieval-augmented-generation.md %}).

#### Axioms
The AI does understand many axioms and logic concepts.
> Note: Try to use a known axiom with the AI. If it does not work, attempt to explain the axiom to the AI. I find that using the summary paragraph from wikipedia is generally enough.

#### Conversational Context
The AI is **exceptional** at this. Given that this is a core language concept, the AI  be able to find this context easily. Explain using text as you would explain the conversation / social interaction to another human.

### Verbosity
To use an old physical-security addage: *"when it doubt, write it out"*, the concept here is, always feel free to include additional context for the AI. 


## In Context Information
The more information you include the better. Remember that the AI's scope is always global, as it has no incoming context about your request. 

### Examples
For this section, I would like you to think about how a human would perform with the following instructions, given no other context. Remember that this human does not have access to the internet, nor does it have the ability to follow up on questions. 

#### Example 1 - Produce Content
In this example we will ask the AI to do our homework, because obviously. In this example we will cover what a bad prompt looks like, why it is bad, and what a good prompt looks like.

##### Bad Prompt
```text
Write my history assignment for me.
```

This is an example of a poor prompt because it is missing almost all of the information that is required. If you were to give this task to a human they would most likely respond with *at least* the following questions.
- What level is the homework expected at? 2nd grade? PHD history?
- What is the title of the class?
- What is the title of the history lesson the class is currently working on?
- What are the length requirements for the paper?
- How are citations handled / required?
- Are there any specific events in history that are being covered that should appear in the paper.

##### Good Prompt

```
Write an essay detailing the use of the Friedrichshafen G.II aircraft during World War I. This essay is intended is for 'World War I History' a Graduage Study course for a History Major. The document should be at least 10 pages. Write the Document cover the following items. Format the output as Markdown:
- The events leading up to the development of the aircraft
- The development of the aircraft
- Its inclusion in the war by the German Military
- Specific uses / notable uses of the aircraft during World War I.
- Specifics about the aircraft.
```

As we can see from the prompt above, we covered many of the relevant points that the AI needs to accomplish the task. 