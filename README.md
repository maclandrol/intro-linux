# Introduction à linux

Ceci est une introduction à quelques commandes de base de la console linux. Ce document aborde certaines commandes utiles pour un bioinformaticien débutant et peut également servir d'aide mémoire pour le future. Un effort a été fait pour ne mentionner que les options standard sur toutes les distributions linux. Si vous désirez contribuer à ce guide, cloner le répertoire sur github et proposer un pull-request.

## Liens utiles

Voici une liste de lien utiles pour un débutant

- [Guide exhaustive sur linux]()

- [Aide memoire linux]()


## Ouvrir un terminal

Pour ouvrir un terminal, vous pouvez utiliser le raccourci clavier **Ctrl+Alt+t** très commun, ou utiliser la barre de recherche de votre distribution pour cherche _terminal_ ou _console_ parmi les applications disponibles. En général, le terminal n'est pas très difficile à trouver.


## Commandes linux


Les commandes linux permettent l'exécution de programmes à partir d'un terminal. La forme générale d'une commande est :
 
```bash
nom_du_programme [options] arguments
```



## Manuel d'une commande 

Pour voir le manuel d'utilisation d'une commande, il faut utiliser la commande `man`. Dans l'exemple suivant, le manuel d'utilisation de la commande `cp` sera affiché. Beaucoup de programme n'ont pas de manuel d'utilisation. À la place, on utilise l'option soit `--help` soit `-h` fournie par la commande. Dans le pire des cas, faîtes une recherche internet. 

```bash
man cp
```

```bash
cp --help
```


## Navigateur web

Pour accéder au fureteur firefox: 

```bash
firefox &
```

ou encore

```bash
firefox nomDuSite &
``` 

(ex: `firefox www.google.ca &`)

L'éperluette (`&`) sert à faire rouler le programme tout en permettant de continuer à travailler dans le terminal. Vous pouvez essayer avec et sans afin de voir la différence.

Si vous n'utilisez pas le signe `&` à la fin d'une commande qui ouvre un programme, le terminal ne sera alors plus disponible pour écrire des commandes. Vous devrez alors ouvrir un nouveau terminal ou fermer le programme précedent.

Notez que vous pouvez tout simplement utiliser l'interface graphique pour **firefox**

## PDF
Pour ouvrir un fichier pdf à partir du terminal, utilisez `okular` ou `evince` 

```bash
evince nomDuFichier.pdf &
``` 

ou 

```bash
okular nomDuFichier.pdf &
``` 

## Se retrouver

Trouver sa position dans l'arborescence (pwd: **p**rint **w**orking **d**irectory). Cette commande affiche votre répertoire actuel. 
```sh
pwd
``` 
	
Lorsque vous ouvrez votre terminal, vous vous retrouver dans votre [`$HOME`](https://openclassrooms.com/courses/reprenez-le-controle-a-l-aide-de-linux/la-structure-des-dossiers-et-fichiers). Si vous changez de répertoire, `pwd` vous indiquera votre répertoire courant.

## Lister

Lister le contenu du répertoire courant.

```bash
ls 
```

**`ls`** accepte des paramètres supplémentaires et il est possible de les combiner. Exemple pour lister avec détails (`list : -l`), les fichiers cachés (`all : -a`) et en ordre chronologique (`reverse time : -rt`)

```bash
ls -l -a -rt
```

ou

```bash
ls -lart
```


## Créer un répertoire

Créer un répertoire (dossier) dans le répertoire courant (mkdir : make directory)

```bash
mkdir -p nomDuRépertoire
```

L'option `-p` est optionnelle et permet d'ignorer les erreurs, mais également de créér récursivement les répertoires parents s'ils n'existent pas.

## Changer de répertoire

Se déplacer du répertoire courant à celui indiqué (cd : **c**hange **d**irectory).

```bash
cd repertoireCible
```

Pour aller au répertoire parent :
```bash
cd ..
```

Et pour aller au répertoire parent du parent: 
```bash
cd ../..
```

Si vous entrez `cd` sans aucun arguments, le répertoire sera changé à votre `$HOME`. Il en est de même pour `cd ~/`, puisque '`~/`' est un raccourci pour désigner votre `$HOME`

Vous aurez à utiliser `ls` et `cd` conjointement pour lister le contenu d'un répertoire et en changer, la plus part du temps.

## Copier
Copier des fichiers d'un endroit à un autre

```bash
cp fichier_a_copier endroit_ou_le_copier
```

Copier des fichiers d'un autre endroit vers le répertoire courant. (Notez la présence du "." qui indique le répertoire courant).

```bash
cp fichier_a_copier .
```


## curl et wget
Télécharger le contenu d'un lien dans un fichier

```bash
curl http://example.com -o example.txt
```

```bash
wget -O example.txt https://example.com
```

Les options `-o` pour `curl` et `-O` pour `wget` permet respectivement de spécifier où sauvegarder le fichier téléchargé.

--------------------------------------------------------

Vous êtes prêts pour faire [le premier exercice](#exercice-1)


## tldr: un assistant aide mémoire.

Pour vous aider à vous rappeler des commandes linux à travers des examples pratiques, nous allons installer `tldr`. L'installation de programme sous linux requière souvent les permissions d'administrateur (commande `sudo`). Toutefois, dans certain cas, il est possible d'installer des programmes de façon locale, c'est-à-dire pour l'utilisateur courant uniquement. 

- Commençons par créer un répertoire local appelé `bin` dans notre `$HOME` pour sauvegarder le script à télécharger.

```bash
mkdir -p ~/bin
```

- Utilisons la commande `curl` pour télécharger le script et le sauvegarder dans le répertoire nouvellement créé.

```bash
curl -o ~/bin/tldr https://raw.githubusercontent.com/raylee/tldr/master/tldr
```

- Ajoutons maintenant les permissions pour rendre le script exécutable

```bash
chmod +rx ~/bin/tldr
```

- Et pour finir, nous devons ajouter le chemin vers le script dans notre [`$PATH`](https://www.commentcamarche.com/faq/3585-bash-la-variable-d-environnement-path#simili_main) pour pouvoir l'éxécuter de n'importe où !

```bash
printf '\nexport PATH=~/bin:$PATH' >> .bashrc && source .bashrc
``` 

- Essayer maintenant d'avoir un résumé de la commande tar avec :

```bash
tldr tar
```


## Essayer micro, l'éditeur de texte simple !

Vous aurez besoin très souvent d'utiliser un éditeur de texte, sans interface graphique. Par exemple si vous vous connectez à un serveur par `ssh` avec les paramètres par défaut. L'utilisation des éditeurs de base (**nano**, **vim**, **emacs**) peut être compliqué pour les débutants. À la placec, vous pouvez installer [micro](https://github.com/zyedidia/micro), une alternative très légère et facile à utiliser. Pour l'installer:

- Créer le dossier pour les programmes locaux (`~/bin`) s'il n'existe pas encore et déplacer vous à l'intérieur
```bash
mkdir -p ~/bin && cd ~/bin
```

- Télécharger le script de *micro*
```bash
curl https://getmic.ro | bash
```

- Un nouveau fichier appelé `micro` doit se trouver dans `~/bin`. Vous n'avez plus qu'à ajouter le chemin vers `~/bin` dans votre `$PATH` si ce n'est pas encore fait (Si vous avez suivi les instructions pour installer `tldr`, ignorer l'étape).

```bash
printf '\nexport PATH=~/bin:$PATH' >> .bashrc && source .bashrc
``` 

- Retourner dans votre `$HOME` et essayer d'ouvrir un nouveau fichier avec `micro` pour vérifier que tout fonctionne. La documentation de `micro` se trouve à [https://github.com/zyedidia/micro#documentation-and-help](https://github.com/zyedidia/micro#documentation-and-help).

```bash
cd 
micro nom_fichier
```


## Trucs et astuces à savoir

- Sous linux, les majuscules et les minuscules sont considérées comme deux caractères différents.
- Évitez les espaces dans les noms de fichiers/dossiers. À la place, utilisez l'underscore «**_**». Par exemple : `nom_de_fichier.txt` au lieu de `nom de fichier.txt`. L'espace fait parti des caractères spéciaux qu'on doit _échapper_ avec des backslash (`\`) où des guillemets (`""`). Par ailleurs, la plupart des commandes considèrent les arguments séparés par des espaces (sans échapement) comme des arguments différents. Par example, la commande `touch mon fichier `{:.language-bash} créera deux fichiers `mon` et `fichier`. Voilà une raison de plus pour éviter l'espace en général, quand on est débutant. 
- Le même raisonnement s'applique aux accents. Évitez les aussi !
- La touche Tab (pour tabulation) permet de compléter une commande ou le nom d'un fichier avec les options d'autocompletion mises en cache par le système. 
- Lorsque vous exécutez une commande, assurez-vous que celle-ci a bien fonctionné. Dans certains cas, un message d'erreur apparaîtra. Ce message donne les raisons potentielles expliquant l'erreur. Assurez vous de bien le lire. 
- Les flèches haut et bas permettent de naviguer parmi les dernières commandes lancées
- Avant de lancer toute commande, assurez vous que [l'invite de commande ou prompt](https://www.commentcamarche.com/contents/645-linux-le-shell#invite-de-commande-prompt) est présent (généralement '>' ou '$', mais peut varier en fonction de la configuration de la variable PS1). Dans le cas contraire, arrêtez le programme courrant, ou ouvrez un second terminal. 
- Notez que certains programmes bloquent le terminal et empêchent son utilisation. Pour éviter ça, vous devez exécuter le programme en arrière plan en ajoutant l'eperluette `&` à la fin de votre commande. La plupart des programmes continueront à écrire dans le terminal, mais vous pourriez libérer le prompt avec la **touche entrée** du clavier.
- Si vous voulez terminer un programme qui roule dans un terminal, vous pouvez utiliser la combinaison `ctrl+c`. Dans certains cas il faut faire `ctrl+d`. Plusieurs petits utilitaires Linux, comme par exemple la commande `less`, se quittent en utilisant tapant `q`. Il s'agit des trois façon standard pour quitter un programme sous linux.
- Vous pouvez obtenir de l'aide pour la plupart des programmes avec les options `--help` et/ou `-h`. Par exemple : ```ls --help``` affichera les options communes de la commande `ls`





# Exercices

## Exercice 1

Pour ce TP (et les suivants), vous devez travailler dans un répertoire réservé. 

- Commencez par créer un dossier appelé `TPLinux` et à l'intérieur un autre répertoire `test1` dans votre `$HOME`

<details><summary>Solution</summary>
<p>

```bash
mkdir -p ~/TPLinux/test1
```

</p>
</details>


- Aller dans le répertoire `test1` 

<details><summary>Solution</summary>
<p>
`test1` se trouve dans le répertoire `$HOME/TPLinux`. Pour y accéder il faut donc faire: 

```bash
cd ~/TPLinux/test1
```

Si vous vous trouvez déjà dans votre `$HOME`, vous pouvez utiliser `cd TPLinux/test1`. Essayer de taper juste une partie du chemin, puis appuyer sur la touche de tabulation pour voir l'autocomplètion qui vous sera proposée. 

</p>
</details>

S'assurer que l'on se retrouve dans le répertoire bcm2002 

Vérifier le contenu du dossier courant (il devrait être vide) 

Creer un dossier tp0 

Copiez y le fichier ~dbcm2002/A17/tp0/unknown.fasta. Le tilde (~) indique le 'home' du répertoire indiqué. Vérifiez le terminal après avoir exécuté la commande. Si celle-ci n'a pas fonctionné vous devriez voir un message d'erreur 

Il est important de s'assurer que le fichier a bien été copié. Pour ce faire, vérifiez le contenu du dossier tp0/ 

Vous pouvez en profiter pour créer des répertoires de travail pour les trois prochains TPs en même temps.


