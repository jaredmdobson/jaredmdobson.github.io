---
layout: post
title:  "Getting started with Mojo on macOS"
date:   2024-06-18 09:48:17 -0600
categories: mojo python data-science ai
---
Running numpy in Mojo is 20,000x faster on macbook!  That is incredible!  Let's get this going on our machine!

Open your terminal app and Install homebrew (if it isn't already installed):
{% highlight bash %}
/bin/bash -c "$(curl -fsSL <https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh>)"
{% endhighlight %}

Then install python version 3.11 (currently the highest supported version by Mojo)

{% highlight bash %}
brew install python@3.11
{% endhighlight %}

Then add the python executables to your path:
{% highlight bash %}
echo 'export PATH="/opt/homebrew/opt/python@3.11/libexec/bin:$PATH"' >> ~/.zshrc \
  && source ~/.zshrc
{% endhighlight %}

Change to your workspace directory 
 OR use this code to create a development folder in your home directory:
{% highlight bash %}
mkdir ~/Development && cd ~/Development
{% endhighlight %}

Ensure that you get something like "Python 3.11.9" when you run:
{% highlight bash %}
python3 --version
{% endhighlight %}

It may have a different Patch Level 3.11.x, like 3.11.10 as long as it is 3.11 or the latest supported version by mojo.

Install Mojo 
{% highlight bash %}
curl -s https://get.modular.com | sh -
{% endhighlight %}

Activate a python venv for mojo
{% highlight bash %}
python3 -m venv mojo-venv && source mojo-venv/bin/activate
{% endhighlight %}

Then install mojo via the modular package manager:
{% highlight bash %}
modular install mojo
{% endhighlight %}

And add required modular and mojo to your path:
{% highlight bash %}
MOJO_PATH=$(modular config mojo.path) \
  && echo 'export MODULAR_HOME="'$HOME'/.modular"' >> ~/.zshrc \
  && echo 'export PATH="'$MOJO_PATH'/bin:$PATH"' >> ~/.zshrc \
  && source ~/.zshrc  
{% endhighlight %}
