# rasa-project
A simple chatbot built with Rasa and Flask.

# Install Dependencies
```bash
pip3 install rasa
pip3 install flask
```


## Init
---
```bash
rasa init
```

## Folder Structure and Assets
- `data/nlu.yml`: Contains the training data in the form of **intents** and **entities**. **Intents** are used to classify individual user messages.
- `data/stories.yml`: Contains stories/conversations between the bot and a user.
- `data/rules.yml`: Contains rules that handle small conversations at any point.
- `config.yml`: Contains the pipeline that the bot will use to interpret the message.
- `domain.yml`: Contains all the intents and their corresponding responses.

## Process

### Define Intent
```yaml
version: "3.1"
nlu:
- intent: greet
	examples: |
	- hey
	- hello
	- hi
	- hello there
	- good morning
	- good evening
	- moin
	- hey there
	- let's go
	- hey dude
	- goodmorning
	- goodevening
	- good afternoon

...
```

### Define Stories
```yaml
version: "3.1"
stories:
- story: happy path
	steps:
	- intent: greet
	- action: utter_greet
	- intent: mood_great
	- action: utter_happy

...
```

## Defining Rules
---
Some messages do not require full-length conversations. 

They can be resolved by always following the same path using a single response. 
These are defined as **rules**.

```yaml
version: "3.1"
rules:

- rule: Say goodbye anytime the user says goodbye
	steps:
	- intent: goodbye
	- action: utter_goodbye

...

```


## Train Model
---
```
rasa train
```

Trains model and puts it n ./models/

## Start Model Inside Shell
---
```bash
rasa shell
```

## Interactive Training
```bash
rasa interactive
```

Talk to bot about utterances and intents and improve data set.

## Check Data for Inconsistency:
```bash
rasa data validate
```

## Train Again 
```bash
rasa train
```

## Visualize Dataset
```
rasa visualize
```

## Run Rasa
```bash
rasa run -m models --enable-api
```

# Run App
```bash
python3 app.py
```