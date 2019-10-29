# Config VSCode Restructuredtext Plugin

This document intend to organize the steps to config VSCode Restructured text plugin, with and excelent documentation for some goals but in the official doc some of the present details are missing.

## Prerequisites for VSCode Plugin

* sphinx
* sphinx-autobuild
* docutils
* doc8

__Note:__ You can add this to your venv using next command

```bash
$ pip install sphinx sphinx-autobuild docutils doc8
```

## Config your Venv inside VSCode

It is better to work with your personal python virtualenv.

* Go to _File_ > _preferences_ > _Settings_.
* Click on Workspace settings.
* Under __Files:Association__, you will find "_Edit in settings.json_" , click on that.
* Update "[python.pythonPath]()": "Your_venv_path/bin/python" under workspace settings.

### Example

```javascript
"python.pythonPath": "/home/user/pydev/bin/python3",
```

Restart VSCode in case if it still doesn't show your venv.

## Config VSCode settings.js

Finally you need that the plugin finds the conf.py file, to pre-build the doc. You need to add another parameter to your settings.js

* "restructuredtext.confPath": "/path/to/your_conf.py"

### Example

```javascript
"restructuredtext.confPath": "/media/user/"
```

## CopyRight

This doc is licensed under MIT License, Read [LICENSE](../LICENSE)