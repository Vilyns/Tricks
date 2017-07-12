# Shell

![meme](http://s2.quickmeme.com/img/70/7082870877970b690afc771176729c75fc4a13e1fa3f0211f16cc691a64f6b40.jpg)

Le shell est massivement utilisée lors du j00 & j01, mais ce n'est pas pour autant qu'il faut l'oublier des le j02, 
c'est un amis precieux pour vous eviter le travail laborieur et devenit de vrait paresseux :innocent:

Par exemple pour les plus temeraires qui tenteront sastantua, cette commande peux vous être utile
```sh
./sastantua 5 | tr -d ' ' | awk "{ print length(\$0) - 2 }"
```
Avec ceci, on compte le nombre d'etoiles par etage

## Zsh

Le Z shell est le shell par default utilisé à 42 ou Le 101, la communauté autour de ce shell a developpé de nombreuses ressources dont il serait dommage de se priver

### [Oh my zsh](https://github.com/robbyrussell/oh-my-zsh)

Oh my Zsh est le framework de configuration le plus populaire pour zsh. IL ameliore l'experience utilisateur de zsh
Il ajoute notament:
- Une configuration avancée de zsh lui même
- Des themes
- Des fonctionnalité en extra & quelques raccourcis de commandes (comme `ll` par exemple)
- navigation dans les dossiers
- Integration avec certains services et programmes
- completion, aliases, et fonctions auxilières

#### Installation
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### [Prezto](https://github.com/sorin-ionescu/prezto)

Oh my Zsh est lent, prezto a donc été crée avec la rapidité comme but, il fournit casiment les mêmes fonctionnalités que oh my zsh.

#### Installation
```sh
git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
```

puis ajouter a la fin de votre ~/.zshrc

```
source "${ZDOTDIR:-$HOME}/.zprezto/init.zsh"
```

### [Zsh Syntax Highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

Ce plugin ajoute une coloration au commandes tapée dans zsh

Avant: ![1before](https://github.com/zsh-users/zsh-syntax-highlighting/raw/master/images/before1.png)
<br/>
Après: ![1after](https://github.com/zsh-users/zsh-syntax-highlighting/raw/master/images/after1.png)

Avant: ![2before](https://github.com/zsh-users/zsh-syntax-highlighting/raw/master/images/before2.png)
<br/>
Après:  ![2after](https://github.com/zsh-users/zsh-syntax-highlighting/raw/master/images/after2.png)

Avant: ![3before](https://github.com/zsh-users/zsh-syntax-highlighting/raw/master/images/before3.png)
<br/>
Après: ![3after](https://github.com/zsh-users/zsh-syntax-highlighting/raw/master/images/after3.png)

#### Installation
```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
    echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

## Alias

Les alias vous permentent de creer .... des alias, merci Jamy

Pro tip: Si jamais vous voulez qu'un alias soit persistant, n'oubliez pas de l'ajouter dans votre ~/.zshrc

## Alias utiles
### Pour les premiers jour
```
alias norminette="norminette -R CheckForbiddenSourceHeader"
```
Attention n'oubliez pas de l'enlever

### CCC, ...
```
alias ccc="gcc -Wall -Werror -Wextra"
