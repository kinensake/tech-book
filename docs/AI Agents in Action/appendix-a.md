---
sidebar_position: 21
---

# appendix A Accessing OpenAI large language models

Although several commercial large language model (LLM) services are available, this book recommends using OpenAI services directly or through Azure OpenAI Studio. To access either service, you must create an account and register a payment method not covered in this appendix. The GPT-4 family of LLMs is considered best in class and better suited for agent development. Using open source and alternative services is always an option but generally only advisable after you’ve worked with GPT-4 for some time.

## A.1 Accessing OpenAI accounts and keys

The following general steps can help you quickly set up using OpenAI LLMs for agent development. Though using OpenAI and other commercial LLMs comes at a price, you can expect to pay less than US$100 to complete all the exercises in this book:

1. Go to [https://openai.com](https://openai.com) and log in, or register for an account and log in. If this is your first time creating an account, you’ll likely be given free credit in some amount. If you already have an account, you must register a payment method and type. It’s generally better to purchase a number of credits at a time. This will allow you to manage the costs better and avoid overruns.
2. After logging in to the platform, select ChatGPT or the API, as shown in figure A.1. Choose the API.

![figure](assets/A-1.png)

##### Figure A.1 Selecting the API section of the OpenAI platform

1. 3\. Open the left menu, and select the API Keys option, as shown in figure A.2.

![figure](assets/A-2.png)

##### Figure A.2 Selecting the API Keys option

1. 4\. Click the Create button to create a new key, enter a name for the key, and click the Create Secret Key button, as shown in figure A.3.

![figure](assets/A-3.png)

##### Figure A.3 Creating the secret API key

1. 5\. Copy and paste the key to a notepad or another area for safekeeping using the Copy button, as shown in figure A.4. Keep this key secret, and ensure it remains only on your development machine.

![figure](assets/A-4.png)

##### Figure A.4 Copying and pasting the key to a well-known safe location

After generating a key, you can continue to use it within an `.env` configuration file or through other means of registering an OpenAI key. For most of the packages used in this book, configuring OpenAI will generally only require the key. Other services, such as Azure OpenAI, will require the configuration of a model deployment and a base URL as covered in the next section.

## A.2 Azure OpenAI Studio, keys, and deployments

Through its ongoing relationship with OpenAI, Microsoft hosts the same models at the same price within Azure OpenAI Studio. Occasionally, Azure may be a model version behind, but Microsoft generally keeps current with the latest OpenAI models.

These guidelines will be more general because there are several ways to access Azure and methods of creating accounts and accessing the studio (for specific instructions, refer to Microsoft documentation):

1. Log in to your Azure portal account subscription.
2. Create a new Azure OpenAI Studio resource in a region that makes sense to you. At the time of writing, not all regions provided access to all models. You may need to check which models are available for your region first. This will also be specific to your account and usage.

Within Azure OpenAI, models are exposed through a resource allocation called a *deployment*. Deployments wrap a model, such as GPT-4, and provide access to the resource. Figure A.5 shows an example of various models being exposed through deployments.

![figure](assets/A-5.png)

##### Figure A.5 Deploying a model through an Azure OpenAI Studio deployment

1. 3\. Click the Create New Deployment button to create a new deployment, and then select the model you want to deploy.
2. 4\. After the model is wrapped in a deployment, you must access the parent Azure OpenAI resource. From there, you can access the key, endpoint, or base URL needed to configure your connection, as shown in figure A.6.

![figure](assets/A-6.png)

##### Figure A.6 Getting access to the keys and base URL used to access the service

Again, if you get stuck, the Microsoft documentation can guide you in the right direction. The three critical differences to remember when connecting to a resource such as Azure OpenAI Studio or another LLM using the OpenAI tooling are listed here:

- The `api key` to access the model
- The base `url` or `endpoint` where the model is located
- The name of the `model` or `deployment` name

If you can’t access a model for whatever reason, a good alternative is open source models. Setting up and consuming open source LLMs is covered in chapter 2.
