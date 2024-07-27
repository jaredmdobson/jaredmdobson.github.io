---
layout: post
title:  "Install mojo on macos via homebrew"
date:   2024-06-18 09:48:17 -0600
---
Mojo looks pretty exciting so here's how i got it working on my machine, good luck!

Open your terminal.app

Install homebrew (if it isn't already installed):
```bash
/bin/bash -c "$(curl -fsSL <https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh>)"
```

Then install python version 3.11 (currently the highest supported version by Mojo)

```bash
brew install python@3.11
```

Then add the python executables to your path:
```bash
echo 'export PATH="/opt/homebrew/opt/python@3.11/libexec/bin:$PATH"' >> ~/.zshrc \
  && source ~/.zshrc
```

pipx - Install and Run Python Applications in Isolated Environments:
```bash
brew install pipx
pipx ensurepath
sudo pipx ensurepath --global
```

Change to your workspace directory 
 OR use this code to create a development folder in your home directory:
```bash
mkdir ~/Development && cd ~/Development
```

Ensure that you get something like "Python 3.11.9" when you run:
```bash
python3 --version
```

It may have a different Patch Level 3.11.x, like 3.11.10 as long as it is 3.11 or the latest supported version by mojo.

Install Mojo 
```bash
curl -s https://get.modular.com | sh -
```

Activate a python venv for mojo

```bash
python3 -m venv mojo-venv && source mojo-venv/bin/activate
```

Then install mojo via the modular package manager:
```bash
modular install mojo
```

And add required modular and mojo to your path:
```bash
MOJO_PATH=$(modular config mojo.path) \
  && echo 'export MODULAR_HOME="'$HOME'/.modular"' >> ~/.zshrc \
  && echo 'export PATH="'$MOJO_PATH'/bin:$PATH"' >> ~/.zshrc \
  && source ~/.zshrc  
```

Now you should be able to run the mojo repl
```bash
mojo repl
```

And get something like this:
```bash
Welcome to Mojo! 🔥

Expressions are delimited by a blank line.
Type `:quit` to exit the REPL and `:mojo help` for further assistance.

  1>  

```


Good luck!