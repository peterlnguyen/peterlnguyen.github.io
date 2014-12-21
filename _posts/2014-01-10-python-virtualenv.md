---
layout: post
title: Python Virtualenv
permalink: python-virtualenv
tags: python, linux
---


<div class="message">
  Setting up virtualenv to manage temporary python installs according to <a href="http://stackoverflow.com/a/7237949/1203188">this helpful Stack Overflow answer</a>
</div>

### What is virtualenv?

[virtualenv](http://virtualenv.readthedocs.org/en/latest/virtualenv.html) is a tool to create isolated python environments.  

It's useful for painlessly managing multiple versions of python when you have, for example, different projects that require python 2 and python 3 separately.   

It's analogous to [nvm](https://github.com/creationix/nvm) for node.js and [rvm](https://rvm.io/) or [rbenv](https://github.com/sstephenson/rbenv) for ruby.  


### Install virtualenv

Run multiple versions of python on Arch linux.  
```
pacman -S python2-virtualenv
```

### Install python onto virtualenv

Use this to create your temporary python "install"  
(Assuming that is the correct path to the python interpreter you want to use.)  
```
virtualenv -p /usr/bin/python2.7 --distribute temp-python  
```

Type this command when you want to use your temporary python.  
```
source temp-python/bin/activate  
```

While you are using your temporary python you will also have access to a temporary pip,  which will keep all packages installed with it seperate from your main python install.

### Deactivate python on virtualenv

To deactivate your temporary python version, simply issue command `deactivate`.

### Further Reading
[python 2 instead of python 3 as the (temporary) default python?](http://stackoverflow.com/a/7237949)


-----
