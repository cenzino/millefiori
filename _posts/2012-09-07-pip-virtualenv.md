---
layout: post
title: "Installare e configurare Pip, Virtualenv e Virtualenvwrapper su linux)"
description: ""
category: "Guida"
tags: [ubuntu, ruby]
published: true
comments: true
---

Virtualenv è uno strumento indispensabile per chi programma in Python, permette di creare sulla stessa macchina ambienti di sviluppo diversi detti *sandbox*.

#Installazione

Per installare Virtualenv abbiamo bisogno di `pip`, se non è ancora presente:

```bash
$ sudo apt-get install python-setuptools
```

```bash
$ sudo easy_install pip
```

Ora possiamo installare Virtualenv:

```bash
$ sudo pip install virtualenv virtualwrapper
```

# Configurazione

Ultimo step, settiamo la cartella dove verranno create le sandbox, nel mio caso `~/progetti/venvs`, per farlo inseriamo queste righe nel nostro `~/.bashrc`.

```bash
# virtualenvwrapper
export WORKON_HOME=~/progetti/venvs
source /usr/local/bin/virtualenvwrapper.sh
export PIP_VIRTUALENV_BASE=$WORKON_HOME
export PIP_RESPECT_VIRTUALENV=true
```
Adesso creiamo la cartella e inizializziamo virtualenvwrapper

```bash
$ mkdir -p ~/progetti/vens
$ source ~/.bashrc
```

# Utilizzo

```bash
$ mkvirtualenv --no-site-packages myenv
(myenv) $ workon myenv
(myenv) $ cdvirtualenv
```

