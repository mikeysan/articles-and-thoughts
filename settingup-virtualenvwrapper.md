*#this is just a holding spot for me notes#*

### Things that I found to be different from the guide I was following.

###### Location to where virtualenvwrapper was installed

- using `pip3 install virtualenvwrapper` on Mint 20.01

```bash
Successfully built virtualenvwrapper
Installing collected packages: pbr, stevedore, appdirs, filelock, distlib, virtualenv, virtualenv-clone, virtualenvwrapper
  WARNING: The script pbr is installed in '/home/sspade/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  WARNING: The script virtualenv is installed in '/home/sspade/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  WARNING: The script virtualenv-clone is installed in '/home/sspade/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
```


- Editing ".bashrc" required changing the path to match installed location.

```bah
# virtualenvwrapper settings
export WORKON_HOME=$HOME/.virtualenvs
VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
#. /usr/local/bin/virtualenvwrapper.sh  # this line was commented out and changed to the one below
. /home/sspade/.local/bin/virtualenvwrapper.sh
```

- save .bashrc file and then run `source ~/.bashrc`
- You should now see the following output confrm changes went well

```bash
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/premkproject
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/postmkproject
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/initialize
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/premkvirtualenv
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/postmkvirtualenv
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/prermvirtualenv
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/postrmvirtualenv
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/predeactivate
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/postdeactivate
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/preactivate
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/postactivate
virtualenvwrapper.user_scripts creating /home/sspade/.virtualenvs/get_env_details
```
