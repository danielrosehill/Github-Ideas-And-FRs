# OpenWebUI - A "Meta" Assistant To Act As An Instance Sidekick

25-Jan-25

Final idea in this batch, but I think this would be really cool. 

I've been thinking about ways to configure an orchestration assistant in my instance. 

The functionality I'm targeting is having an assistant which has in its context a list of all the assistants provisioned in the instance. Ideally, this would be a dynamic datastore reflecting the current models configured. But I'll map out a few other potential use cases just to be ambitious. 

## Use-Case 1: Assistant knows which custom models you've configured & recommends one for your need/use-case

If there were any way to pass the current model list as context to an assistant (perhaps dynamically and directly into the RAG store), users could have an assistant, which could serve as the manager for the overall chat interface. 

For want of a better world, I'm going to call the orchestration assistant *The Bouncer*! Perhaps it could be the modern incarnation of the Microsoft Word paper clip guy of yesteryear (I'm showing my age, I know!)

**User:** Is there an assistant in this workspace that could help me to find a product on an e-commerce site? 
**Bouncer:** Yup, you've configured the Product Research Assistant. Here's the link. Do you want me to connect you? 

I'm aware that the handover functionality is quite an elaborate implementation. But the basic one of just being able to provide a link from the current model store would be great in its own right.

## Use-Case 2: Prompt to LLM recommendation

The second use case for an "instance assistant" might be guiding the user towards a particular large language model. This would again require live contextual data about the models that the user has provisioned and configured. But if this data could be connected and queried against in real time, this could be very valuable. 

**User:** I have a pretty detailed software generation prompt. I'm going to paste it at the end of this one. Have a look at it and recommend which of the models in my instance you think would be best prepared to handle this?

**Bouncer:** For this kind of detailed Python prompt, two models stand out to me that you have currently configured. Sonnet 3.5 and Deep Seek 3. Both have strong benchmarks in code generation and would be able to handle this well. 

## Use-Case 3: Prompt to LLM recommendation 2 - cost optimisation

Like perhaps many, it's taken me a lot of time to embrace the idea of using older models when newer functionalities just aren't required. There's something appealing about using the latest and greatest, but I've seen that models like 3.5 can be highly effective for simple tasks like text editing. 

As Open Web UI excels in model configuration and customization, I think it would be pretty cool if the assistant could make intelligent recommendations for more cost effective models where they can be best used:

**User:** Okay, I have a batch of text that I need to rewrite from the second to the third person. Can you recommend a good model for this purpose from those I have in my instance? 

**Bouncer:** Sure, GPT 3.5 Turbo provided by either OpenAI or OpenRouter would be perfect for this and a lot more economical than your current default model of 4.0.  

---

# Connecting agent to the other parts of the instance!

Here are some thoughts about how this idea could be really fleshed out.

I'll organize these according to the module that the assistant would need to integrate with:

## With knowledge stores / vector DB (utility: probably quite marginal)

The user could query the assistant about various things related to the knowledge stores that the user has configured in the instance. This particular functionality might make a lot more sense in a multi tenant deployment. 

If an instance were significantly scaled and there were perhaps hundreds of different knowledge data sets configured, a user might wish to use an assistant as a source of pathfinder. 

**User**: I'm working on populating a knowledge store with our SOPs. Do we already have a knowledge pool configured for that? 

## Prompt library connection (utility: potentially very high!)

If the assistant had dynamic knowledge of the prompt library in the instance, it could be very useful in guiding the user towards existing prompts thereby saving them from having to create prompts that either they or the other workspace users had already drafted.

**User**: I remember writing a prompt last week attempting to find a CRM. I laid out our spec in quite a lot of detail. Could you check the print library and try to find the prompt and give me the link to?

## Tools (Ditto)

Likewise, tools could be queried. 

## Chat History Queries

User asks the assistant with natural language queries about the chat history. 

Assistant could provide a direct link to the chat. 

Chat. His truth can quickly scale into the thousands. At which point pinpointing a previous conversation with useful information can become quite challenging. 

Perhaps an assistant with a vectorized footprint of the chat history might actually be more effective for finding chats than the search functionality. 

## MCP / Configuration Tweaking

Finally, a very ambitious one!

As agentic and MCP capabilities become more practicable, Perhaps we might consider the idea that an assistant could actually tweak the configurations in Open Web UI itself!

I have no idea what internal APIs are being used under the hood. But if an assistant had access to them, perhaps they could actually be a configuration sidekick. 

One use case I've made of assistants in this respect (without the agentic capabilities) Is having them debug RAG settings. 

Thinking more widely, perhaps they could adjust the temperature on models to better achieve the desired performance.  Edit configuration texts. Suggest API and tool additions. Etc.


