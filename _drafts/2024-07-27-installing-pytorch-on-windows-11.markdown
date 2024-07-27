---
layout: post
title:  "Installing PyTorch on Windows 11 "
date:   2024-07-27 12:25:13 -0600
---

PyTorch is the most widely used open source library for deep learning and AI.   Here i show how to install on Windows 11 by creating a mamba environment via miniforge3.  

Press `Win + X` and Select [**Windows Terminal (Admin)**](https://apps.microsoft.com/detail/9n0dx20hk701?launch=true&mode=full&hl=en-us&gl=us&ocid=bingwebsearch) or **Windows Powershell(Admin)** and run the commands below:

Install miniforge3
{% highlight powershell %}
Invoke-WebRequest -Uri "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Windows-x86_64.exe" -OutFile "Miniforge3-Windows-x86_64.exe"
Start-Process -FilePath ".\Miniforge3-Windows-x86_64.exe" -NoNewWindow -Wait
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

