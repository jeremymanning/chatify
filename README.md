# Chatify 🤖

A python package that enables ipython magic commands to Jupyter notebooks that provide LLM-driven enhancements to markdown and code cells.  This package is currently in the *alpha* stage: expect broken things, crashes, bad (wrong, misleading) answers, and other issues.

# Background

This tool was created to supplement the [NeuroMatch Academy](https://compneuro.neuromatch.io/tutorials/intro.html) materials.  To reign in costs in this initial version, we've used [ChatGPT](https://chat.openai.com/chat) to pre-generate and cache responses for all of the current NeuroMatch materials.  The cached responses are included by default when you install chatify in your environment, so running queries using those materials does not require any additional setup (nor do you need an OpenAI API key).

## Installing and enabling Chatify: default NeuroMatch version
To install and enable chatify in any NeuroMatch tutorial notebook, add the following two cells to the top of your notebook (and run them):

```python
%pip install davos
import davos
davos.config.suppress_stdout = True
```

```python
smuggle chatify   # pip: git+https://github.com/ContextLab/chatify.git
%load_ext chatify
```

No further setup is required.  To use Chatify to automatically explain any code in the notebook, simply insert the `%%explain` magic command at the top of the code cell and then run it (shift + enter) to access the Chatify interface for receiving LLM-based assistance.  To disable Chatify and run the code block as usual, simply delete the `%%explain` command and re-run the cell.

## Installing and enabling Chatify: General version

By default, Chatify only supports cached responses.  To enable full-on interactive mode (and in arbitrary notebooks, including non-NeuroMatch notebooks), you'll first need an [OpenAI API key](https://help.openai.com/en/collections/3675940-getting-started-with-openai-api).  Once you have your key, create a `config.yaml` file in the directory where your
notebook is located.  Replace `<OPENAI API KEY>` with your actual OpenAI API key (with no quotes) and then save the following in your `config.yaml` file:

```yaml
cache_config:
  cache: True
  caching_strategy: exact  # alternative: similarity
  cache_db_version: 0.1
  url: https://www.dropbox.com/scl/fi/qw2lcscz7izpfk55lvruh/neuro_match_llm_cache_0.1.txt?rlkey=k7sfksk5x0x02t1rh3qxrc4ay&dl=1

feedback: False

model_config:
  open_ai_key: <OPENAI API KEY>
  model: open_ai_model
  model_name: gpt-3.5-turbo  # alternative: gpt-4 (more expensive and slower, but higher-quality responses)

chain_config:
  chain_type: default
```

After saving your `config.yaml` file, follow the "**Installing and enabling Chatify: default NeuroMatch version**" instructions.  Note that any non-cached responses you request will use your OpenAI API key to query ChatGPT, and your account will be billed accordingly.  We recommend enabling [usage limits](https://platform.openai.com/account/billing/limits) on your OpenAI account to prevent unexpected costs.


# What do I do if I have questions or problems?

We'd love to hear from you!  Please consider filling out our [feedback survey](https://forms.gle/V9ZGssyukjmFR9bk7) or submitting an [issue](https://github.com/ContextLab/chatify/issues).


# I want to help!

Yay-- welcome!  This is a new project (in the "concept" phase) and we're looking for all the help we can get!  If you're new around here and want to explore/contribute, here's how:

1. [Fork](https://github.com/ContextLab/chatify/fork) this repository so that you can work with your own "copy" of the code base
2. Take a look at our [Project Board](https://github.com/orgs/ContextLab/projects/3) and/or the list of open [issues](https://github.com/ContextLab/chatify/issues) to get a sense of the current project status, todo list, etc.
3. Feel free to add your own issues/tasks, comment on existing issues, etc.

## Current priorities and suggested tasks to start with

In general, we've broken down tasks into ["coding" tasks](https://github.com/ContextLab/chatify/labels/coding%20required) (which require some amount of coding, likely in Python) and ["non-coding" tasks](https://github.com/ContextLab/chatify/labels/non-coding) (which do *not* require coding).

If you have questions, ideas, etc., also please check out the [discussion board](https://github.com/ContextLab/chatify/discussions)!
