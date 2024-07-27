---
layout: post
title:  "Installing PyTorch Lightning on macos ARM Sonoma 14.5 "
date:   2024-07-27 10:25:13 -0600
---

PyTorch is the most widely used open source library for deep learning and AI.  

Open your terminal.app

Install homebrew (if it isn't already installed):
{% highlight bash %}
/bin/bash -c "$(curl -fsSL <https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh>)"
{% endhighlight %}


Install miniforge
{% highlight bash %}
brew install miniforge
{% endhighlight %}

If you have a ~/.condarc file Remove the defaults so mamba will work correctly.
{% highlight bash %}
sed '/^[[:space:]]*- defaults[[:space:]]*$/d' ~/.condarc > ~/.condarc
{% endhighlight %}

Init Conda per brew install instructions:
{% highlight bash %}
mamba init "$(basename "${SHELL}")"
{% endhighlight %}


Restart your terminal by exiting the terminal or just using the: ⌘+T key combination to start a new terminal tab in the macos terminal.app.

{% highlight bash %}
mamba create -n lightning
mamba activate lightning
mamba install lightning -c conda-forge
{% endhighlight %}
