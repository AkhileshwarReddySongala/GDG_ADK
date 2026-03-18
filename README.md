# GDG Agent Dev Kit (ADK) Example

This project demonstrates how to build a multi-tool agent using the `google-adk` library. The agent is powered by Google's Gemini models (`gemini-2.5-flash`) and uses function calling to answer user queries about time and weather.

## Project Structure

- `multi_tool_agent/agent.py`: Contains the core agent logic. It defines the tools (`get_weather`, `get_current_time`) and initializes the `Agent` object (`weather_time_agent`).
- `multi_tool_agent/.env`: Configuration file storing the Google API Key and Vertex AI settings.
- `requirments.txt`: Lists the project dependencies (currently `google-adk`).

## Prerequisites

- Python version supported by `google-adk`
- A valid Google Gemini API Key.

## Setup Instructions

1. **Clone the repository** (if you haven't already).
2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv .venv
   # On Windows use:
   .venv\Scripts\activate
   ```
3. **Install dependencies:**
   ```bash
   pip install -r requirments.txt
   ```
4. **Configure your API Key:**
   Ensure the `.env` file inside the `multi_tool_agent` directory has your actual `GOOGLE_API_KEY`:
   ```env
   GOOGLE_GENAI_USE_VERTEXAI=FALSE
   GOOGLE_API_KEY=your_actual_api_key_here
   ```

## Usage

The `weather_time_agent` defined in `multi_tool_agent/agent.py` can be imported and executed in your Python scripts. It currently focuses on querying the current time and weather and works by default with "New York" as its main targeted area.

### Available Tool Functions

- **`get_weather(city: str)`**: Retrieves weather information. It currently returns a static success response with the weather for "New York".
- **`get_current_time(city: str)`**: Retrieves the localized current time using the "America/New_York" timezone for New York.

### Example Execution

You can run the agent by creating a new script in the same root and invoking the agent instance you imported from `multi_tool_agent.agent`:

```python
from multi_tool_agent.agent import root_agent

response = root_agent.invoke("What is the time and weather in New York?")
print(response)
```
