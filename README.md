# Moneta - an AI-Agentic Assistant for Insurance and Banking

Moneta is an AI-powered assistant designed to empower insurance and banking advisors. This Solution Accelerator provides a chat interface where advisors can interact with various AI agents specialized in different domains such as insruance policies, CRM, product information, funds, CIO insights, and news.

The agentic framework used behind is the:
[Microsoft GBB AI EMEA - Vanilla Agents](https://github.com/Azure-Samples/genai-vanilla-agents)

## Features
- Multi-Use Case Support: Switch between insurance and banking use cases.
- Agent Collaboration: Agents collaborate to provide the best answers.
- Azure AD Authentication: Secure login with Microsoft Azure Active Directory.
- Conversation History: Access and continue previous conversations.

### Overview
- Python 3.11 or higher
- Streamlit (frontend app - chatGPT style)
- Microsoft Authentication Library (MSAL- if using authentication - optional)
- Azure AD application registration (if using authentication - optional)
- An Azure Function App as backend API endpoint
- CosmosDB to store user conversations adn history

## Use cases

### Insurance

'Planner': an orchestrator agent
'CRM': simulate fetching clients information from a CRM (DB, third-party API etc)
'Policies RAG': vector search with AI Search on various public available policy documents (product informations)

### Banking

'Planner': an orchestrator agent
'CRM': simulate fetching clients information from a CRM (DB, third-party API etc)
'Funds and ETF RAG': vector search with AI Search on few funds and ETF factsheets (product informations)
'CIO': vector search with AI Search on in house investements view and reccomandations 
'News': RSS online feed search on stock news

## Frontend (local deployment)

### Environment Variables
Create a .env file following the env.sample in the project frontend directory and set the following environment variables:

Mandatory vars, use Disable login = True for local dev and to bypass msal auth
DISABLE_LOGIN=<Set to 'True' to disable login>
FUNCTION_APP_URL=<Your Azure Function App URL>

for enabling auth you need to have an app registration:
AZ_REG_APP_CLIENT_ID=<Your Azure Registered App Client ID>
AZ_TENANT_ID=<Your Azure Tenant ID>
WEB_REDIRECT_URI=<Your Redirect URI>

### Running the App
Start the Streamlit application:

'cd frontend'
'streamlit run rm_app.py'

### Usage
+ Login: Click on "Log in with Microsoft" to authenticate via Azure AD (automatically skip if disableLogin = True)
+ Select Use Case: Choose between 'fsi_insurance' and 'fsi_banking' from the sidebar.
+ Start a Conversation: Click "Start New Conversation" or select an existing one.
+ Chat: Use the chat input to ask questions. Predefined questions are available in a dropdown.
+ Agents Online: View the available agents for the selected use case.
+ Chat histories: view and reload your past conversations


