# CLAIRify
## Errors are Useful Prompts: Instruction Guided Task Programming with Verifier-Assisted Iterative Prompting

- Project website: https://ac-rad.github.io/clairify/

This repository contains
- The source code for CLAIRify
- Dataset (Chem-RnD and Chem-EDU)
- CLAIRify web interface

## Albert's Modifications:

- Modifications are only on the web verify.py right now and pare down the XDL into something that is more relevant for our code base
- Removed hyper-chemistry specific things such as titration/stirring for resuspending/centrifuge etc.
- Fixed a requirements file

Thoughts:
XDL is still pretty human readable to understand if the steps are in order, but this could be made into a visual representation and sketched out.

Questions of exploration: 

[] Do we need to formulate our own XDL version which will be constructed of skills that our robot can do (i.e. Centrifuge, FlaskManipulation). Proof of concept in the works!
[] If we formulate our own XDL version, we should have a way to auto-generate the verifier and also auto-generate the XDL_description.txt
[] We should have human feedback forwarded to the XDL and looped back into the LLM. This way they can change the directions or XDL if the ordering is incorrect. 
[] Where are the limitations? Should users be feeding in pieces of their protocol in larger steps? Can we ingest a complex protocol with multiple repeats? 

### Tutorial
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ac-rad/xdl-generation/blob/master/tutorial.ipynb)

A tutorial on CLAIRify is provided as [Jupyter Notebook](https://github.com/ac-rad/xdl-generation/blob/master/tutorial.ipynb).

### Requirement
- OpenAI Python Library

You need to set your OpenAI API key in `OPENAI_API_KEY` environment variable.

### How to run
To generate a XDL protocol from a natural language description of an experiment, run the following: 

`python3 xdlgenerator/nlp2xdl.py --input_dir /path/to/experiment/dir` 

where `/path/to/experiment/dir` is a directory containing natural language experiments. Each experiment is assumed to be its own file in the dictory (e.g. expertiment1.txt, experiment2.txt). Running the script will automatically generate an output directory `/path/to/experiment/dir_output`. Each file in the new directory contains a XDL description.
