
# Atradius Assignment

This repo contains the source files for the Atradius Data Engineering Assignment.

## Installation

There are 2 ways to set up this project your machine, and they are as follows:
- Uisng Docker **[Recommended]**
- Using a Python Virtual Environemnt

While the 2 above methods should work, we highly recommend you try the first approach.


## Setting Up and Running


## Approach 1: Using Docker

To get started, please make sure you have Docker installed on your machine. If you do not already have it installed, you can download it [here](https://docs.docker.com/get-docker/).

Assuming you have docker installed, you can run the following command in the terminal to handle most of the work (build the Docker image, and run the container).

```bash
$ bash ./start.sh
```

### Start the App

Assuming you ran the last step successfully, you should now be able to access the app on http://127.0.0.1:5000.

*The `raw.json`, `translated.json`, `sentiments.json` and `metadata.json` can be found in the `data` folder of this app.*

## Approach 2: Using a Python Virtual Environment

This approach requires that you have Python 3.8.* and above installed. If you do not have it installed, you can download it [here](https://www.python.org/downloads/release).

### To Setup a Python 3  Virtual  Environment
After you have installed Python, you can run the following in your Terminal

```python3 -m venv /path/to/new/virtual/environment```

Example:

```python3 -m venv venv```

This creates a new Python virtual environment for us.

### Activate Virtual Environment

Run the following in your Command prompt /Terminal

#### For Windows [Powershell]
```bash
source /path/to/new/virtual/environment/Scripts/activate
```
Example:
```bash
venv/Scripts/activate
```

#### For Linux and MacOS
```bash
source /path/to/new/virtual/environment/bin/activate
```
Example:

```bash
source venv/bin/activate
```

### Install necessary Libraries
After activating the virtual environment, we need to install necessary libraries for our app to work. To achieve this, we run:

```bash
python -m pip install -r requirements.txt
```

and to download the necessary tokenizer for classification we need to run the following:

```bash
python -m nltk.downloader punkt
```

### Start the App
To start the app, we want to run the following in your terminal:
```bash
flask run
```

You should now be able to access the app here: http://localhost:5000/


## Advanced

If you want to search for new Tweets different from the ones already collected, translate them and also run the sentiment classifier, you can do so using your own Twitter credential.

**IMPORTANT: add your credentials to the `test.env` file in the repo, and rename the file to `.env`.**

To show the option for searching for tweets on the dashboard, do the following:

- Delete any of the json files in the `data` folder
- Reload the dashboard page and you should see the option now

While you can search for new Tweets by using the App dashboard, you can also perform this from the CLI (command line interface).

```bash
python parse.py --maxtweets 20 --hashtag "#construction"
```

And if there may be rate limiting on translating our Tweets, you want to use the delay tag.
```bash
python parse.py --maxtweets 20 --hashtag "#construction" --delay 8
```

This may take some time, but you will see your results in the data folder of the project.
