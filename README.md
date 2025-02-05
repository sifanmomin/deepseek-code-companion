# DeepSeek Code Companion

![App Screenshot](https://github.com/sifanmomin/T20-World-Cup-Cricket-Data-Analytics/blob/main/power_hitter)

🧠 DeepSeek Code Companion is an AI-powered pair programming assistant built with Streamlit, Ollama, and LangChain. It helps you with coding, debugging, and documentation.

## Features

- 🐍 **Python Expert**: Provides expert-level Python coding assistance.
- 🐞 **Debugging Assistant**: Helps identify and fix bugs in your code.
- 📝 **Code Documentation**: Generates documentation for your code.
- 💡 **Solution Design**: Assists in designing solutions for complex problems.

## Built With

- [Streamlit](https://streamlit.io/): A fast way to build and share data apps.
- [Ollama](https://ollama.ai/): An AI model provider.
- [LangChain](https://python.langchain.com/): A framework for developing applications powered by language models.

## Getting Started

### Prerequisites

Make sure you have the following installed:

- Python 3.7+
- pip

### Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/yourusername/deepseek-code-companion.git
    cd deepseek-code-companion
    ```

2. Install the required packages:

    ```sh
    pip install -r requirements.txt
    ```

### Running the App

1. Start the Streamlit app:

    ```sh
    streamlit run app.py
    ```

2. Open your browser and go to `http://localhost:8501` to see the app.

## Usage

1. Select the model from the sidebar.
2. Type your coding question in the chat input box.
3. The AI will respond with solutions, debugging tips, and documentation.

## Project Structure

- [app.py](http://_vscodecontentref_/0): The main application file that sets up the Streamlit interface and handles user interactions.
- `requirements.txt`: A file listing the Python dependencies needed to run the app.

## Code Overview

### [app.py](http://_vscodecontentref_/1)

- **Custom CSS Styling**: Adds custom styles to the Streamlit app for a better user experience.
- **Sidebar Configuration**: Allows users to select the AI model and view model capabilities.
- **Chat Engine Initialization**: Sets up the `ChatOllama` engine with the selected model.
- **System Prompt Configuration**: Defines the system prompt for the AI.
- **Session State Management**: Manages the chat message log in the session state.
- **Chat Input and Processing**: Handles user input, generates AI responses, and updates the chat display.

### Key Functions

- [generate_ai_response(prompt_chain)](http://_vscodecontentref_/2): Generates an AI response using the provided prompt chain.
- [build_prompt_chain()](http://_vscodecontentref_/3): Builds a prompt chain from the system prompt and message log.

### Example Code Snippet

```python
# filepath: /c:/Users/SIFAN/Desktop/deepssekwithollma/app.py
if msg["role"] == "user":
    prompt_sequence.append(HumanMessagePromptTemplate.from_template(msg["content"]))
elif msg["role"] == "ai":
    prompt_sequence.append(AIMessagePromptTemplate.from_template(msg["content"]))
return ChatPromptTemplate.from_messages(prompt_sequence)

if user_query:
    # Add user message to log
    st.session_state.message_log.append({"role": "user", "content": user_query})
    
    # Generate AI response
    with st.spinner("🧠 Processing..."):
        prompt_chain = build_prompt_chain()
        ai_response = generate_ai_response(prompt_chain)
    
    # Add AI response to log
    st.session_state.message_log.append({"role": "ai", "content": ai_response})
    
    # Rerun to update chat display
    st.rerun()
