---
layout: post
title: "Installare Ruby su Ubuntu 12.10 (Quantal Quetzal)"
description: "Semplice guida all'installazione di Ruby su Ubuntu 12.10 (Quantal Quetzal)"
category: "Guida"
tags: [ubuntu, ruby]
published: true
comments: true
---

Per poter pubblicare questo sito ho dovuto installare e configurare Ruby sul mio Ubuntu 12.10 (Quantal Quetzal), la procedura è stata semplice e unveloce senza nessun intoppo. Riporto tutte le operazioni eseguite spernando possano essere utili a qualcuno che si è ritrovato con la stessa esigenza.

Iniziamo un update del sistema per avere la certezza che verranno installati tutti i software più recendi, quindi da terminale eseguiamo il comando:

```console
$ sudo apt-get update
```

Ora, possiamo installare la **RVM** (Ruby Version Manager). Questa applicazione permette di installare più versioni di Ruby sulla stessa macchina, in questo caso io l'ho utilizzata per installare l'ultima versione di Ruby.

Per poter installare RVM utilizziamo `curl`, se non è già presente nel sistema installiamo tramite il comando:

```console
$ sudo apt-get install curl
```

Installiamo RVM, sempre nel terminale eseguiamo il comando:

```console
$ \curl -L https://get.rvm.io | bash -s stable
```

Dopo l'installazione, carichiamo RVM. Potrebbe essere necessario chiudere il terminale e aprirne uno nuovo.

```console
$ source ~/.rvm/scripts/rvm
```

Per eseguire correttamente RMV dobbiamo installare le dipendenze. Digitiamo il seguente comando per otterene la lista delle librerie da installare:

```console
$ rvm requirements
```

Dovrebbe restituire una stringa di questo genere:

```console
Additional Dependencies:

# For ruby:
apt-get --no-install-recommends install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev libgdbm-dev ncurses-dev automake libtool bison subversion pkg-config libffi-dev
```

Quindi basta copiare e incollare il comando nel terminale e attendere il completamento.

In alcuni casi può generare un errore per la mancanza della libreria `zlib` per risolvere eseguire i comandi riportati in questo [guida](https://rvm.io/packages/zlib/).

In altri casi (com'è successo a me) il comando `rmv requirements` non genera la stringa su riportata, io seguendo il consiglio riportato nella stringa di risposta del comando, ho risolto esegendo:

```console
$ rvm autolibs enable
$ rvm requirements
```

Ora se tutto è andato a buon fine possiamo installare **Ruby**. Digitiamo nel terminale il comando:

```console
$ rvm install 1.9.3
```

Ora che Ruby è installato settiamo la versione di default:

```console
$ rvm use 1.9.3 --default
```

Installiamo **RubyGems** con il comando:

```console
$ rvm rubygems current
```

E infine installiamo **Rails**:

```console
$ gem install rails
```

Ora che tutto è installato e funzionante, aggiungiamo l'autocompletamento dei comandi rvm alla bash, per farlo basta inserire le seguenti righe nel proprio `~/.bashrc`:

```
PATH=$PATH:$HOME/.rvm/bin # Add RVM to PATH for scripting

[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

[[ -r $rvm_path/scripts/completion ]] && . $rvm_path/scripts/completion
```

Il risultato dovrebbe essere questo:

```console
$ rvm [TAB] 
debug            info             reload           system
default          install          remove           tests
fetch            list             reset            uninstall
gem              monitor          ruby             update
gemdir           notes            ruby-1.9.3-p392  use
gemset           package          snapshot         version
help             rake             specs            
implode          reinstall        srcdir 
$ rvm _
```

------------------------------

##### Riferimenti

https://www.digitalocean.com/community/articles/how-to-install-ruby-on-rails-on-ubuntu-12-04-lts-precise-pangolin-with-rvm

http://ryanbigg.com/2010/12/ubuntu-ruby-rvm-rails-and-you/


