# OpenAI GPT-3 Chatbot


A simple interface to the OpenAI GPT-3 models with speech
to text for input and text to speech for the output from OpenAI.

## Setup

Optionally create a new Python environment and active it:

```bash
# create a new environment in the current directory called env
python3 -m venv env

# activate the environment
source env/bin/activate
```

Install dependencies:

```bash
# Mac OSX
brew install portaudio
brew link portaudio

# save the output of this command
brew --prefix portaudio
```

Run

```bash
sudo vi $HOME/.pydistutils.cfg
```

and paste the following text replacing the values with the output saved from above:

```text
[build_ext]
include_dirs=<PATH FROM STEP 3>/include/
library_dirs=<PATH FROM STEP 3>/lib/
```

Finally, run the following to install all required Python packages:

```bash
pip install -e .
```

## Running the Script

```bash
python gpt3_assistant/main.py --log-level=INFO --open-ai-key=<OPEN API SECRET KEY HERE>
```

Start speaking and turn up your volume to hear the AI
assistant respond.

Say the word "exit" to stop the application.

### Optional: Specifying an Output Language Accent

Specify both the `LANGUAGE` and `TOP_LEVEL_DOMAIN` vars to override the default English (United States)

```bash
python gpt3_assistant/main.py --open-ai-key=<OPENAI_KEY> --lang=en --tld=com
```

#### Language Examples

* English (United States) *DEFAULT*
    * `LANGUAGE=en TOP_LEVEL_DOMAIN=com`
* English (Australia)
    * `LANGUAGE=en TOP_LEVEL_DOMAIN=com.au`
* English (India)
    * `LANGUAGE=en TOP_LEVEL_DOMAIN=co.in`
* French (France)
    * `LANGUAGE=fr TOP_LEVEL_DOMAIN=fr`

See Localized 'accents' section on gTTS docs for more information

## Linting

Sort all imports with:

```bash
isort --multi-line 3 --profile black --python-version 38 gpt3_assistant
```

Run `black gpt3_assistant` to automatically reformat all source files
based on the default configuration.

## Testing

### Unit Tests

Run `pytest` to run all unit tests.

### Coverage Report

Get the coverage with:

```bash
coverage run -m pytest tests
```

View the coverage report:

```bash
coverage report --fail-under=90 --include="gpt3_assistant/*"
```
