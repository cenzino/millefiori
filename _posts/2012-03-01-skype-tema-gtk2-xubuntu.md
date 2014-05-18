---
layout: post
title: "Skype e il tema Gtk+ su Xubuntu"
description: ""
category: "Guida"
tags: [ubuntu, xubuntu, skype, gtk, ruby]
published: true
comments: true
---


Installando Skype su Xubuntu 11.10 si presenta il problema del tema Gtk+, infatti Skype non riesce a trovarlo e viene visualizzato con un tema di default. Bastano poche operazioni per risolvere il problema.


Aggiungere la seguente riga nel file `~/.gtkrc-2.0` (se non esiste, crearlo):

    gtk-theme-name="il nome del tuo tema"

Aggiungere la seguente riga nel file `~/.profile`:

    export GTK2_RC_FILES="$HOME/.gtkrc-2.0"

Ora sloggare e riloggare o riavviare per applicare le modifiche.
