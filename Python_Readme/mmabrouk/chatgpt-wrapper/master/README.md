<h1><p align="center">:candy:ChatGPT (and GPT4) Wrapper:candy:</p></h1>

## Welcome!

What would you like to do?

* [Learn about the project](#summary-header)
* [Install the wrapper](#requirements)
* [Learn more about configuration/features](#configuration)
* [Learn how to use it](#usage)
* [Troubleshoot common issues](#troubleshooting)
* [Upgrade the wrapper](#upgrading)
* [Using GPT4](#gpt4)
* [Report a bug](ISSUES.md)
* [Get support](SUPPORT.md)

<p id="summary-header" align="center">ChatGPT Wrapper is an open-source unofficial <b>Power CLI</b>, <b>Python API</b> and <b>Flask API</b> that lets you interact programmatically with ChatGPT/GPT4.</p>

## Highlights

🤖 The ChatGPT Wrapper lets you use the powerful ChatGPT/GPT4 bot from the **command line**.

💬 **Runs in Shell**. You can call and interact with ChatGPT/GPT4 in the terminal.

💻  **Supports official ChatGPT API**. Make API calls directly to the OpenAI ChatGPT endpoint (all supported models accessible by your OpenAI account)

🔌 **Simple plugin architecture**. Extend the wrapper with custom functionality

🗣 **Supports multiple LLM providers**. Provider plugins allow interacting with other LLMs (GPT-3, Cohere, Hugginface, etc.)

🐍**Python API**. The ChatGPT Wrapper also has a Python library that lets you use ChatGPT/GPT4 in your Python scripts.

🔄[**Build workflows**](#workflows). Easily integrate calls to an LLM into larger workflows via Ansible Playbooks (alpha)

𝑓(𝑥) [**Execute functions**](#functions). Support for [OpenAI functions](https://platform.openai.com/docs/guides/gpt/function-calling) (alpha)

🐳 **Docker image**. The ChatGPT Wrapper is also available as a docker image. (experimental)

:test_tube: **Flask API**. You can use the ChatGPT Wrapper as an API. (experimental)

## How it works

Run an interactive CLI in the terminal:

![kod](https://user-images.githubusercontent.com/4510758/212907070-602d61fe-708d-4a39-aaa2-0e84fcf88dcf.png)

Or just get a quick response for one question:

![kod(1)](https://user-images.githubusercontent.com/4510758/212906773-666be6fe-90e1-4f5e-b962-7748143bd744.png)

See below for details on using ChatGPT as an API from Python.

## Requirements

To use this repository, you need `setuptools` installed. You can install it using `pip install setuptools`. Make sure that you have the last version of pip: `pip install --upgrade pip`

To use the 'api' backend (the default), you need a database backend (SQLite by default, any configurable in SQLAlchemy allowed).

## Installation

### Code

#### From packages

Install the latest version of this software directly from github with pip:

```bash
pip install git+https://github.com/mmabrouk/chatgpt-wrapper
```
#### From source (recommended for development)

* Install the latest version of this software directly from git:
  ```bash
  git clone https://github.com/mmabrouk/chatgpt-wrapper.git
  ```
* Install the development package:
  ```bash
  cd chatgpt-wrapper
  pip install -e .
  ```

### Backend

The wrapper works with several different backends to connect to the ChatGPT models, and installation is different for each backend.

#### API (REST-based): **DEFAULT**

* Pros:
  * Fast (many operations run locally for speed)
  * Simple API authentication
  * Full model customizations
  * You control your data
* Cons:
  * Only paid version available (as of this writing)
  * More complex setup suitable for technical users

Grab an API key from [https://platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys)

Export the key into your local environment:

```bash
export OPENAI_API_KEY=<API_KEY>
```

Windows users, see [here](https://www.computerhope.com/issues/ch000549.htm) for how to edit environment variables.

To tweak the configuration for the current profile, see [Configuration](#configuration)

##### Database configuration

The API backend requires a database server to store conversation data. The wrapper leverages [SQLAlchemy](https://www.sqlalchemy.org/) for this.

The simplest supported database is SQLite (which is already installed on most modern operating systems), but you can use any database that is supported by SQLAlchemy.

Check the `database` setting from the `config` command above, which will show you the currently configured connection string for a default SQLite database.

If you're happy with that setting, nothing else needs to be done -- the database will be created automatically in that location when you run the program.

##### Initial user creation and login

Once the database is configured, run the program with no arguments:

```bash
chatgpt
```

It will recognize no users have been created, and prompt you to create the first user:

* Username: Required, no spaces or special characters
* Email: Optional
* Password: Optional, if not provided the user can log in without a password

Once the user is created, execute the `/login` command with the username:

```bash
/login [username]
```

Once you're logged in, you have full access to all commands.

**IMPORTANT NOTE:** The user authorization system from the command line is 'admin party' -- meaning every logged in user has admin privileges, including editing and deleting other users.

##### Setting a per-user default preset

The API backend supports configuring a preset per user.

To do so, run `/user-edit` and selecting a default preset will be one of the options.

See [Presets](#presets) for more information on configuring presets.

#### Playwright (browser-based): **DEPRECATED**

This backend is deprecated, and may be removed in a future release.

Support will not be provided for using the `ChatGPT` class of this backend directly.

* Pros:
  * Free or paid version available (as of this writing)
  * Fairly easy to set up for non-technical users
  * Access to ChatGPT plugins (alpha, requires account with access)
* Cons:
  * Slow (runs a full browser session)
  * Clunky authentication method
  * No model customizations
  * Third party controls your data

In your profile configuration file, you'll want to make sure the backend is set to the following in order to use the browser backend:

```yaml
backend: 'browser'
```

To tweak the configuration for the current profile, see [Configuration](#configuration)

Install a browser in playwright (if you haven't already). The program will use firefox by default.

```
playwright install firefox
```

Start up the program in `install` mode:

```bash
chatgpt install
```

This opens up a browser window. Log in to ChatGPT in the browser window, walk through all the intro screens, then exit program.

```bash
1> /exit
```

Restart the program without the `install` parameter to begin using it.

```bash
chatgpt
```

##### Using ChatGPT Plugins (alpha)

Officially approved ChatGPT plugins can be configured for use with the browser backend.

**NOTE:** This requires your OpenAI login account to have access to ChatGPT plugins.

To use plugins:

1. You must use a model that supports plugins: `/model model_name gpt-4-plugins`
2. Browse the plugins: `/plugins`, or a filter the full list by a phrase, `/plugins youtube`
3. To enable the plugin by default, add the plugin ID to the `browser.plugins` list in your configuration file:
   ```yaml
   browser:
     plugins:
       - plugin-d1d6eb04-3375-40aa-940a-c2fc57ce0f51
   ```
4. You can also dynamically enable/disable plugins, see the help for `/plugin-enable` and `/plugin-disable`

##### Using ChatGPT with browsing (alpha)

**NOTE:** This requires your OpenAI login account to have access to ChatGPT with browsing.

To use ChatGPT with browsing, you must use a model that supports browsing: `/model model_name gpt-4-browsing`

### Notes for Windows users

Most other operating systems come with SQLite (the default database choice) installed, Windows may not.

If not, you can grab the 32-bit or 64-bit DLL file from [https://www.sqlite.org/download.html](https://www.sqlite.org/download.html), then place the DLL in `C:\Windows\System32` directory.

You also may need to install Python, if so grab the latest stable package from [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/) -- make sure to select the install option to `Add Python to PATH`.

For the `/editor` command to work, you'll need a command line editor installed and in your path. You can control which editor is used by setting the `EDITOR` environment variable to the name of the editor executable, e.g. `nano` or `vim`.

## Configuration

Run the program with the 'config' command:

```bash
chatgpt config
```

This will show all the current configuration settings, the most important ones for installation are:

* **Config dir:** Where configuration files are stored
* **Current profile:** (shown in the 'Profile configuration' section)
* **Config file:** The configuration file current being used
* **Data dir:** The data storage directory

From a running `chatgpt` instance, execute `/config` to view the current configuration.

Configuration is optional, default values will be used if no configuration profile is
provided. The default configuation settings can be seen in
[config.sample.yaml](/config.sample.yaml) -- the file is commented with descriptions 
of the settings -- DON'T just copy this file as your configuration! Instead, use it as
a reference to tweak the configuration to your liking.

*NOTE:* Not all settings are available on all backends. See the example config for more information.

Command line arguments overrride custom configuration settings, which override default
configuration settings.

### Editing the configuration for the current profile

1. Start the program: `chatgpt`
2. Open the profile's configuration file in an editor: `/config edit`
3. Edit file to taste and save
4. Restart the program

## Configuring model properties

To change the properties of a particular LLM model, use the `/model` command:

```
/model model_name gpt-3.5-turbo
/model temperature 1.0
```

The `/model` command works within the models of the currently loaded provider.

NOTE: The attributes that a particular model accepts are beyond the scope of this 
document. While some attributes can be displayed via command completion in the
shell, you are advissed to consult the API documentation for the specific provider
for a full list of available attributes and their values.

## Presets

Presets allow you to conveniently manage various provider/model configurations.

As you use the CLI, you can execute a combination of `/provider` and `/model`
commands to set up a provider/model configuration to your liking.

Once you have the configuration set up, you can 'capture' it by saving it as a
preset.

To save an existing configuration as a preset:

```
/preset-save mypresetname
```

Later, to load that configuration for use:

```
/preset-load mypresetname
```

See `/help` for the various other preset commands.

## Templates

The wrapper comes with a full template management system.

Templates allow storing text in template files, and quickly leveraging the contents as your user input.

Features:

 * Per-profile templates
 * Create/edit templates
 * `{{ variable }}` syntax substitution
 * Five different workflows for collecting variable values, editing, and running

See the various `/help template` commands for more information.

### Builtin variables

The wrapper exposes some builtin variables that can be used in templates:

 * `{{ clipboard }}` - Insert the contents of the clipboard

### Front matter

Templates may include front matter (see [examples](examples/templates)).

These front matter attributes have special functionality:

* title: Sets the title of new conversations to this value
* description: Displayed in the output of `/templates`
* request_overrides: A hash of model customizations to apply when the template is run:
  * preset: An existing preset for the provider/model configuration to use when running
            the template (see [Presets](#presets))

All other attributes will be passed to the template as variable substitutions.

## Plugins

### Using plugins

1. Place the plugin file in either:
  * The main `plugins` directory of this module
  * A `plugins` directory in your profile

2. Enable the plugin in your configuration:

   ```yaml
   plugins:
     enabled:
       # This is a list of plugins to enable, each list item should be the name of a plugin file, without the extension.
       - test
   ```
   Note that setting `plugins.enabled` will overwrite the default enabled plugins. see `/config` for a list of default enabled plugins.

### Core plugins:

* **test:** Test plugin, echos back the command you give it
* **awesome:** Use a prompt from Awesome ChatGPT Prompts: [https://github.com/f/awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)
* **database:** Send natural language commands to a database **WARNING: POTENTIALLY DANGEROUS -- DATA INTEGRITY CANNOT BE GUARANTEED.**
* **data_query:** Send natural language commands to a loaded file of structured data
* **shell:** Transform natural language into a shell command, and optionally execute it **WARNING: POTENTIALLY DANGEROUS -- YOU ARE RESPONSIBLE FOR VALIDATING THE COMMAND RETURNED BY THE LLM, AND THE OUTCOME OF ITS EXECUTION.**
* **zap:** Send natural language commands to Zapier actions: [https://nla.zapier.com/get-started/](https://nla.zapier.com/get-started/)

### Provider plugins (alpha, subject to change):

**NOTE:** Most provider plugins are *not* chat-based, and instead return a single response to any text input.
These inputs and responses are still managed as 'conversations' for storage purposes, using the same storage
mechanism the chat-based providers use.

#### Supported providers

**NOTE:** While these provider integrations are working, none have been well-tested yet.

* **provider_ai21:** Access to [AI21](https://docs.ai21.com/docs/jurassic-2-models) models
* **provider_cohere:** Access to [Cohere](https://docs.cohere.com/docs/models) models
* **provider_huggingface_hub:** Access to [Huggingface Hub](https://huggingface.co/models) models
* **provider_openai:** Access to non-chat [OpenAI](https://platform.openai.com/docs/models) models (GPT-3, etc.)

#### Usage

To enable a supported provider, add it to `plugins.enabled` list in your configuration.

```yaml
plugins:
  enabled:
    - provider_openai
```

See `/providers` for a list of currently enabled providers.

See `/help provider` for how to switch providers/models on the fly.

### Writing plugins

There is currently no developer documentation for writing plugins.

The `plugins` directory has some default plugins, examining those will give a good idea for how to design a new one.

Currently, plugins for the shell can only add new commands. An instantiated plugin has access to these resources:

* `self.config`: The current instantiated Config object
* `self.log`: The instantiated Logger object
* `self.backend`: The instantiated backend
* `self.shell`: The instantiated shell

To write new provider plugins, investigate the existing provider plugins as examples.

## Tutorials:

- **Newest Youtube video:** [ChatCPT intro, walkthrough of features](https://www.youtube.com/watch?v=Ho3-pzAf5e8)
- Youtube Tutorial: [How To Use ChatGPT With Unity: Python And API Setup #2](https://www.youtube.com/watch?v=CthF8c8qk4c) includes a step by step guide to installing this repository on a windows machine
- This [Blog post](https://medium.com/geekculture/using-chatgpt-in-python-eeaed9847e72) provides a visual step-by-step guide for installing this library.

## Usage

### Shell

#### Command line arguments

Run `chatgpt --help`

#### One-shot mode

To run the CLI in one-shot mode, simply follow the command with the prompt you want to send to ChatGPT:

```
chatgpt Hello World!
```

#### Interactive mode

To run the CLI in interactive mode, execute it with no additional arguments:

```
chatgpt
```

Once the interactive shell is running, you can see a list of all commands with:

```
/help
```

...or get help for a specific command with:

```
/help <command>
```

### Python

**IMPORTANT:** Use of browser backend's `ChatGPT` class has been deprectated, no support will be provided for this usage.

You can  use the API backend's `ApiBackend` class to interact directly with the chat LLM.

Create an instance of the class and use the `ask` method to send a message to OpenAI and receive the response. For example:

```python
from lwe import ApiBackend

bot = ApiBackend()
success, response, message = bot.ask("Hello, world!")
if success:
    print(response)
else:
    raise RuntimeError(message)
```

The ask method takes a string argument representing the message to send to the API, and returns a string representing the response received.

You may also stream the response as it comes in from the API in chunks using the `ask_stream` generator.

To pass custom configuration to ChatGPT, use the Config class:

```python
from lwe import ApiBackend
from lwe.core.config import Config

config = Config()
config.set('browser.debug', True)
bot = ApiBackend(config)
success, response, message = bot.ask("Hello, world!")
if success:
    print(response)
else:
    raise RuntimeError(message)
```

### Workflows

**NOTE: Alpha, subject to change**

The wrapper supports more complex linear workflows via built-in integration for [Ansible playbooks](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html).

Some example workflows are included, run `/workflows` to list them, and `/workflow-show workflowname` to view the playbook configuration for a particular workflow.

To execute a workflow, run `/workflow-run workflowname` -- depending on configuration, workflows can either be run ad hoc (not saved to the database), or associated with a conversation stored in the database.

See `/help` for the various other workflow commands.

The wrapper implements a custom Ansible module, `lwe_llm`, which handles communicating with the LLM and storing the response for each task execution. For supported arguments and return values, see the [module documentation](/lwe/backends/api/workflow/library/lwe_llm.py).

It is also possible to execute workflows directly with `ansible-playbook`, by simply navigating to the `lwe/backends/api/workflow` directory:

```bash
ansible-playbook playbooks/hello-world.yaml
```

### Functions

**NOTE: Alpha, subject to change**

The wrapper supports [OpenAI functions](https://platform.openai.com/docs/guides/gpt/function-calling) for all models that support it.

Mutiple functions may be attached, and the LLM can choose to call any or all of the attached functions.

The example configuration below assumes you want to add a new function called `test_function`.

#### Creating functions.

Functions are created as callable Python classes, that inherit from the base `Function` class.

The class name must be the camel-cased version of the snake-cased function name, so `test_function` becomes `TestFunction`.

There is one required method to implement, `__call__`, and its return value must be a dictionary -- this is what will be
returned to the LLM as the result of the function call.

```python
from lwe.core.function import Function

class TestFunction(Function):
    def __call__(self, word: str, repeats: int, enclose_with: str = '') -> dict:
        """
        Repeat the provided word a number of times.

        :param word: The word to repeat.
        :type content: str
        :param repeats: The number of times to repeat the word.
        :type repeats: int
        :param enclose_with: Optional string to enclose the final content.
        :type enclose_with: str, optional
        :return: A dictionary containing the repeated content.
        :rtype: dict
        """
        try:
            repeated_content = " ".join([word] * repeats)
            enclosed_content = f"{enclose_with}{repeated_content}{enclose_with}"
            output = {
                'result': enclosed_content,
                'message': f'Repeated the word {word} {repeats} times.',
            }
        except Exception as e:
            output = {
                'error': str(e),
            }
        return output
```

The file should be named `[function_name].py`, e.g. `test_function.py`, and be placed in the `functions` directory
in either the base config directory, or in the profile config directory. (These directories are listed in the output
of the `/config` command).

#### Providing the function definition

In the example above, notice both the [type hints](https://docs.python.org/3/library/typing.html) in the function signature (e.g. `word: str`),
and the [reStructured text](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html) documentation of the method arguments.
This is the default method for providing the function definition to the OpenAI API.

Alternatively, you may provide the function definition by creating a `[function_name].config.yaml` file in the same location as the
`[function_name].py` file, e.g. `test_function.config.yaml` -- if provided, its contents will be used instead of the default
method.

Finally, for full control, you may override the `get_config()` method of the base `Function` class, and return
a dictionary of the function definition.

#### Attaching functions.

For now, the function list must be attached to a [preset](#presets), as a list of function names, like so:

```yaml
metadata:
  name: gpt-4-function-test
  provider: chat_openai
  # Add this to have the FIRST function CALL response from the LLM returned directly.
  # return_on_function_call: true
  # Add this to have the LAST function RESPONSE from the LLM returned directly.
  # return_on_function_response: true
model_customizations:
  # Other attributes.
  model_name: gpt-4-0613
  model_kwargs:
    # Functions are added under this key, as a list of function names.
    # Multiple functions can be added.
    functions:
      - test_function
```

A preset can be edited by using the `/preset-edit` command:

Note the special `return_on_function_call` and `return_on_function_response` metadata attributes, which can be used to
control the return value, useful when using the `ApiBackend`module, or via [workflows](#workflows)

#### Support for Langchain tools

[Langchain](https://docs.langchain.com) has many useful [tools](https://python.langchain.com/docs/modules/agents/tools/) that
can be used in function calls.

To use a Langchain tool as function:

1. Find the name of the tool class, e.g. `MoveFileTool` or `ShellTool`.
2. Prefix that class name with `Langchain-`
3. Add it to the `functions` list for the preset:
   ```yaml
   metadata:
     # Usual preset metadata.
   model_customizations:
     # Other attributes.
     model_kwargs:
       functions:
         - Langchain-ShellTool
   ```


### Flask API (experimental)

- Run `python lwe/gpt_api.py --port 5000` (default port is 5000) to start the server
- Install pytest: `pip install pytest`
- Test whether it is working using `pytest tests/integration/api_test.py`
- See an example of interaction with api in `tests/integration/example_api_call.py`

## Docker (experimental)

Build a docker image for testing `chatgpt-wrapper`:

Make sure your OpenAI key has been exported into your host environment as `OPENAI_API_KEY`

Run the following commands:

```bash
docker-compose build && docker-compose up -d
docker exec -it lwe-container /bin/bash -c "lwe"
```

Follow the instructions to create the first user.

Enjoy the chat!

## Test suite

The project uses [Pytest](https://docs.pytest.org).

```
pip install pytest
```

To run all tests:

```
pytest
```

## Troubleshooting

### OpenAI system issues

**Oftentimes issues are related to upstream service problems with OpenAI, so please check [https://status.openai.com](https://status.openai.com) before concluding there's an issue with this codebase!**

### Playwright (browser-based) backend issues

It's possible that:

1. Your session has gone stale: Try issuing a `/session` command to refresh it
2. Your browser session information is corrupted: Try `chatgpt reinstall` and go through the login process again
3. You're running an outdated version of this project, or one of its dependencies: Completely reinstall the project and its dependencies
4. You're running into geolocation restrictions in OpenAI's security systems: Try proxying your requests through a VPN server in the US.

## Upgrading:

### PLEASE HEED THESE IMPORTANT WARNINGS

1. This is a pre-release project
  * Breaking changes are happening regularly
  * **Before you upgrade and before you file any issues related to upgrading, refer to the `Breaking Changes` section for all releases since your last upgrade.**
2. Back up your database
  * Some releases include changes to the database schema
  * **If you care about any data stored by this project, back it up before upgrading**
  * Common upgrade scenarios are tested with the default database (SQLite), but data integrity is **not** guaranteed
  * If any database errors occur during an upgrade, roll back to an earlier release and [file an issue](ISSUES.md)

### Via pip

Until an official release exists, you'll need to uninstall and reinstall:

```sh
pip uninstall -y chatGPT
pip install chatGPT
```

### Via git

If the package was installed via `pip install -e`, simply pull in the latest changes from the repository:

```sh
git pull
```

## GPT4

### API backend

To use GPT-4 with this backend, you must have been granted access to the model in your OpenAI account.

NOTE: If you have not been granted access, you'll probably see an error like this:

```
InvalidRequestError(message='The model: `gpt-4` does not exist', param=None, code='model_not_found', http_status=404, request_id=None)
```

There is nothing this project can do to fix the error for you -- contact OpenAI and request GPT-4 access.

Follow one of the methods below to utilize GPT-4 in this backend:

##### Method 1: Set a default preset configured with GPT-4

See [Presets](#presets) above to configure a preset using GPT-4

Add the preset to the config file as the default preset on startup:

```yaml
# This assumes you created a preset named 'gpt-4'
model:
  default_preset: gpt-4

```

##### Method 2: Dynamically switch

From within the shell, execute this command:

```
/model model_name gpt-4
```

...or... if you're not currently using the 'chat_openai' provider:

```
/provider chat_openai gpt-4
```

### Playwright (browser-based) backend: **DEPRECATED**

To use GPT-4 with this backend, you must have a ChatGPT-Plus subscription.

Follow one of the methods below to utilize GPT-4 in this backend:

##### Method 1: Command line argument

Enter the following command in your shell:

```
chatgpt --model=gpt4
```

##### Method 2: Modify the `config.yaml` file

Update your `config.yaml` file to include the following line:

```
chat:
  model: gpt4
```

Then start the program normally:

```
chatgpt
```

##### Method 3: Dynamically switch

From within the shell, execute this command:

```
/model gpt4
```

### Python module

To use GPT-4 within your Python code, you must use [Presets](#presets).

The code below uses the system-defined `gpt-4-chatbot-responses` preset:

```python
from lwe import ApiBackend
from lwe.core.config import Config

config = Config()
config.set('model.default_preset', 'gpt-4-chatbot-responses')
bot = ApiBackend(config)
success, response, message = bot.ask("Hello, world!")
```

## Projects built with chatgpt-wrapper

- [bookast: ChatGPT Podcast Generator For Books](https://github.com/SamMethnani/bookast)
- [ChatGPT.el: ChatGPT in Emacs](https://github.com/joshcho/ChatGPT.el)
- [ChatGPT Reddit Bot](https://github.com/PopDaddyGames/ChatGPT-RedditBot)
- [Smarty GPT](https://github.com/citiususc/Smarty-GPT/tree/v1.1.0)
- [ChatGPTify](https://github.com/idilsulo/ChatGPTify)
- [selection-to-chatgpt](https://github.com/collin-murphy/selection-to-chatgpt)

## Contributing

We welcome contributions to ChatGPT Wrapper! If you have an idea for a new feature or have found a bug, please open an issue on the GitHub repository.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- The original 'browser' backend is a modification from [Taranjeet](https://github.com/taranjeet/chatgpt-api) code which is a modification of [Daniel Gross](https://github.com/danielgross/whatsapp-gpt) code.

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=mmabrouk/chatgpt-wrapper&type=Date)](https://star-history.com/#mmabrouk/chatgpt-wrapper&Date)
