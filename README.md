# Copilot example

This is a _do-it-yourself_ exercise on how to use GitHub Copilot with some simple examples. This example will work on WSL or pure Linux. But you do need to have Docker and Docker Compose installed, and - of course - a working GitHub Copilot subscription.

This example is expecting that you use Visual Studio Code.

## Inline suggestion

This is an example on how to use the in-editor suggestions from GitHub Copilot.

### The fizzbuzz example

Create a file named `fizzbuzz.py`, and copy the following code:

```python
# Fizzbuzz function that receives a parameter "number"
# If the number is divisible by 3, return "Fizz"
# If the number is divisible by 5, return "Buzz"
# But if the number is divisible by 3 and 5, return "FizzBuzz"
# Else, print the number
def fizzbuzz
```

The VSCode extension will capture the open files, and start to suggest the code. Wait a moment for the suggestion to appear and press `tab` to accept the suggestion.

Bring up Copilot function in the editor by pressing `CTRL-i` and type:

```
Add code to run the function
```

Copilot will suggest the following code a snippet to run the function in a loop. Press `tab` to accept the suggestion.

Most likely the code will not be perfect, and you have to fix things like identation, missing colons, etc. But it is a good starting point.

## Generative example

Now lets try Copilot Chat to generate a simple python project.

### Setup python project with virtualenv

Lets start with just setting up Python Virtual Environment in the project by writing into the *Copilot Chat*:

```
can you give me give the bash commands to setup an virtualenv that can read the output from a REST API and output it to YAML?
```

In the Chat side panel find the code example with the shell commands, and click on the "Insert into terminal" button.

You can see that Chat inserts the commands into the VSCode terminal, so click `Enter` in the terminal to execute the commands.


### Create the test environment

Create docker compose with nginx that mount bind volume to `./html`.

```
can you create a docker compose file that runs nginx and maps the html directory to the nginx html using a bind volume
```

Save the following code to `compose.yml`:

Let's refactor compose file to listen to port 8888, but first, open the `compose.yml` file, select all, and bringing up the Copilot function in the editor by pressing `CTRL-i` and type:

```
can you refactor this compose file to listen to port 8888
```

Create JSON test file to simulate API response.

```
can you create a json file named api without the .json extension with some test data in html/
```

In case Copilot forgets to create the `html` directory first, then is fine, because Chat works like GPT and can be trained to understand the context of the conversation as well as the open file. So you can just ask:

```
you forgot to create the html directory first
```

Run the suggested commands to create the `html` directory and the `api` file.

Run in an other terminal the following command to start the nginx server:

```bash
docker-compose up
```

### Create simple python that fetches data from nginx

Create a simple python script to retrieve data from the nginx server.

```
generate python script to retrieve data from http://localhost:8888/api
```

In the chat, you will see the code example, and you can click on the "Insert into file" button to insert the code into the `get_data.py` file.

Lets just document code by bringing up the Copilot function in the editor by pressing `CTRL-i` and type:

```
/doc
```

Lets refactor from a function to a class, so again bring up the Copilot function in the editor by pressing `CTRL-i` and type:

```
can you refactor the code to a class
```

### Create complex python example

Create a module that creates classes to fetch and process json data

Open `html/api` file in VSCode and write in chat:

```
considering the json open, can you create a example that interprets the json data from <http://localhost:8888/api> with multiple classes in separate files and how to organize them in a python module named get_some_api_output
```

You can now see how Copilot suggests the code call the URL, and base the output on the `html/api` content.

But lets be a little more helpless:

```
can you include the commands to create the files and folder structure?
```

So open the files created by the commands, and start copying the code into the files. Often Copilot forgets the content of `__init__.py`, but then you can ask it:

```
you forgot about __init__py
```

Sometimes the `main.py` ends up being created in the module folder, so just move it to the root of the project. But this just emphasizes the importance of actually knowing what you are doing, and not just blindly accepting the suggestions.

Now refactor code to convert output to `YAML`, so open `main.py` and bring up the Copilot function in the editor by pressing `CTRL-i` and type:

```
can you refactor the code to convert the output to yaml
```

Let's create a unit test, by opening `main.py` and bring up the Copilot function in the editor by pressing `CTRL-i` and type:

```
/tests
```

Copilot will suggest to create a new file call `test_main.py` and insert the test code.

After accepting that Copilot creates the test, then just run `pytest`:

```shell
pip install pytest
pytest
```
