---
sidebar_position: 18
---

# 9 Mastering agent prompts with prompt flow

### This chapter covers

- Understanding systematic prompt engineering and setting up your first prompt flow
- Crafting an effective profile/persona prompt
- Evaluating profiles: Rubrics and grounding
- Grounding evaluation of a large language model profile
- Comparing prompts: Getting the perfect profile

In this chapter, we delve into the Test Changes Systematically prompt engineering strategy. If you recall, we covered the grand strategies of the OpenAI prompt engineering framework in chapter 2. These strategies are instrumental in helping us build better prompts and, consequently, better agent profiles and personas. Understanding this role is key to our prompt engineering journey.

Test Changes Systematically is such a core facet of prompt engineering that Microsoft developed a tool around this strategy called *prompt flow*, described later in this chapter. Before getting to prompt flow, we need to understand why we need systemic prompt engineering.

## 9.1 Why we need systematic prompt engineering

Prompt engineering, by its nature, is an iterative process. When building a prompt, you’ll often iterate and evaluate. To see this concept in action, consider the simple application of prompt engineering to a ChatGPT question.

You can follow along by opening your browser to ChatGPT ([https://chat.openai.com/](https://chat.openai.com/)), entering the following (text) prompt into ChatGPT, and clicking the Send Message button (an example of this conversation is shown in figure 9.1, on the left side):

can you recommend something

![figure](assets/9-1.png)

##### Figure 9.1 The differences in applying prompt engineering and iterating

We can see that the response from ChatGPT is asking for more information. Go ahead and open a new conversation with ChatGPT, and enter the following prompt, as shown in figure 9.1, on the right side:

Can you please recommend a time travel movie set in the medieval period.

The results in figure 9.1 show a clear difference between leaving out details and being more specific in your request. We just applied the tactic of politely Writing Clear Instructions, and ChatGPT provided us with a good recommendation. But also notice how ChatGPT itself guides the user into better prompting. The refreshed screen shown in figure 9.2 shows the OpenAI prompt engineering strategies.

![figure](assets/9-2.png)

##### Figure 9.2 OpenAI prompt engineering strategies, broken down by agent component

We just applied simple iteration to improve our prompt. We can extend this example by using a system prompt/message. Figure 9.3 demonstrates the use and role of the system prompt in iterative communication. In chapter 2, we used the system message/prompt in various examples.

![figure](assets/9-3.png)

##### Figure 9.3 The messages to and from an LLM conversation and the iteration of messages

You can also try this in ChatGPT. This time, enter the following prompt and include the word *system* in lowercase, followed by a new line (enter a new line in the message window without sending the message by pressing Shift-Enter):

system

You are an expert on time travel movies.

ChatGPT will respond with some pleasant comments, as shown in figure 9.4. Because of this, it’s happy to accept its new role and asks for any follow-up questions. Now enter the following generic prompt as we did previously:

can you recommend something

![figure](assets/9-4.png)

##### Figure 9.4 The effect of adding a system prompt to our previous conversation

We’ve just seen the iteration of refining a prompt, the prompt engineering, to extract a better response. This was accomplished over three different conversations using the ChatGPT UI. While not the most efficient way, it works.

However, we haven’t defined the iterative flow for evaluating the prompt and determining when a prompt is effective. Figure 9.5 shows a systemic method of prompt engineering using a system of iteration and evaluation.

![figure](assets/9-5.png)

##### Figure 9.5 The systemic method of prompt engineering

The system of iterating and evaluating prompts covers the broad Test Changes Systemically strategy. Evaluating the performance and effectiveness of prompts is still new, but we’ll use techniques from education, such as rubrics and grounding, which we’ll explore in a later section of this chapter. However, as spelled out in the next section, we need to understand the difference between a persona and an agent profile before we do so.

## 9.2 Understanding agent profiles and personas

An *agent profile* is an encapsulation of component prompts or messages that describe an agent. It includes the agent’s persona, special instructions, and other strategies that can guide the user or other agent consumers.

Figure 9.6 shows the main elements of an agent profile. These elements map to prompt engineering strategies described in this book. Not all agents will use all the elements of a full agent profile.

![figure](assets/9-6.png)

##### Figure 9.6 The component parts of an agent profile

At a basic level, an *agent profile* is a set of prompts describing the agent. It may include other external elements related to actions/tools, knowledge, memory, reasoning, evaluation, planning, and feedback. The combination of these elements comprises an entire agent prompt profile.

Prompts are the heart of an agent’s function. A prompt or set of prompts drives each of the agent components in the profile. For actions/tools, these prompts are well defined, but as we’ve seen, prompts for memory and knowledge can vary significantly by use case.

The definition of an AI agent profile is more than just a system prompt. Prompt flow can allow us to construct the prompts and code comprising the agent profile but also include the ability to evaluate its effectiveness. In the next section, we’ll open up prompt flow and start using it.

## 9.3 Setting up your first prompt flow

Prompt flow is a tool developed by Microsoft within its Azure Machine Learning Studio platform. The tool was later released as an open source project on GitHub, where it has attracted more attention and use. While initially intended as an application platform, it has since shown its strength in developing and evaluating prompts/ profiles.

Because prompt flow was initially developed to run on Azure as a service, it features a robust core architecture. The tool supports multi-threaded batch processing, which makes it ideal for evaluating prompts at scale. The following section will examine the basics of starting with prompt flow.

### 9.3.1 Getting started

There are a few prerequisites to undertake before working through the exercises in this book. The relevant prerequisites for this section and chapter are shown in the following list; make sure to complete them before attempting the exercises:

- *Visual Studio Code (VS Code)* —Refer to appendix A for installation instructions, including additional extensions.
- *Prompt flow, VS Code extension* —Refer to appendix A for details on installing extensions.
- *Python virtual environment* —Refer to appendix A for details on setting up a virtual environment.
- *Install prompt flow packages* —Within your virtual environment, do a quick `pip` `install`, as shown here:

```
pip install promptflow promptflow-tools
```

- *LLM (GPT-4 or above)* —You’ll need access to GPT-4 or above through OpenAI or Azure OpenAI Studio. Refer to appendix B if you need assistance accessing these resources.
- *Book’s source code* —Clone the book’s source code to a local folder; refer to appendix A if you need help cloning the repository.

Open up VS Code to the book’s source code folder, `chapter` `3`. Ensure that you have a virtual environment connected and have installed the prompt flow packages and extension.

First, you’ll want to create a connection to your LLM resource within the prompt flow extension. Open the prompt flow extension within VS Code, and then click to open the connections. Then, click the plus sign beside the LLM resource to create a new connection, as shown in figure 9.7.

![figure](assets/9-7.png)

##### Figure 9.7 Creating a new prompt flow LLM connection

This will open a YAML file where you’ll need to populate the connection name and other information relevant to your connection. Follow the directions, and don’t enter API keys into the document, as shown in figure 9.8.

![figure](assets/9-8.png)

##### Figure 9.8 Setting the connection information for your LLM resource

When the connection information is entered, click the Create Connection link at the bottom of the document. This will open a terminal prompt below the document, asking you to enter your key. Depending on your terminal configuration, you may be unable to paste (Ctrl-V, Cmd-V). Alternatively, you can paste the key by hovering the mouse cursor over the terminal and right-clicking on Windows.

We’ll now test the connection by first opening the simple flow in the `chapter_09/promptflow/simpleflow` folder. Then, open the `flow.dag.yaml` file in VS Code. This is a YAML file, but the prompt flow extension provides a visual editor that is accessible by clicking the Visual Editor link at the top of the file, as shown in figure 9.9.

![figure](assets/9-9.png)

##### Figure 9.9 Opening the prompt flow visual editor

After the visual editor window is opened, you’ll see a graph representing the flow and the flow blocks. Double-click the recommender block, and set the connection name, API type, and model or deployment name, as shown in figure 9.10.

![figure](assets/9-10.png)

##### Figure 9.10 Setting the LLM connection details

A prompt flow is composed of a set of blocks starting with an `Inputs` block and terminating in an `Outputs` block. Within this simple flow, the `recommender` block represents the LLM connection and the prompt used to converse with the model. The `echo` block for this simple example echoes the input.

When creating a connection to an LLM, either in prompt flow or through an API, here are the crucial parameters we always need to consider (prompt flow documentation: [https://microsoft.github.io/promptflow](https://microsoft.github.io/promptflow)):

- *Connection* —This is the connection name, but it also represents the service you’re connecting to. Prompt flow supports multiple services, including locally deployed LLMs.
- *API* —This is the API type. The options are `chat` for a chat completion API, such as GPT-4, or `completion` for the older completion models, such as the OpenAI Davinci.
- *Model* —This may be the model or deployment name, depending on your service connection. For OpenAI, this will be the model’s name, and for Azure OpenAI, it will represent the deployment name.
- *Temperature* —This represents the stochasticity or variability of the model response. A value of `1` represents a high variability of responses, while `0` indicates a desire for no variability. This is a critical parameter to understand and, as we’ll see, will vary by use case.
- *Stop* —This optional setting tells the call to the LLM to stop creating tokens. It’s more appropriate for older and open source models.
- *Max tokens* —This limits the number of tokens used in a conversation. Knowledge of how many tokens you use is crucial to evaluating how your LLM interactions will work when scaled. Counting tokens may not be a concern if you’re exploring and conducting research. However, in production systems, tokens represent the load on the LLM, and connections using numerous tokens may not scale well.
- *Advanced parameters* —You can set a few more options to tune your interaction with the LLM, but we’ll cover that topic in later sections of the book.

After configuring the LLM block, scroll up to the Inputs block section, and review the primary input shown in the user\_input field, as shown in figure 9.11. Leave it as the default, and then click the Play button at the top of the window.

![figure](assets/9-11.png)

##### Figure 9.11 Setting the inputs and starting the flow

All the blocks in the flow will run, and the results will be shown in the terminal window. What you should find interesting is that the output shows recommendations for time travel movies. This is because the recommender block already has a simple profile set, and we’ll see how that works in the next section.

### 9.3.2 Creating profiles with Jinja2 templates

The flow responds with time travel movie recommendations because of the prompt or profile it uses. By default, prompt flow uses Jinja2 templates to define the content of the prompt or what we’ll call a *profile.* For the purposes of this book and our exploration of AI agents, we’ll refer to these templates as the profile of a flow or agent.

While prompt flow doesn’t explicitly refer to itself as an assistant or agent engine, it certainly meets the criteria of producing a proxy and general types of agents. As you’ll see, prompt flow even supports deployments of flows into containers and as services.

Open VS Code to `chapter_09/promptflow/simpleflow/flow.dag.yaml`, and open the file in the visual editor. Then, locate the Prompt field, and click the `recommended` `.jinja2` link, as shown in figure 9.12.

![figure](assets/9-12.png)

##### Figure 9.12 Opening the prompt Jinja2 template and examining the parts of the profile/prompt

Jinja is a templating engine, and Jinja2 is a particular version of that engine. Templates are an excellent way of defining the layout and parts of any form of text document. They have been extensively used to produce HTML, JSON, CSS, and other document forms. In addition, they support the ability to apply code directly into the template. While there is no standard way to construct prompts or agent profiles, our preference in this book is to use templating engines such as Jinja.

At this point, change the role within the system prompt of the `recommended.jinja2` template. Then, run all blocks of the flow by opening the flow in the visual editor and clicking the Play button. The next section will look at other ways of running prompt flow for testing or actual deployment.

### 9.3.3 Deploying a prompt flow API

Because prompt flow was also designed to be deployed as a service, it supports a couple of ways to deploy as an app or API quickly. Prompt flow can be deployed as a local web application and API running from the terminal or as a Docker container.

Return to the `flow.dag.yaml` file in the visual editor from VS Code. At the top of the window beside the Play button are several options we’ll want to investigate further. Click the Build button as shown in figure 9.13, and then select to deploy as a local app. A new YAML file will be created to configure the app. Leave the defaults, and click the Start Local App link.

![figure](assets/9-13.png)

##### Figure 9.13 Building and starting the flow as a local app

This will launch the flow as a local web application, and you’ll see a browser tab open, as shown in figure 9.14. Enter some text into the user\_input field, which is marked as required with a red asterisk. Click Enter and wait a few seconds for the reply.

![figure](assets/9-14.png)

##### Figure 9.14 Running the flow as a local web application

You should see a reply like the one shown earlier in figure 9.12, where the flow or agent replies with a list of time travel movies. This is great—we’ve just developed our first agent profile and the equivalent of a proxy agent. However, we need to determine how successful or valuable the recommendations are. In the next section, we explore how to evaluate prompts and profiles.

## 9.4 Evaluating profiles: Rubrics and grounding

A key element of any prompt or agent profile is how well it performs its given task. As we see in our recommendation example, prompting an agent profile to give a list of recommendations is relatively easy, but knowing whether those recommendations are helpful requires us to evaluate the response.

Fortunately, prompt flow has been designed to evaluate prompts/profiles at scale. The robust infrastructure allows for the evaluation of LLM interactions to be parallelized and managed as workers, allowing hundreds of profile evaluations and variations to happen quickly.

In the next section, we look at how prompt flow can be configured to run prompt/ profile variations against each other. We’ll need to understand this before evaluating profiles’ performance.

Prompt flow provides a mechanism to allow for multiple variations within an LLM prompt/profile. This tool is excellent for comparing subtle or significant differences between profile variations. When used in performing bulk evaluations, it can be invaluable for quickly assessing the performance of a profile.

Open the `recommender_with_variations/flow.dag.yaml` file in VS Code and the flow visual editor, as shown in figure 9.15. This time, we’re making the profile more generalized and allowing for customization at the input level. This allows us to expand our recommendations to anything and not just time travel movies.

![figure](assets/9-15.png)

##### Figure 9.15 The recommender, with variations in flow and expanded inputs

The new inputs Subject, Genre, Format, and Custom allow us to define a profile that can easily be adjusted to any recommendation. This also means that we must prime the inputs based on the recommendation use case. There are multiple ways to prime these inputs; two examples of priming inputs are shown in figure 9.16. The figure shows two options, options A and B, for priming inputs. Option A represents the classic UI; perhaps there are objects for the user to select the subject or genre, for example. Option B places a proxy/chat agent to interact with the user better to understand the desired subject, genre, and so on.

![figure](assets/9-16.png)

##### **Figure 9.16 The user interaction options for interfacing with the agent profile to prime inputs to the agent profile**

Even considering the power of LLMs, you may still want or need to use option A. The benefit of option A is that you can constrain and validate the inputs much like you do with any modern UI. Alternatively, the downside of option A is that the constrained behavior may limit and restrict future use cases.

Option B represents a more fluid and natural way without a traditional UI. It’s far more powerful and extensible than option A but also introduces more unknowns for evaluation. However, if the proxy agent that option B uses is written well, it can assist a lot in gathering better information from the user.

The option you choose will dictate how you need to evaluate your profiles. If you’re okay with a constrained UI, then it’s likely that the inputs will also be constrained to a set of discrete values. For now, we’ll assume option B for input priming, meaning the input values will be defined by their name.

To get back to VS Code and the visual view of the recommender with variants flow, click the icon shown earlier in figure 9.15 to open the variants and allow editing. Then, click the `recommend.jinja2` and `recommender_variant_1.jinja2` links to open the files side by side, as shown in figure 9.17.

![figure](assets/9-17.png)

##### Figure 9.17 Side-by-side comparison of variant profile templates for the recommender

Figure 9.17 demonstrates the difference between the variant profiles. One profile injects the inputs into the user prompt, and the other injects them into the system prompt. However, it’s essential to understand that variations can encompass more than profile design, as identified in table 9.1.

##### Table 9.1 LLM variation options in prompt flow

Option

Evaluation option examples

Notes

Jinja2 prompt template  
Compare system prompt variations, user prompt variations, or mixed prompt variations.  
Some endless combinations and techniques can be applied here. Prompt engineering is evolving all the time.  
LLM  
Compare GPT-9.5 to GPT-4.  
Compare GPT-4 to GPT-4 Turbo.  
Compare open source models to commercial models.  
This is a useful way to evaluate and ground model performance against a prompt. It can also help you tune your profile to work with open source and/or cheaper models.  
Temperature  
Compare a 0 temperature (no randomness) to a 1 (maximum randomness).  
Changes to the temperature can significantly change the responses of some prompts, which may improve or degrade performance.  
Max tokens  
Compare limited tokens to larger token sizes.  
This can allow you to reduce and maximize token usage.  
Advanced parameters  
Compare differences to options such as `top_p`, `presence_penalty`, `frequency_penalty`, and `logit_bias`.  
We’ll cover the use of these advanced parameters in later chapters.  
Function calls  
Compare alternative function calls.  
Function calls will be addressed later in this chapter.

For this simple example, we’re just going to use prompt variations by varying the input to reflect in either the system or user prompt. Refer to figure 9.17 for what this looks like. We can then quickly run both variations by clicking the Play (Run All) button at the top and choosing both, as shown in figure 9.18.

![figure](assets/9-18.png)

##### Figure 9.18 Running both prompt variations at the same time

In the terminal window, you’ll see the results of both runs. The results will likely look similar, so now we must move on to how we evaluate the difference between variations in the next section.

## 9.5 Understanding rubrics and grounding

Evaluation of prompt/profile performance isn’t something we can typically do using a measure of accuracy or correct percentage. Measuring the performance of a profile depends on the use case and desired outcome. If that is as simple as determining if the response was right or wrong, all the better. However, in most cases, evaluation won’t be that simple.

In education, the *rubric* concept defines a structured set of criteria and standards a student must establish to receive a particular grade. A rubric can also be used to define a guide for the performance of a profile or prompt. We can follow these steps to define a rubric we can use to evaluate the performance of a profile or prompt:

1. *Identify the purpose and objectives.* Determine the goals you want the profile or agent to accomplish. For example, do you want to evaluate the quality of recommendations for a given audience or overall quality for a given subject, format, or other input?
2. *Define criteria.* Develop a set of criteria or dimensions that you’ll use to evaluate the profile. These criteria should align with your objectives and provide clear guidelines for assessment. Each criterion should be specific and measurable. For example, you may want to measure a recommendation by how well it fits with the genre and then by subject and format.
3. *Create a scale*. Establish a rating scale that describes the levels of performance for each criterion. Standard scales include numerical scales (e.g., 1–5) or descriptive scales (e.g., Excellent, Good, Fair, Poor).
4. *Provide descriptions.* For each level on the scale, provide clear and concise descriptions that indicate what constitutes a strong performance and what represents a weaker performance for each criterion.
5. *Apply the rubric.* When assessing a prompt or profile, use the rubric to evaluate the prompt’s performance based on the established criteria. Assign scores or ratings for each criterion, considering the descriptions for each level.
6. *Calculate the total score.* Depending on your rubric, you may calculate a total score by summing up the scores for each criterion or using a weighted average if some criteria are more important than others.
7. *Ensure evaluation consistency.* If multiple evaluators are assessing the profile, it’s crucial to ensure consistency in grading.
8. *Review, revise, and iterate.* Periodically review and revise the rubric to ensure it aligns with your assessment goals and objectives. Adjust as needed to improve its effectiveness.

*Grounding* is a concept that can be applied to profile and prompt evaluation—it defines how well a response is aligned with a given rubric’s specific criteria and standards. You can also think of grounding as the baseline expectation of a prompt or profile output.

This list summarizes some other important considerations when using grounding with profile evaluation:

- Grounding refers to aligning responses with the criteria, objectives, and context defined by the rubric and prompt.
- Grounding involves assessing whether the response directly addresses the rubric criteria, stays on topic, and adheres to any provided instructions.
- Evaluators and evaluations gauge the accuracy, relevance, and adherence to standards when assessing grounding.
- Grounding ensures that the response output is firmly rooted in the specified context, making the assessment process more objective and meaningful.

A well-grounded response aligns with all the rubric criteria within the given context and objectives. Poorly grounded responses will fail or miss the entire criteria, context, and objectives.

As the concepts of rubrics and grounding may still be abstract, let’s look at applying them to our current recommender example. Following is a list that follows the process for defining a rubric as applied to our recommender example:

1. *Identify the purpose and objectives.* The purpose of our profile/prompt is to recommend three top items given a subject, format, genre, and custom input.
2. *Define criteria.* For simplicity, we’ll evaluate how a particular recommendation aligns with the given input criteria, subject, format, and genre. For example, if a profile recommends a book when asked for a movie format, we expect a low score in the format criteria.
3. *Create a scale.* Again, keeping things simple, we’ll use a scale of 1–5 (1 is poor, and 5 is excellent).
4. *Provide descriptions.* See the general descriptions for the rating scale shown in table 9.2.
5. *Apply the rubric.* With the rubric assigned at this stage, it’s an excellent exercise to evaluate the rubric against recommendations manually.
6. *Calculate the total score.* For our rubric, we’ll average the score for all criteria to provide a total score.
7. *Ensure evaluation consistency.* The technique we’ll use for evaluation will provide very consistent results.
8. *Review, revise, and iterate.* We’ll review, compare, and iterate on our profiles, rubrics, and the evaluations themselves.

##### Table 9.2 Rubric ratings

Rating

Description

1  
Poor alignment: this is the opposite of what is expected given the criteria.  
2  
Bad alignment: this isn’t a good fit for the given criteria.  
3  
Mediocre alignment: it may or may not fit well with the given criteria.  
4  
Good alignment: it may not align 100% with the criteria but is a good fit otherwise.  
5  
Excellent alignment: this is a good recommendation for the given criteria.

This basic rubric can now be applied to evaluate the responses for our profile. You can do this manually, or as you’ll see in the next section, using a second LLM profile.

## 9.6 Grounding evaluation with an LLM profile

This section will employ another LLM prompt/profile for evaluation and grounding. This second LLM prompt will add another block after the recommendations are generated. It will process the generated recommendations and evaluate each one, given the previous rubric.

Before GPT-4 and other sophisticated LLMs came along, we would have never considered using another LLM prompt to evaluate or ground a profile. You often want to use a different model when using LLMs to ground a profile. However, if you’re comparing profiles against each other, using the same LLM for evaluation and grounding is appropriate.

Open the `recommender_with_LLM_evaluation\flow.dag.yaml` file in the prompt flow visual editor, scroll down to the `evaluate_recommendation` block, and click the `evaluate_recommendation.jinja2` link to open the file, as shown in figure 9.19. Each section of the rubric is identified in the figure.

![figure](assets/9-19.png)

##### Figure 9.19 The evaluation prompt, with each of the parts of the rubric outlined

We have a rubric that is not only well defined but also in the form of a prompt that can be used to evaluate recommendations. This allows us to evaluate the effectiveness of recommendations for a given profile—automatically. Of course, you can also use the rubric to score and evaluate the recommendations manually for a better baseline.

Note  Using LLMs to evaluate prompts and profiles provides a strong baseline for comparing the performance of a profile. It can also do this without human bias in a controlled and repeatable manner. This provides an excellent mechanism to establish baseline groundings for any profile or prompt.

Returning to the `recommender_with_LLM_evaluation` flow visual editor, we can run the flow by clicking the Play button and observing the output. You can run a single recommendation or run both variations when prompted. The output of a single evaluation using the default inputs is shown in the following listing.

##### Listing 9.1 LLM rubric evaluation output

```
{
    "recommendations": "Title: The Butterfly Effect
Subject: 5
Format: 5
Genre: 4

Title: Primer
Subject: 5
Format: 5
Genre: 4

Title: Time Bandits
Subject: 5
Format: 5
Genre: 5"
}
```

We now have a rubric for grounding our recommender, and the evaluation is run automatically using a second LLM prompt. In the next section, we look at how to perform multiple evaluations simultaneously and then at a total score for everything.

## 9.7 Comparing profiles: Getting the perfect profile

With our understanding of rubrics and grounding, we can now move on to evaluating and iterating the perfect profile. Before we do that, though, we need to clean up the output from the LLM evaluation block. This will require us to parse the recommendations into something more Pythonic, which we’ll tackle in the next section.

### 9.7.1 Parsing the LLM evaluation output

As the raw output from the evaluation block is text, we now want to parse that into something more usable. Of course, writing parsing functions is simple, but there are better ways to cast responses automagically. We covered better methods for returning responses in chapter 5, on agent actions.

Open `chapter_09\prompt_flow\recommender_with_parsing\flow.dag.yaml` in VS Code, and look at the flow in the visual editor. Locate the `parsing_results` block, and click the link to open the Python file in the editor, as shown in figure 9.20.

![figure](assets/9-20.png)

##### Figure 9.20 Opening the `parsing_results.py` file in VS Code

The code for the `parsing_results.py` file is shown in listing 9.2.

##### Listing 9.2 `parsing_results.py`

```
from promptflow import tool

@tool      #1
def parse(input: str) -> str:
    # Splitting the recommendations into individual movie blocks
    rblocks = input.strip().split("\n\n")      #2

    # Function to parse individual recommendation block into dictionary
    def parse_block(block):
        lines = block.split('\n')
        rdict = {}
        for line in lines:
            kvs = line.split(': ')
            key, value = kvs[0], kvs[1]
            rdict[key.lower()] = value     #3
        return rdict

    parsed = [parse_block(block) for block in rblocks]    #4

    return parsed
```

#1 Special decorator to denote the tool block  
#2 Splits the input and double new lines  
#3 Creates a dictionary entry and sets the value  
#4 Loops through each block and parses into key/value dictionary

We’re converting the recommendations output from listing 9.1, which is just a string, into a dictionary. So this code will convert this string into the JSON block shown next:

*Before parsing:*

```
"Title: The Butterfly Effect
Subject: 5
Format: 5
Genre: 4

Title: Primer
Subject: 5
Format: 5
Genre: 4

Title: Time Bandits
Subject: 5
Format: 5
Genre: 5"
```

*After parsing:*

```
       {
            "title": " The Butterfly Effect
            "subject": "5",
            "format": "5",
            "genre": "4"
        },
        {
            "title": " Primer",
            "subject": "5",
            "format": "5",
            "genre": "4"
        },
        {
            "title": " Time Bandits",
            "subject": "5",
            "format": "5",
            "genre": "5"
        }
```

The output of this `parsing_results` block now gets passed to the output and is wrapped in a list of recommendations. We can see what all this looks like by running the flow.

Open `flow.dag.yaml` for the flow in the visual editor, and click the Play (Run All) button. Be sure to select to use both recommender variants. You’ll see both variations run and output to the terminal.

At this point, we have a full working recommendation and LLM evaluation flow that outputs a score for each criterion on each output. However, to do comprehensive evaluations of a particular profile, we want to generate multiple recommendations with various criteria. We’ll see how to do batch processing of flows in the next section.

### 9.7.2 Running batch processing in prompt flow

In our generic recommendation profile, we want to evaluate how various input criteria can affect the generated recommendations. Fortunately, prompt flow can batch-process any variations we want to test. The limit is only the time and money we want to spend.

To perform batch processing, we must first create a JSON Lines (JSONL) or JSON list document of our input criteria. If you recall, our input criteria looked like the following in JSON format:

```
{
    "subject": "time travel",
    "format": "books",
    "genre": "fantasy",
    "custom": "don't include any R rated content"
}
```

We want to create a list of JSON objects like that just shown, preferably in a random manner. Of course, the simple way to do this is to prompt ChatGPT to create a JSONL document using the following prompt:

I am developing a recommendation agent. The agent will recommend anything given the following criteria:

1\. subject - examples: time travel, cooking, vacation

2\. format - examples: books, movies, games

3\. genre: documentary, action, romance

4\. custom: don't include any R rated content

Can you please generate a random list of these criteria and output it in the format of a JSON Lines file, JSONL. Please include 10 items in the list.

Try this out by going to ChatGPT and entering the preceding prompt. A previously generated file can be found in the flow folder, called `\bulk_recommend.jsonl`. The contents of this file have been shown here for reference:

```
{
  "subject": "time travel",
  "format": "books",
  "genre": "fantasy",
  "custom": "don't include any R rated content"
}
{
  "subject": "space exploration",
  "format": "podcasts",
  "genre": "sci-fi",
  "custom": "include family-friendly content only"
}
{
  "subject": "mystery",
  "format": "podcasts",
  "genre": "fantasy",
  "custom": "don't include any R rated content"
}
{
  "subject": "space exploration",
  "format": "podcasts",
  "genre": "action",
  "custom": "include family-friendly content only"
}
{
  "subject": "vacation",
  "format": "books",
  "genre": "thriller",
  "custom": "don't include any R rated content"
}
{
  "subject": "mystery",
  "format": "books",
  "genre": "sci-fi",
  "custom": "don't include any R rated content"
}
{
  "subject": "mystery",
  "format": "books",
  "genre": "romance",
  "custom": "don't include any R rated content"
}
{
  "subject": "vacation",
  "format": "movies",
  "genre": "fantasy",
  "custom": "don't include any R rated content"
}
{
  "subject": "cooking",
  "format": "TV shows",
  "genre": "thriller",
  "custom": "include family-friendly content only"
}
{
  "subject": "mystery",
  "format": "movies",
  "genre": "romance",
  "custom": "include family-friendly content only"
}
```

With this bulk file, we can run both variants using the various input criteria in the bulk JSONL file. Open the `flow.dag.yaml` file in the visual editor, click Batch (the beaker icon) to start the bulk-data loading process, and select the file as shown in figure 9.21. For some operating systems, this may appear as `Local` `Data` `File`.

![figure](assets/9-21.png)

##### Figure 9.21 Loading the bulk JSONL file to run the flow on multiple input variations

After the bulk file is selected, a new YAML document will open with a Run link added at the bottom of the file, as shown in figure 9.22. Click the link to do the batch run of inputs.

![figure](assets/9-22.png)

##### Figure 9.22 Running the batch run of inputs

At this point, a few things will happen. The flow visual editor will appear, and beside that a log file will open, showing the progress of the run. In the terminal window, you’ll see the various worker processes spawning and running.

Be patient. The batch run, even for 10 items, may take a few minutes or seconds, depending on various factors such as hardware, previous calls, and so on. Wait for the run to complete, and you’ll see a summary of results in the terminal.

You can also view the run results by opening the prompt flow extension and selecting the last run, as shown in figure 9.23. Then, you dig into each run by clicking the table cells. A lot of information is exposed in this dialog, which can help you troubleshoot flows and profiles.

![figure](assets/9-23.png)

##### Figure 9.23 An opening run visualization and an examination of a batch run

A lot of information is captured during a batch run, and you can explore much of it through the visualizer. More information can be found by clicking the output folder link from the terminal window. This will open another session of VS Code with the output folder allowing you to review the run logs and other details.

Now that we’ve completed the batch run for each variant, we can apply grounding and evaluate the results of both prompts. The next section will use a new flow to perform the profile/prompt evaluation.

### 9.7.3 Creating an evaluation flow for grounding

Open `chapter_3\prompt_flow\evaluate_groundings\flow.dag.yaml` in the visual editor, as shown in figure 9.24. There are no LLM blocks in the evaluation flow—just Python code blocks that will run the scoring and then aggregate the scores.

![figure](assets/9-24.png)

##### Figure 9.24 Looking at the `evaluate_groundings` flow used to ground recommendation runs

We can now look at the code for the `scoring` and `aggregate` blocks, starting with the scoring code in listing 9.3. This scoring code averages the score for each criterion into an average score. The output of the function is a list of processed recommendations.

##### Listing 9.3 `line_process.py`

```
@tool
def line_process(recommendations: str):     #1
    inputs = recommendations
    output = []
    for data_dict in inputs:                      #2
        total_score = 0
        score_count = 0

        for key, value in data_dict.items():     #2
                if key != "title":     #3
                    try:
                        total_score += float(value)
                        score_count += 1
                        data_dict[key] = float(value)     #4
                    except:
                        pass

        avg_score = total_score / score_count if score_count > 0 else 0

        data_dict["avg_score"] = round(avg_score, 2)    #5
        output.append(data_dict)

    return output
```

#1 A set of three recommendations is input into the function.  
#2 Loops over each recommendation and criterion  
#3 Title isn’t a criterion, so ignore it.  
#4 Totals the score for all criteria and sets the float value to key  
#5 Adds the average score as a grounding score of the recommendation

From the grounded recommendations, we can move on to aggregating the scores with the `aggregate` block—the code for the `aggregate` block is shown in the following listing.

##### Listing 9.4 `aggregate.py`

```
@tool
def aggregate(processed_results: List[str]):
    items = [item for sublist in processed_results 
              ↪ for item in sublist]     #1

    aggregated = {}

    for item in items:
        for key, value in item.items():
            if key == 'title':
                continue

            if isinstance(value, (float, int)):      #2
                if key in aggregated:
                    aggregated[key] += value
                else:
                    aggregated[key] = value

    for key, value in aggregated.items():      #3
        value = value / len(items)
        log_metric(key=key, value=value)     #4
        aggregated[key] = value

    return aggregated
```

#1 The input is a list of lists; flatten to a list of items.  
#2 Checks to see if the value is numeric and accumulates scores for each criterion key  
#3 Loops over aggregated criterion scores  
#4 Logs the criterion as a metric

The result of the aggregations will be a summary score for each criterion and the average score. Since the evaluation/grounding flow is separate, it can be run over any recommendation run we perform. This will allow us to use the batch run results for any variation to compare results.

We can run the grounding flow by opening `flow.dag.yaml` in the visual editor and clicking Batch (beaker icon). Then, when prompted, we select an existing run and then select the run we want to evaluate, as shown in figure 9.25. This will open a YAML file with the Run link at the bottom, as we’ve seen before. Click the Run link to run the evaluation.

![figure](assets/9-25.png)

##### Figure 9.25 Loading a previous run to be grounded and evaluated

After the run is completed, you’ll see a summary of the results in the terminal window. You can click the output link to open the folder in VS Code and analyze the results, but there is a better way to compare them.

Open the prompt flow extension, focus on the Batch Run History window, and scroll down to the Run against Run section, as shown in figure 9.26. Select the runs you want to compare—likely the ones near the top—so that the checkmark appears. Then, right-click the run, and select the Visualize Runs option. The Batch Run Visualization window opens, and you’ll see the metrics for each of the runs at the top.

![figure](assets/9-26.png)

##### Figure 9.26 Visualizing the metrics for multiple runs and comparing them

We can now see a significant difference between profile/prompt variation 0, the user prompt, and variation 1, the system prompt. Refer to figure 9.15 if you need a refresher on what the prompts/profiles look like. At this point, it should be evident that injecting the input parameters into the system prompt provides better recommendations.

You can now go back and try other profiles or other variant options to see what effect this has on your recommendations. The possibilities are virtually endless, but hopefully you can see what an excellent tool prompt flow will be for building agent profiles and prompts.

### 9.7.4 Exercises

Use the following exercises to improve your knowledge of the material:

- *Exercise 1* —Create a New Prompt Variant for Recommender Flow (Intermediate)

*Objective* —Improve the recommendation results by creating and testing a new prompt variant in prompt flow.

*Tasks:*

- - Create a new prompt variant for the recommender flow in prompt flow.
  - Run the flow in batch mode.
  - Evaluate the results to determine if they are better or worse compared to the original prompt.
- *Exercise 2* —Add a Custom Field to the Rubric and Evaluate (Intermediate)

*Objective* —Enhance the evaluation criteria by incorporating a custom field into the rubric and updating the evaluation flow.

*Tasks:*

- - Add the custom field as a new criterion to the rubric.
  - Update the evaluation flow to score the new criterion.
  - Evaluate the results, and analyze the effect of the new criterion on the evaluation.
- *Exercise 3* —Develop a New Use Case and Evaluation Rubric (Advanced)

*Objective* —Expand the application of prompt engineering by developing a new use case and creating an evaluation rubric.

*Tasks:*

- - Develop a new use case aside from the recommendation.
  - Build the prompt for the new use case.
  - Create a rubric for evaluating the new prompt.
  - Update or alter the evaluation flow to aggregate and compare the results of the new use case with existing ones.
- *Exercise 4* —Evaluate Other LLMs Using LM Studio (Intermediate)

*Objective* —Assess the performance of different open source LLMs by hosting a local server with LM Studio.

*Tasks:*

- - Use LM Studio to host a local server for evaluating LLMs.
  - Evaluate other open source LLMs.
  - Consult chapter 2 if assistance is needed for setting up the server and performing the evaluations.
- *Exercise 5* —Build and Evaluate Prompts Using Prompt Flow (Intermediate)

*Objective* —Apply prompt engineering strategies to build and evaluate new prompts or profiles using prompt flow.

*Tasks:*

- - Build new prompts or profiles for evaluation using prompt flow.
  - Apply the Write Clear Instructions prompt engineering strategy from chapter 2.
  - Evaluate the prompts and profiles using prompt flow.
  - Refer to chapter 2 for tactics and implementation details if a refresher is needed.

## Summary

- An agent profile consists of several other component prompts that can drive functions such as actions/tools, knowledge, memory, evaluation, reasoning, feedback, and planning.
- Prompt flow can be used to evaluate an agent’s component prompts.
- Systemic prompt engineering is an iterative process evaluating a prompt and agent profile.
- The Test Changes Systematically strategy describes iterating and evaluating prompts, and system prompt engineering implements this strategy.
- Agent profiles and prompt engineering have many similarities. We define an agent profile as the combination of prompt engineering elements that guide and help an agent through its task.
- Prompt flow is an open source tool from Microsoft that provides several features for developing and evaluating profiles and prompts.
- An LLM connection in prompt flow supports additional parameters, including temperature, stop token, max tokens, and other advanced parameters.
- LLM blocks support prompt and profile variants, which allow for evaluating changes to the prompt/profile or other connection parameters.
- A rubric applied to an LLM prompt is the criteria and standards a prompt/profile must fulfill to be grounded. Grounding is the scoring and evaluation of a rubric.
- Prompt flow supports running multiple variations as single runs or batch runs.
- In prompt flow, an evaluation flow is run after a generative flow to score and aggregate the results. The Visualize Runs option can compare the aggregated criteria from scoring the rubric across multiple runs.
