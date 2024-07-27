---
layout: post
title:  "Installing PyTorch on macos ARM Sonoma 14.5 "
date:   2024-07-27 10:25:13 -0600
---

PyTorch is the most widely used open source library for deep learning and AI. Here i show how to install on macos by creating a mamba environment via miniforge3.  

Open your terminal.app

Install homebrew (if it isn't already installed):
```bash
/bin/bash -c "$(curl -fsSL <https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh>)"
```


Install miniforge
```bash
brew install miniforge
```

If you have a ~/.condarc file Remove the defaults so mamba will work correctly.
```bash
sed '/^[[:space:]]*- defaults[[:space:]]*$/d' ~/.condarc > ~/.condarc
```

Init Conda per brew install instructions:
```bash
mamba init "$(basename "${SHELL}")"
```


Restart your terminal by exiting the terminal or just using the: ⌘+T key combination to start a new terminal tab in the macos terminal.app.

```bash
mamba create -n pytorch
mamba activate pytorch
mamba install pytorch torchvision -c pytorch
```

Run the python interpreter and make sure pytorch works:
```bash
python
```

You should see something like this:
```bash
Python 3.12.4 | packaged by conda-forge | (main, Jun 17 2024, 10:13:44) [Clang 16.0.6 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
```


Then run:
```python
import torch
x = torch.rand(5, 3)
print(x)
```

And you should get something like this as the print out:

```python
tensor([[0.8157, 0.6091, 0.1054],
        [0.2226, 0.0481, 0.0551],
        [0.9921, 0.1987, 0.6182],
        [0.2014, 0.1642, 0.7176],
        [0.8058, 0.7948, 0.9841]])
```

and then exit when done:

```python
quit()
```


Now if you want to install pytorch lightning you can create a new environment like so:

```bash
mamba create -n lightning
mamba activate lightning
mamba install lightning -c conda-forge
```

Then you can follow the steps to test pytorch lightning [here](https://lightning.ai/docs/pytorch/stable/starter/introduction.html#define-a-lightningmodule)