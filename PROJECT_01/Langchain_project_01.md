# LangChain Hello World: Chat with Google Generative AI
This project demonstrates how to integrate LangChain with Google Generative AI (Gemini) to interact with the model using a conversational interface. The code highlights the initialization of the model, retrieving the API key securely, and invoking a query to generate responses.
## Features
* Leverages Google Generative AI (Gemini) for conversational AI capabilities.
* Uses the LangChain framework to streamline interaction with the model.
* Securely retrieves the Google API key through Colab's userdata module.
## Installation
Before running the code, ensure the required libraries are installed. Use the following command to install dependencies:
```bash
!pip install langchain langchain_google_genai
```
LangChain Hello World: Chat with Google Generative AI
This project demonstrates how to integrate LangChain with Google Generative AI (Gemini) to interact with the model using a conversational interface. The code highlights the initialization of the model, retrieving the API key securely, and invoking a query to generate responses.

Features
Leverages Google Generative AI (Gemini) for conversational AI capabilities.
Uses the LangChain framework to streamline interaction with the model.
Securely retrieves the Google API key through Colab's userdata module.
Installation
Before running the code, ensure the required libraries are installed. Use the following command to install dependencies:

bash
Copy code
!pip install langchain langchain_google_genai  
## Code Overview
1. Import Required Modules
```python
import langchain_google_genai as genai  
from langchain_google_genai import ChatGoogleGenerativeAI  
from google.colab import userdata
```
2. Retrieve API Key
The API key is securely retrieved using Colab's userdata module. This ensures sensitive information is not exposed in the code:

```python
GOOGLE_API_KEY = userdata.get('GOOGLE_API_KEY')
```
3. Initialize the Model
The ChatGoogleGenerativeAI class is used to configure the Google Generative AI (Gemini) model.

```python
model = ChatGoogleGenerativeAI(  
    model="gemini-1.5-flash",  # Model version  
    api_key=GOOGLE_API_KEY    # Secure API key  
)
```
4. Invoke the Model
A query is passed to the model using the .invoke() method, and the response is printed.

```python
Copy code
response = model.invoke("How is founder OF ai")  
print(response.content)
```
## Usage
1. Make sure your Google Generative AI API key is set up in Colab using the userdata module.
2. Run the script in a Colab notebook or Python environment supporting LangChain and Google Generative AI.
3. Enter your query in the `model.invoke()` method, and the model will respond.
## Example Output
Input:
```python
"How is founder OF ai"  
```
Output:
```bash
"Artificial Intelligence has been founded and advanced by several pioneers, including Alan Turing, John McCarthy, and others."  
```
## Requirements
* Python 3.8+
* Google Generative AI API Key
* Libraries:
* `langchain`
* `langchain_google_genai`
## License
This project is licensed under the MIT License.
