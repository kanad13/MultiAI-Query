# MultiAI-Query

## Overview

This repository contains a [Jupyter Notebook](./code.ipynb) designed to query multiple language models simultaneously using a single user prompt.

It supports a variety of models from different providers, including OpenAI, Mistral, LLaMA, Groq, and Google Gemini.

The notebook collects and formats the responses from each model into a Markdown file for easy comparison and analysis.

## Features

- **Multi-Model Support**: Query models from OpenAI, Mistral, LLaMA, Groq, and Google Gemini.
- **Customizable Parameters**: Adjust inference settings like temperature, top_p, and max_tokens to control response behavior.
- **Flexible Model Selection**: Easily include or exclude models based on your needs by modifying a simple list.
- **System Message Configuration**: Guide model responses with customizable system messages.
- **Formatted Output**: Responses are neatly organized into a `response.md` file with clear headers for each model.
- **Scalable Design**: Easily extendable to include additional models or modify existing ones.

## Installation

### Prerequisites

- Python 3.8 or higher
- Git

### Clone the Repository

```bash
git clone https://github.com/yourusername/multiai-query.git
cd multiai-query
```

### Create a Virtual Environment

It's recommended to use a virtual environment to manage dependencies.

```bash
python3 -m venv venv
source multiai_query_venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

## Configuration

### Environment Variables

The notebook requires several API tokens to interact with the various language models. Create a `.env` file in the root directory and add your tokens:

```bash
GITHUB_TOKEN=your_github_token
GROQ_TOKEN=your_groq_token
GEMINI_TOKEN=your_gemini_token
```

Checkout these links on how to create tokens for each of the platforms included above

- [Github Models Marketplace](https://github.com/marketplace)
- [Groq Cloud](https://console.groq.com/docs/quickstart)
- [Google AI for Developers](https://ai.google.dev)

### Selecting Models

Within the script, you can choose which models to query by modifying the `selected_models` list. Uncomment or edit the relevant lines to include desired models:

```python
# selected_models = ["openai", "mistral", "llama", "groq1", "groq2", "gemini1", "gemini2"]
# github only
# selected_models = ["openai", "mistral", "llama"]
# groq only
# selected_models = ["groq1", "groq2"]
# google only
# selected_models = ["gemini1", "gemini2"]
# custom
selected_models = ["gemini1"]
```

### Setting Parameters

Customize the inference behavior by adjusting the following parameters:

```python
temperature = 1.0  # Controls randomness (higher = more random)
top_p = 1.0        # Nucleus sampling parameter
max_tokens = 100   # Maximum number of tokens in the response
```

### System Messages

Guide the behavior of the models by selecting or customizing system messages. Uncomment the desired prompt or define your own:

```python
# **Prompt 1: Generic Prompt**
# my_instructions = "You are a knowledgeable and helpful assistant..."

# **Prompt 4: Well-Thought-Out Answers**
my_instructions = """You are a meticulous and thorough assistant. Before providing a response:
a. Take the time to thoroughly review and validate your answer.
b. Ensure that it is accurate, comprehensive, and relevant to the user's query.
c. Consider multiple perspectives or approaches to the problem.
d. Prioritize the quality of your response over speed.
e. Do not hesitate to request clarification if needed.
f. Provide a structured response with clear reasoning for your conclusions."""
```

## Usage

1. **Set Your Query**: Modify the `user_message` variable in the script with your desired question or prompt.

   ```python
   user_message = """
   How does Photosynthesis work?
   """
   ```

2. **Run the Script**:

   ```bash
   python script.py
   ```

   _Replace `script.py` with the actual name of your Python script._

3. **View the Output**: After execution, a `response.md` file will be generated containing the responses from the selected models.

## Output

The script generates a `response.md` file structured with Markdown headers for each model's response. The format includes:

- **Question Timestamp**: The user's query along with the timestamp.
- **Model Responses**: Each model's response is prefixed with a header indicating the model's name.

**Example Structure:**

```markdown
# Question 2024-04-27 12:34:56

What's the origin of the surname Ludwig.

## Gemini 1 (gemini-1.5-flash-8b)

[Gemini 1 response here]

## OpenAI (gpt-4o)

[OpenAI response here]

...
```

## Example

After running the script with the provided configuration, your `response.md` might look like this:

```markdown
# Question 2024-10-20 10:00:00

What's the origin of the surname Ludwig.

## Gemini 1 (gemini-1.5-flash-8b)

The surname Ludwig is of German origin, derived from the given name "Ludwig," which combines the elements "hlud" meaning "famous" and "wig" meaning "warrior." It has been borne by various notable figures throughout history, including Ludwig van Beethoven and Ludwig II of Bavaria.

## Mistral (Mistral-large-2407)

[Response from Mistral]

...
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/YourFeature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/YourFeature`
5. Open a pull request.

Please ensure your code adheres to the project's coding standards and includes appropriate documentation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
