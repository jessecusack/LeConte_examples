# LeConte examples (and working with python)

This repository contains some examples of working with LeConte data using python and jupyter lab. Before starting, it is recommended to [run the LeConte post-processing code](https://github.com/jessecusack/LeConte_postprocessing). You need access to the LeConte dropbox folder to run the examples (and the post-processing), but the inital instructions are general to any project.

The tutorial below works on my macbook pro running MacOS 10.15. I can't guarantee it will work on another system. 

## Setting up jupyter lab

If you don't have it already, install the python package manager [miniconda](https://docs.conda.io/en/latest/miniconda.html). 

When working with conda I find most packages are available on the [conda-forge](https://conda-forge.org/#page-top) channel. To make sure conda knows to use this channel, enter the following in your terminal.
```
conda config --add channels conda-forge
conda config --set channel_priority strict
```

Jupyter lab can be installed with conda. I personally don't create a separate environment for 
managing jupyterlab and related packages (but you definitely could), so running the following will install it in the `base` conda environment.
```
conda install jupyterlab
```

You can now start jupyter lab using
```
jupyter lab
```
which will start a new server and should open a new browser tab showing the application.

You can shut down the server at the terminal by hitting `ctrl+c` twice. Note that closing the browser tab will not shut it down.

## Next, do this.

For the purpose of this mini tutorial it will be convenient to work from the same directory using the same conda environment.

First, acquire this git repository (which might require you [install git](https://gist.github.com/kamermanpr/23bc20180dc277bc8043558f0c22f8a9)) and step inside.
```
git clone https://github.com/jessecusack/LeConte_examples.git
cd LeConte_examples
```
Now create the conda environment which specifies the python packages required to run the examples. 
```
conda env create -f environment.yml
```
The name of the environment, `lcexamples`, is specified in the yml file. If you run `conda env list` in the terminal you should see this name pop up along with all the other environments. 

For notebooks to work, you have to tell them which kernel to use. Install the kernel specification for the environment as follows:
```
conda activate lcexamples
python -m ipykernel install --user --name lcexamples --display-name lcexamples
conda deactivate
```
Doing the above will allow us to run notebooks that can access all the python packages specified in the `lcexamples` conda environment. 

Lastly, start jupyter lab.
```
jupyter lab
```

## Workspaces

Before going further it is important to mention workspaces. Jupyter lab stores information about the notebooks and text files you keep open, as well as the visual layout of the software, in what it calls a [workspace](https://jupyterlab.readthedocs.io/en/stable/user/urls.html). When you open jupyter lab, it will load the default workspace. Suppose you open a file or create a new notebook and then shut down jupyter lab. If you then reopen jupyter lab, those open files should appear again in the arrangement that you had them in previously. This is a very handy feature, but if you always work in the default space, things will get messy. It is better to keep separate workspaces for different projects.

To create a new workspace simply edit the URL in your browser. The default URL probably looks like this for you:
```
http://localhost:8888/lab
```

Edit it manually to something like
```
http://localhost:8888/lab/workspaces/WhateverNameYouWant
```
which will create a new workspace named `WhateverNameYouWant`. If you want to revist the same workspace, simply append the base URL with `/workspaces/WhateverNameYouWant`, even if the base URL has changed (i.e. the port is no longer 8888 but 8889). 

## Notebooks

With jupyter lab open, you should see a litte `+` button in the top left. Pressing this brings up the launcher (which may already be at the front anyway). 

To create a new notebook, press the button labelled 'python 3' under the notebook heading. Doing so replaces the launcher with a new untitled notebook located in the directory you're currently in (hopefully `'LeConte_examples/'`). On the left hand side of the lab interface, you can see the directory structure. 

By selecting 'python 3', you were selecting the kernal that the notebook initialises with. If the kernel specification for `lcexamples` was successfully installed following the instructions above, you should also have had the option to launch a new notebook using the 'lcexamples' button. 

You can always change the kernel that the notebook uses from within the notebook itself, by clicking the kernel name located at the top right of the notebook.

The above instructions were just a brief introduction to creating notebooks and specifying kernels. Feel free to delete the untitled notebook that you just created. 

Jupyter lab and jupyter notebooks have many great features way beyond the scope of this tutorial. I would highly recommend browsing the [documentation](https://jupyterlab.readthedocs.io/en/stable/index.html) to get an overview of their capabilities. Or just play around with jupyter lab and the examples here. 

## Running the examples

At this point, we need the LeConte data and/or [post-processed data](https://github.com/jessecusack/LeConte_postprocessing). The exact dataset required will be specified in the individual example notebooks. 

To open an example, use the left hand side bar of the jupyter lab interface to navigate to the `examples` directory. Double click on the a notebook file to open and continue following the instructions within. 

## Some useful extensions

The basic features of jupyter lab are good enough to get most things done. However, a few extensions add some very useful functionality. 

In no particular order:
* [Table of contents](https://github.com/jupyterlab/jupyterlab-toc) for easier navigation of notebooks. 
* [Jupytext](https://github.com/mwouts/jupytext) for cleaner version control of notebooks among other things. 


<!-- ### Installing jupyter lab in a new environment (optional)

It might be considered cleaner to put jupyter lab and related packages in a separate environment, in which case you could do something like this:

```
conda create --name jlab
conda activate jlab
conda install jupyterlab
```

You will have to remember to `conda activate jlab` whenever you watned to start a new instance in the terminal.  -->