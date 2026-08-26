# LangChain: Chat with SQL DB

This project is a Streamlit-based web application that allows users to interact with a SQL database using natural language. It leverages **LangChain** and **Groq's LLMs** (e.g., `qwen/qwen3.6-27b`) to dynamically convert natural language queries into SQL, execute them against the database, and return human-readable answers.

## Features
- **Natural Language to SQL**: Chat with your database without writing complex SQL queries.
- **Support for Multiple Databases**:
  - **SQLite**: Built-in support for a local SQLite database (`student.db`).
  - **MySQL**: Connect directly to your own MySQL database by providing host and credentials.
- **Interactive UI**: Built with Streamlit for a seamless, easy-to-use chat interface.

## Workflow

1. **User Input**: The user asks a question about the data via the Streamlit chat interface.
2. **Agent Processing**: The LangChain SQL Agent processes the input and uses the Groq LLM to generate an appropriate SQL query.
3. **Database Execution**: The generated SQL query is executed against the selected database (SQLite or MySQL) via SQLAlchemy.
4. **Result Synthesis**: The result of the SQL query is fed back to the LLM to generate a conversational response.
5. **Output**: The user receives the final natural language answer in the chat UI.

## Requirements

Ensure you have Python 3.12+ installed. The following libraries are used in this project:

- `streamlit`
- `langchain`
- `langchain-community`
- `langchain-groq`
- `SQLAlchemy`
- `mysql-connector-python`

## Setup and Installation

1. **Clone the repository** (or download the files to your local machine).

2. **Set up a Virtual Environment**:
   ```bash
   python -m venv evenv
   # Windows
   evenv\Scripts\activate
   # macOS/Linux
   source evenv/bin/activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Initialize Local Database (Optional)**:
   If you want to use the local SQLite option, run the `sqlite.py` script first. This will create a `student.db` file and populate it with sample student records.
   ```bash
   python sqlite.py
   ```

## Running the Application

1. Start the Streamlit app:
   ```bash
   streamlit run app.py
   ```
2. Open the provided Local URL in your web browser.

## Usage

1. **Select Database**: From the sidebar, choose whether to use the local SQLite database or connect to a MySQL database.
   - If using MySQL, provide your `Host`, `User`, `Password`, and `Database Name`.
2. **Provide API Key**: Enter your **Groq API Key** in the sidebar.
3. **Chat**: Use the chat input at the bottom to ask questions about your data (e.g., *"How many students are in Data Science?"* or *"Who got the highest marks?"*).

## Troubleshooting

- **Output Parsing Error**: If the agent struggles to format the output correctly, it will automatically attempt to recover. Ensure you are using a capable model like `Llama3` or `Qwen`.
- **Database Connection**: Double-check your MySQL credentials if the app fails to connect to your remote database.
