# Training Code: Getting Started with Google Agent Development Kit (ADK)

This project represents the complete, functional application developed during my training, derived from two foundational Google Codelabs. It serves as a comprehensive example and reference for ADK implementation.

## Introduction

The Google Agent Development Kit (ADK) provides a framework for building powerful and sophisticated AI agents. This project serves as a starting point and a tutorial for creating your own agent using `uv` for environment management and the ADK for agent creation.

## Prerequisites

- Python 3.9 or higher.
- `uv` installed. `uv` is a fast, next-generation Python package manager. If you are using Google Cloud Shell, `uv` is pre-installed.

## Getting Started

Follow these steps to create and set up your AI agent.

### 1. Verify `uv` Installation

First, ensure `uv` is installed and available in your terminal.

```bash
uv --version
```

### 2. Create a Project Folder

Use `uv init` to create a new project directory and initialize it.

```bash
uv init ai-agents-adk
```

### 3. Navigate to the Project Folder

Change into the newly created directory.

```bash
cd ai-agents-adk
```

### 4. Create a Virtual Environment

It's a best practice to use a virtual environment to manage project-specific dependencies. This command creates a virtual environment using Python 3.12.

```bash
uv venv --python 3.12
```
After creating the virtual environment, you need to activate it. On Linux or macOS, you would typically run `source .venv/bin/activate`.

### 5. Install the Google ADK

With the virtual environment activated, install the `google-adk` library.

```bash
uv add google-adk
```

### 6. Verify the Installation

Check that the `google-adk` package was installed successfully.

```bash
uv pip list | grep google-adk
```

You should see an output line with `google-adk` and its version number.

### 7. Create the Agent

Now, use the ADK to generate the scaffolding for your new agent.

```bash
uv run adk create personal_assistant
```

This command will prompt you with a few configuration questions:

1.  **Choose a model for the root agent:** Select `gemini-1.5-flash` (option 1) for a fast and efficient model.
    ```
    Choose a model for the root agent:
    1. gemini-1.5-flash
    2. Other models (fill later)
    Choose model (1, 2): 1
    ```

2.  **Choose a backend:** Select `Vertex AI` (option 2) to use Google Cloud's managed AI platform.
    ```
    1. Google AI
    2. Vertex AI
    Choose a backend (1, 2): 2
    ```

3.  **Enter Google Cloud project ID:** Verify that the detected project ID is correct and press `Enter`. If not, enter the correct one.
    ```
    Enter Google Cloud project ID [your-project-id]:
    ```

4.  **Enter Google Cloud region:** Verify the region is correct and press `Enter`. If not, provide the correct region.
    ```
    Enter Google Cloud region [your-region]:
    ```

## Project Structure

After running the `adk create` command, your `personal_assistant` directory will contain the following files:

- `personal_assistant/`: This directory is a Python package containing your agent's code.
  - `__init__.py`: An empty file that marks this directory as a Python package.
  - `agent.py`: This is the core of your agent. It contains the main logic, including the agent's prompts and tool definitions. You will spend most of your time editing this file to customize your agent's behavior.
- `.env`: This file is used to store environment variables for your project, such as API keys or your Google Cloud Project ID and location. The `adk` automatically populates this file with the values you provided during setup.


### 8. Run the Agent

You have two primary ways to interact with and test your agent: the Command Line Interface (CLI) for simple chat, or the built-in Web Developer UI for powerful debugging and tracing.

- Stay in your GoogleADKTrainingCode Folder.

- Running the Agent via CLI: Start an interactive chat session with your agent directly in the terminal:

   ```bash
    uv run adk run personal_assistant
- Launching the Developer Web UI: For a visual interface that allows you to trace the agent's internal thought process and tool calls, launch the adk web UI. This is an essential tool for effective development and debugging.

  ```bash
    uv run adk web
Open the URL provided in your terminal (typically http://localhost:8000 or http://127.0.0.1:8000) to access the UI.


### 9. Empowering Agents with Tools
The final step is to see an agent with tools that it can use to perform actions. Add the following files to your current project. 
    
    touch personal_assistant/custom_agents.py 

    touch personal_assistant/custom_functions.py

    touch personal_assistant/third_party_tools.py

- `custom_agents.py`: Contains the `google_search_agent`, a specialized agent for performing Google searches.
 - `custom_functions.py`: Includes custom-defined functions like `get_fx_rate` for fetching currency exchange rates.
- `third_party_tools.py`: Integrates third-party tools, such as the Langchain Wikipedia tool.

### 10. Run the Updated Agent(with tools)
Stay in your GoogleADKTrainingCode Folder and run either of the following commands: 

    uv run adk web
    |OR|
    uv run adk run personal_assistant

Open the URL provided in your terminal (typically http://localhost:8000 or http://127.0.0.1:8000) to access the UI.
