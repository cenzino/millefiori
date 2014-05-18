---
layout: post
published: true
tags: 
  - Guide
  - Debian
  - Ubuntu
---

Installando Crunchbang 11 a causa di un bug dell'installer mi sono trovato costretto a dover selezionare l'inglese come lingua di sistema. Conclusa l'installazione ho provveduto a installare la lingua italiana, tutto risolto tranne **i nomi delle cartelle della Home che sono rimasti in inglese**.

Il problema è dovuto al file di configurazione di user-dirs.dirs il quale rimane ancora con i collegamenti in inglese evitando cosi di convertire le directory della home in italiano.

Per risolvere il problema per prima cosa verifichiamo che il file di configurazione sia davvero in inglese per farlo basta digitare:

```
$ nano  ~/.config/user-dirs.dirs
```

dovremo trovare le directory in lingua inglese.
Per poter avere le cartelle in italiano dovremo rigenerare il file user-dirs.dirs, la prima cosa da fare è rimuovere il file `user-dirs.dirs` digitando da terminale

```bash
$ rm ~/.config/user-dirs.dirs
```

a questo punto rigeneriamo il file user-dirs.dirs digitando:

```
$ xdg-user-dirs-update 
```

a questo punto riavviamo la nostra distribuzione.
Al riavvio troveremo cartelle sia in inglese che italiano, spostiamo il contenuto delle cartelle in inglese in quelle in italiano e poi eliminamo le prime.

La guida funziona anche con altre distruzioni Linux.
