# Fixing tkinter issues on Mac OS X (Catalina)

This article will help anyone who has installed python 3 on Mac OS X using pyenv.

## The Problem?

**You get one of the following errors:**

- Python may not be configured for Tk on import tkinter
- import _tkinter # If this fails your Python may not be configured for Tk
- RuntimeError: tk.h version (8.6) doesn't match libtk.a version (8.5)
- ModuleNotFoundError: No module named '_tkinter'

First, I installed homebrew. Using homebrew, I installed pyenv, and then Python. That was the wrong order.

The correct steps to avoid issues in future or fix the problem:

- Install homebrew

- Install pyenv

- Install tcl-tk

` brew install tcl-tk `

- Confirm the version and location of tcl-tk

` brew info tcl-tk `

- The output of the above command will give you a path to your tcl-tk installation.

- Follow the steps towards the end of the output. On my system, tcl-tk is installed to the following path.
```

echo 'export PATH="/usr/local/opt/tcl-tk/bin:$PATH"' >> ~/.zshrc
echo 'export LDFLAGS="-L/usr/local/opt/tcl-tk/lib"' >> ~/.zshrc
echo 'export CPPFLAGS="-I/usr/local/opt/tcl-tk/include"' >> ~/.zshrc
echo 'export PKG_CONFIG_PATH="/usr/local/opt/tcl-tk/lib/pkgconfig"' >> ~/.zshrc

```

- restart the terminal or source the updated zshrc; this is to make sure your changes to the zshrc file are active

` source ~/.zshrc `

- My final zshrc looks like
```
  export PATH="$PATH:/Users/mikeysan/development/tools/flutter/bin"`
  if command -v pyenv 1>/dev/null 2>&1; then`
    eval "$(pyenv init -)"`
  fi`
  export PATH="/usr/local/opt/tcl-tk/bin:$PATH"
  export LDFLAGS="-L/usr/local/opt/tcl-tk/lib"
  export CPPFLAGS="-I/usr/local/opt/tcl-tk/include"
  export PKG_CONFIG_PATH="/usr/local/opt/tcl-tk/lib/pkgconfig"

```
- If you have already installed Python, you will need to uninstall it

` pyenv uninstall <python-version>``` E.g ``` pyenv uninstall 3.8.5 `

- Update 'PYTHON_CONFIGURATION_OPTS' environment variable via terminal OR

` env PYTHON_CONFIGURE_OPTS="--with-tcltk-includes='-I$(brew --prefix tcl-tk)/include' --with-tcltk-libs='-L$(brew --prefix tcl-tk)/lib -ltcl8.6 -ltk8.6'" `

- Edit python-build file

`vim /usr/local/Cellar/pyenv/1.2.20/plugins/python-build/bin/python-build`

- Look for the following line...

` $CONFIGURE_OPTS ${!PACKAGE_CONFIGURE_OPTS} "${!PACKAGE_CONFIGURE_OPTS_ARRAY}" || return 1 `

- ..and change it to:

` $CONFIGURE_OPTS --with-tcltk-includes='-I/usr/local/opt/tcl-tk/include' --with-tcltk-libs='-L/usr/local/opt/tcl-tk/lib -ltcl8.6 -ltk8.6' ${!PACKAGE_CONFIGURE_OPTS} "${!PACKAGE_CONFIGURE_OPTS_ARRAY}" || return 1 `

- Once this is done, we can now install python using pyenv `pyenv install 3.8.5` or any version you want.

---

### An alternative way of setting environment variables
 - Another way to set the environment variables with making it permanent  is to use the following lines below. installing the python version we want.
```
  env \
    PATH="$(brew --prefix tcl-tk)/bin:$PATH" \
    LDFLAGS="-L$(brew --prefix tcl-tk)/lib" \
    CPPFLAGS="-I$(brew --prefix tcl-tk)/include" \
    PKG_CONFIG_PATH="$(brew --prefix tcl-tk)/lib/pkgconfig" \
    CFLAGS="-I$(brew --prefix tcl-tk)/include" \
    PYTHON_CONFIGURE_OPTS="--with-tcltk-includes='-I$(brew --prefix tcl-tk)/include' --with-tcltk-libs='-L$(brew --prefix tcl-tk)/lib -ltcl8.6 -ltk8.6'" \

```
