# Notes / Todo (CLI minimal)

Système de gestion ultra-simple de tâches et projets, pensé pour :
- un usage quotidien en CLI
- un environnement contraint (42)
- une charge mentale minimale
- une synchronisation fiable via Git

## Architecture

Ce repo contient uniquement des fichiers texte :

repo/notes/ \
├── todo.md        # Vue active (NOW / ROUTINE / AUTRES) \
├── backlog.md     # Mémoire / parking / projets futurs \
└── README.md


Un lien symbolique (`~/.notes`) pointe vers ce dossier afin que
les commandes fonctionnent de la même manière sur toutes les machines.
~/.notes -> ~/repo/notes

---
## Installation

### Prérequis
- Git
- Un shell compatible (zsh / bash)
- `vim` et `less` installés

---

### 1. Cloner le repo

```bash
cd ~/repo
git clone git@github.com:TON_USER/notes.git
```

### 2. Créer le lien symbolique

Le script utilise `~/.notes` comme point d’entrée unique.
```bash
rm -rf ~/.notes
ln -s ~/repo/notes ~/.notes
```

### 3. Installer le script todo

Créer un dossier personnel pour les scripts puis copier le script todo dans ce dossier:
``` bash
mkdir -p ~/bin
cp ~/repo/notes/todo ~/bin/todo
chmod +x ~/bin/todo
```

### 4. Ajouter ~/bin au PATH (si nécessaire)

Dans ~/.zshrc :
``` bash
export PATH="$HOME/bin:$PATH"
source ~/.zshrc
```

---

## Utilisation

``` bash
todo            # afficher la todo
todo -e         # éditer la todo
todo -b         # afficher le backlog
todo -be        # éditer le backlog
todo -p         # git pull
todo -P         # git push
todo -h         # aide
```

