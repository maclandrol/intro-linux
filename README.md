# Introduction à linux

Ceci est une introduction à quelques commandes de base de la console linux. Ce document aborde certaines commandes utiles pour un bioinformaticien et peut également servir d'aide mémoire pour le future. Si vous désirez contribuer à ce guide, cloner le répertoire sur github et proposer un pull-request.

## Liens utiles

Voici une liste de lien utiles pour un débutant

- [Guide exhaustive sur linux]()

- [Aide memoire linux]()


## Ouvrir un terminal

Pour ouvrir un terminal, vous pouvez utiliser le raccourci clavier **Ctrl+Alt+t** très commun, ou utiliser la barre de recherche de votre distribution pour cherche _terminal_ ou _console_ parmi les applications disponibles. En général, le terminal n'est pas très difficile à trouver.


## Commandes linux


Les commandes linux permettent l'exécution de programmes à partir d'un terminal. La forme générale d'une commande est :
 
```bash nom_du_programme [options] arguments```



## Manuel d'une commande 

Pour voir le manuel d'utilisation d'une commande, il faut utiliser la commande `man`. Dans l'exemple suivant, le manuel d'utilisation de la commande `cp` sera affiché. Beaucoup de programme n'ont pas de manuel d'utilisation. À la place, on utilise l'option soit `--help` soit `-h` fournie par la commande. Dans le pire des cas, faîtes une recherche internet. 

```bash man cp```
```bash cp --help```


## Navigateur web

Pour accéder au fureteur firefox: 

```bash firefox &```

ou encore

```bash firefox nomDuSite &``` (ex: ```bash firefox www.google.ca &```)

L'éperluette (`&`) sert à faire rouler le programme tout en permettant de continuer à travailler dans le terminal. Vous pouvez essayer avec et sans afin de voir la différence.

Si vous n'utilisez pas le signe `&` à la fin d'une commande qui ouvre un programme, le terminal ne sera alors plus disponible pour écrire des commandes. Vous devrez alors ouvrir un nouveau terminal ou fermer le programme précedent.

Notez que vous pouvez tout simplement utiliser l'interface graphique pour **firefox**

## Se retrouver

Trouver sa position dans l'arborescence. Cette commande affiche votre répertoire actuel. Lorsque vous ouvrez votre terminal, vous vous retrouver dans votre [`$HOME`](https://openclassrooms.com/courses/reprenez-le-controle-a-l-aide-de-linux/la-structure-des-dossiers-et-fichiers)

```bash pwd``` : **p**rint **w**orking **d**irectory




## Trucs et astuces à savoir

- Sous linux, les majuscules et les minuscules sont considérées comme deux caractères différents.
- Évitez les espaces dans les noms de fichiers/dossiers. À la place, utilisez l'underscore «**_**». Par exemple : `nom_de_fichier.txt` au lieu de `nom de fichier.txt`. L'espace fait parti des caractères spéciaux qu'on doit _échapper_ avec des backslash (`\`) où des guillemets (`""`). Par ailleurs, la plupart des commandes considèrent les arguments séparés par des espaces (sans échapement) comme des arguments différents. Par example, la commande ```bash touch mon fichier```créera deux fichiers `mon` et `fichier`. Voilà une raison de plus pour éviter l'espace en général, quand on est débutant. 
- Le même raisonnement s'applique aux accents. Évitez les aussi !
- La touche Tab (pour tabulation) permet de compléter une commande ou le nom d'un fichier avec les options d'autocompletion mises en cache par le système. 
- Lorsque vous exécutez une commande, assurez-vous que celle-ci a bien fonctionné. Dans certains cas, un message d'erreur apparaîtra. Ce message donne les raisons potentielles expliquant l'erreur. Assurez vous de bien le lire. 
- Les flèches haut et bas permettent de naviguer parmi les dernières commandes lancées
- Avant de lancer toute commande, assurez vous que [l'invite de commande ou prompt](https://www.commentcamarche.com/contents/645-linux-le-shell#invite-de-commande-prompt) est présent (généralement '>' ou '$', mais peut varier en fonction de la configuration de la variable PS1). Dans le cas contraire, arrêtez le programme courrant, ou ouvrez un second terminal. 
- Notez que certains programmes bloquent le terminal et empêchent son utilisation. Pour éviter ça, vous devez exécuter le programme en arrière plan en ajoutant l'eperluette `&` à la fin de votre commande. La plupart des programmes continueront à écrire dans le terminal, mais vous pourriez libérer le prompt avec la **touche entrée** du clavier.
- Si vous voulez terminer un programme qui roule dans un terminal, vous pouvez utiliser la combinaison `ctrl+c`. Dans certains cas il faut faire `ctrl+d`. Plusieurs petits utilitaires Linux, comme par exemple la commande `less`, se quittent en utilisant tapant `q`. Il s'agit des trois façon standard pour quitter un programme sous linux.
- Vous pouvez obtenir de l'aide pour la plupart des programmes avec les options `--help` et/ou `-h`. Par exemple : ```bash ls --help``` affichera les options communes de la commande ```bash ls```






<details><summary>CLICK ME</summary>
<p>

#### yes, even hidden code blocks!

```python
print("hello world!")
```

</p>
</details>