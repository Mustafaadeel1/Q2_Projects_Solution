# LangChain Google Generative AI: Prompt Chaining Example
This project demonstrates the use of LangChain with Google Generative AI (Gemini) to implement a prompt-chaining mechanism. It utilizes two stages of prompt templates to:

1. Generate a detailed response to an input question.
2. Summarize the response into a concise answer.
## Features
* Integrates Google Generative AI via the langchain_google_genai library.
* Uses prompt templates to define structured prompts for generating and summarizing answers.
* Chains prompts together to process AI responses in multiple steps.
* Customizable parameters, including temperature, token limit, and model version.


## Installation
Install the required library before running the code:
```bash
!pip install langchain langchain_google_genai
```  
## Code Workflow
1. Import Libraries
```python
from google.colab import userdata  
from langchain_google_genai import ChatGoogleGenerativeAI  
from langchain.prompts import PromptTemplate
```
2. Securely Retrieve API Key
The API key is fetched securely from Colab using the userdata module:

```python
GOOGLE_API_KEY = userdata.get('GOOGLE_API_KEY')
```  
3. Initialize the Model
The Google Generative AI (Gemini) model is configured with the following parameters:

* `api_key`: API key for authentication.
* model: The model version `(gemini-1.5-flash)`.
* `temperature`: Controls the creativity of the output.
* `tokens`: Limits the response 
```python
llm = ChatGoogleGenerativeAI(  
    api_key=GOOGLE_API_KEY,  
    model="gemini-1.5-flash",  
    temperature=0.7,  
    tokens=70  
)  
```
4. Define Prompt Templates
First Prompt
Generates a detailed response to a user question:

```python
first_prompt = PromptTemplate(  
    input_variables=["question"],  
    template="First, answer the following question:\n\n{question}"  
)
```
### Second Prompt
Summarizes the initial response into five concise lines:

```python
second_prompt = PromptTemplate(  
    input_variables=["first_response"],  
    template="Now, let's summarize the answer in short 5 lines: {first_response}"  
)
```
5. Create Chains
The `first chain` processes the user’s question using the first prompt and the model. The second chain summarizes the response from the first chain.

```bash
first_chain = first_prompt | llm  
second_chain = second_prompt | llm  
```
6. Invoke Chains

##### Step 1: Run the First Chain
Process the input question through the first chain:

```python
first_response = first_chain.invoke({"question": "What is AI?"})  
print("First Answer:", first_response.content)  
```
#### Step 2: Run the Second Chain
Pass the first response into the second chain to get the summary:

```python
final_response = second_chain.invoke({"first_response": first_response})  
print("Final Answer:", final_response.content)
```  
## Example
#### Input Question:
`"What is AI?"`

### Output:
#### First Answer:

Artificial Intelligence (AI) refers to the simulation of human intelligence in machines. It enables machines to learn from data, recognize patterns, and make decisions. AI applications include natural language processing, computer vision, robotics, and more.

#### Final Answer:

AI enables machines to simulate human intelligence. It involves learning, pattern recognition, and decision-making. Applications include NLP, computer vision, and robotics.
### Parameters
* Model Version: `gemini-1.5-flash`
* Temperature: `0.7` (controls creativity; lower values = deterministic, higher values = creative).
* Tokens: `70` (limits the response length).
## Requirements
* Python 3.8+
* Google Generative AI API Key
* Libraries:
* `langchain`
* `langchain_google_genai`
### Usage
1. Set up your Google Generative AI API key securely in Colab.
2. Modify the `question` in the first chain to test different queries.
3. Adjust parameters like `temperature` and `tokens` for customized behavior.

## License
This project is licensed under the MIT License

