# AI Trip Planner

An AI-powered travel planning application that creates detailed trip itineraries using Large Language Models (LLMs), real-time weather data, place search, expense calculations, and currency conversion.

The application provides a FastAPI backend for AI agent processing and a Streamlit frontend for an interactive user experience.

## Features

- Generates comprehensive travel plans for destinations worldwide
- Creates day-by-day itineraries
- Suggests popular tourist attractions and off-beat locations
- Recommends restaurants, activities, and local transportation options
- Fetches current weather forecasts
- Calculates hotel costs, total trip expenses, and daily budgets
- Converts currencies using real-time exchange rates
- Supports Groq and OpenAI language models
- Uses LangGraph for agentic workflows and tool orchestration
- Provides an easy-to-use Streamlit interface

## Technology Stack

- Python
- FastAPI
- Streamlit
- LangChain
- LangGraph
- Groq API
- OpenAI API
- Google Places API
- Tavily Search API
- OpenWeatherMap API
- Exchange Rate API

## Project Structure
AI_Trip_Planner/
│
├── agent/
│   └── agentic_workflow.py       # LangGraph agent workflow
│
├── config/
│   └── config.yaml               # LLM model configuration
│
├── prompt_library/
│   └── prompt.py                 # System prompt for the travel agent
│
├── tools/
│   ├── weather_info_tool.py      # Weather-related tools
│   ├── place_search_tool.py      # Attractions, restaurant, activity, and transport tools
│   ├── expense_calculator_tool.py# Budget and expense calculation tools
│   └── currency_conversion_tool.py # Currency conversion tool
│
├── utils/
│   ├── model_loader.py           # Groq/OpenAI model loader
│   ├── weather_info.py           # OpenWeatherMap API integration
│   ├── place_info_search.py      # Google Places and Tavily integration
│   ├── expense_calculator.py     # Expense calculation utilities
│   ├── currency_converter.py     # Currency conversion utility
│   └── config_loader.py          # YAML configuration loader
│
├── main.py                       # FastAPI backend entry point
├── streamlit_app.py              # Streamlit frontend entry point
├── requirements.txt              # Project dependencies
├── pyproject.toml                # Project metadata and dependencies
└── README.md

##Prerequisites
Before running the project, install:
Python 3.10 or later
Git
Required API keys
It is recommended to use Python 3.11 or newer.
Installation
1. Clone the repository
git clone https://github.com/your-username/AI_Trip_Planner.git
cd AI_Trip_Planner
2. Create a virtual environment
Windows PowerShell:
python -m venv env
.\env\Scripts\Activate.ps1
macOS/Linux:
python3 -m venv env
source env/bin/activate
4. Install dependencies
pip install -r requirements.txt
Alternatively, if the project is configured through pyproject.toml:
pip install -e .
Environment Variables
Create a .env file in the root directory of the project.
GROQ_API_KEY=your_groq_api_key
OPENAI_API_KEY=your_openai_api_key
OPENWEATHERMAP_API_KEY=your_openweathermap_api_key
GPLACES_API_KEY=your_google_places_api_key
TAVILY_API_KEY=your_tavily_api_key
EXCHANGE_RATE_API_KEY=your_exchange_rate_api_key
Never upload your .env file or API keys to GitHub.

Add the following entries to .gitignore:
.env
env/
.venv/
__pycache__/
my_graph.png

Model Configuration

Update config/config.yaml with the model providers and model names you want to use:
llm:
  groq:
    model_name: "openai/gpt-oss-120b"

  openai:
      model_name: "gpt-4o-mini"
  The application currently uses Groq by default. Ensure that GROQ_API_KEY is present in your .env file when using the Groq provider.
  Running the Application
  Start the FastAPI Backend
  From the project root directory:
    uvicorn main:app --reload
  The backend will run at:
    http://127.0.0.1:8000
  Start the Streamlit Frontend
  
Open a new terminal, activate the virtual environment, and run:
  streamlit run streamlit_app.py

The Streamlit application will normally open at:
    http://localhost:8501
  API Usage
    Query Endpoint
  Endpoint:
    POST /query
  **Request body:
  {
    "question": "Plan a 5-day trip to Goa for two people."
  }
  Example response:
  {
    "answer": "Detailed AI-generated travel plan..."
  }

Example Prompts:
  Try prompts such as:
  Plan a 5-day trip to Goa for two people.
  What is the current weather in Jaipur?
  Suggest popular attractions and restaurants in Manali.
  Calculate hotel cost for ₹5000 per night for 4 nights.
  Convert 100 USD to INR.
  
How It Works: 
  The user enters a travel-related query in the Streamlit application.
  Streamlit sends the query to the FastAPI /query endpoint.
  The FastAPI backend passes the request to the LangGraph travel agent.
  The agent decides whether to use weather, place-search, expense, or currency tools.
  The agent uses returned information to generate a detailed Markdown travel plan.
  The response is returned to Streamlit and displayed to the user.
  
Important Notes:
  Travel prices, hotel availability, restaurant details, weather, and local transport information can change frequently.
  AI-generated recommendations should be verified before making bookings or travel decisions.
  Some features require valid API keys and active API service accounts.
  Tool-based responses depend on the availability and accuracy of third-party APIs.

Future Improvements: 
  User authentication and saved trip plans
  PDF itinerary export
  Interactive maps and route visualization
  Hotel and flight booking integrations
  Destination images and travel galleries
  Multi-currency budget dashboard
  Better error handling and retry logic for LLM tool calls
  Conversation history and personalized recommendations
  Deployment using Docker or cloud platforms
License
This project is intended for educational and personal use. Add a license file, such as the MIT License, before using it in production or sharing it publicly.
Author
Developed as an AI-powered travel planning and expense management application.
```
