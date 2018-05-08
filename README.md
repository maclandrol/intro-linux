# Introduction à linux

Ceci est une introduction à quelques commandes de base de la console linux. Ce document aborde certaines commandes utiles pour un bioinformaticien débutant et peut également servir d'aide mémoire pour le future. Un effort a été fait pour ne mentionner que les options standard sur toutes les distributions linux. Si vous désirez contribuer à ce guide, cloner le répertoire sur github et proposer un pull-request.

## Liens utiles

Voici une liste de lien utiles pour débutants:

- [Guide exhaustive sur linux](https://dl2.pushbulletusercontent.com/JeSzkGMMD2dMb9O7GnL3x2q7ouCszqTS/notesLinux.pdf)

- [Aide memoire linux](http://www.epons.org/commandes-base-linux.php)


## Ouvrir un terminal

Pour ouvrir un terminal, vous pouvez utiliser le raccourci clavier **Ctrl+Alt+t** très commun, ou utiliser la barre de recherche de votre distribution pour cherche _terminal_ ou _console_ parmi les applications disponibles. En général, le terminal n'est pas très difficile à trouver.


## Commandes linux

Les commandes linux permettent l'exécution de programmes à partir d'un terminal. La forme générale d'une commande est :
```bash
nom_du_programme [options] arguments
```

En générale, chaque ligne représente une commande différente. Il est toutefois possible d'éxécuter plusieurs commandes sur la même ligne en les séparant par un `;`. De même, on peut imposer que la première commande s'exécute sans erreurs avant que la seconde ne soit lancée en utilisant deux éperluettes `&&` à la place. Cette version est très pratique lorsqu'on désire éxécuter une série de commandes dont chacune dépends du bon fonctionnement du précédent.
```bash
# Affiche test2
cat 'xxtestxx'; echo 'test2'
```

La commande précédente essayera d'afficher le contenu d'un fichier appelé "_xxtestxx_" puis affichera le mot '_test2_'. Puisque le fichier "_xxtestxx_" n'existe pas, il y aura une erreur, mais '_test2_' sera quand même affiché.
```bash
# N'affiche pas test2
cat 'xxtestxx' && echo 'test2'
```

Dans ce second cas, '_test2_' ne sera pas affiché car la commande précédente retourne une erreur.

Notez que les lignes qui commencent par `#` sont des commentaires, et ne représentent donc aucune commande.

## Manuel d'une commande 
Pour voir le manuel d'utilisation d'une commande, il faut utiliser la commande `man`. Dans l'exemple suivant, le manuel d'utilisation de la commande `cp` sera affiché. Beaucoup de programme n'ont pas de manuel d'utilisation. À la place, on utilise l'option soit `--help` soit `-h` fournie par la commande. Dans le pire des cas, faîtes une recherche internet. 

```bash
man cp
cp --help
```

## Navigateur web

Pour accéder au fureteur firefox: 
```bash
firefox &
# ou encore
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
# ou 
okular nomDuFichier.pdf &
``` 


## Éditeur de texte

Afin de pouvoir ouvrir et composer des fichiers textes, vous pouvez utiliser un éditeur de texte comme `kate`. Vous avez en principe, le choix entre `kate`, `gedit`, `vim`, `emacs` et `nano` comme éditeurs par défaut sous linux. Vim et Emacs sont des outils très puissant et un peu trop avancés pour une introduction à linux. Nous essayerons donc l'éditeur graphique `kate`
```bash
kate & 
# ou encore 
kate nomDuFichier &
``` 

Dans le second cas, Kate ouvre le fichier _nomDuFichier_ ou crée un nouveau fichier nommé _nomDuFichier_ si ce dernier n'existe pas encore.


## Commandes de bases
### Se retrouver

Trouver sa position dans l'arborescence avec **pwd**: **p**rint **w**orking **d**irectory. Cette commande affiche votre répertoire actuel. 
```bash
pwd
``` 
    
Lorsque vous ouvrez votre terminal, vous vous retrouver dans votre [`$HOME`](https://openclassrooms.com/courses/reprenez-le-controle-a-l-aide-de-linux/la-structure-des-dossiers-et-fichiers). Si vous changez de répertoire, `pwd` vous indiquera votre répertoire courant.

### Lister

Lister le contenu du répertoire courant avec la commande **ls** : **l**i**s**t
```bash
ls 
```

**`ls`** accepte des paramètres supplémentaires et il est possible de les combiner. Exemple pour lister avec détails (`list : -l`), les fichiers cachés (`all : -a`) et en ordre chronologique (`reverse time : -rt`)
```bash
ls -l -a -rt
# ou 
ls -lart
```


### Créer un répertoire

Créer un répertoire (dossier) avec **mkdir** : **m**a**k**e **dir**ectory
```bash
mkdir -p nomDuRépertoire
```

L'option `-p` est optionnelle et permet d'ignorer les erreurs, mais également de créér récursivement les répertoires parents s'ils n'existent pas.

### Changer de répertoire

Se déplacer du répertoire courant à celui indiqué avec **cd** : **c**hange **d**irectory.
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


### Copier

Copier des fichiers d'un endroit à un autre avec **cp** : **c**o**p**y
```bash
cp fichier_a_copier endroit_ou_le_copier
```

Copier des fichiers d'un autre endroit vers le répertoire courant. (Notez la présence du "." qui indique le répertoire courant).
```bash
cp fichier_a_copier .
```


### Déplacer

Bouger un fichier ou répertoire d'un endroit à un autre avec *mv* : **m**o**v**e.
```bash
mv fichiers_a_bouger endroit_ou_les_bouger
```

Cette commande est également utile pour renommer ou écraser un fichier ou un répertoire.

<strong> <span style="color: red">ATTENTION, écraser un fichier est irréversible ! Faites donc très attention !</span></strong>


### Supprimer

Supprimer des fichiers avec **rm** : **r**e**m**ove
```bash
rm -i fichier1 ... fichierN
```

Il vous faudra confirmer la supression en appuyant sur le caractère indiqué puis sur la touche _entré_. Il est aussi possible de supprimer un répertoire. Celui-ci doit être vide. (rmdir : remove directory )
```bash
rm -i repertoireVide
```

Si l'on veut supprimer un répertoire ainsi que tout son contenu. L'option `r` signifie récursivement.
```bash
rm -ir repertoire
```

<strong> <span style="color: red">ATTENTION, la suppression d'un fichier est irréversible ! Faites donc très attention !</span></strong>


### Télécharger un fichier

Télécharger le contenu d'un lien dans un fichier avec `curl` ou `wget`
```bash
curl http://example.com -o example.txt
wget -O example.txt https://example.com
```

Les options `-o` pour `curl` et `-O` pour `wget` permet respectivement de spécifier où sauvegarder le fichier téléchargé.


### Visualiser le contenu d'un fichier

Les commandes `head/tail` permettent d'afficher les lignes de début et fin d'un fichier. Ainsi pour afficher les 20 premières lignes d'un fichier:
```bash
head -n 20 nomDuFichier
```

Voir les 30 dernières lignes d'un fichier
```bash
tail -n 30 nomDuFichier
```

Vous pouvez afficher le contenu d'un fichier dans le terminal avec `less` ou `more`
```bash
less nomDuFichier
more nomDuFichier
```

Pour less et more, utilisez les flèches du clavier pour faire défiler le contenu du fichier. Remarquez le nombre de lignes composant le fichier au bas du terminal.

Si vous lancer less comme suit : `less -N nomDuFichier`, le numéro de chaque ligne sera affiché. Appuyez sur la touche "q" pour quitter la lecture.

Il existe une autre commande pour afficher le contenu d'un fichier dans le terminal. Il s'agit de la commande `cat`. Contrairement à `less`, cat affiche tout le contenu du fichier d'un coup. Il s'agit donc d'un mauvais choix pour les connaître le contenu des fichiers lourds. Mais cette commande a bien d'autres utilités que nous verrons un peu plus tard.
```bash
cat nomDuFichier
```

### Chercher un fichier
Effectue une recherche dans le répertoire spécifié ainsi que ses sous-répertoires. Attention, la recherche est sensible à la casse! Utilisez -iname à la place de -name pour ne pas tenir compte de la casse (minuscule vs majuscule).
```bash
find endroitAChercher -name 'nomATrouver'
```

Pour trouver tous les documents pdf du répertoire courant ainsi que ses sous-répertoires. 
```bash
find . -name '*.pdf'
```

L'astérisque (\*) est un caractère spécial qui indique qu'il faut considérer n'importe quelle quantité de caractères précédent ".txt".

-------------------------------------------
Vous êtes maintenant prêts pour faire [les exercices 1](#exercice-1)  et [2](#exercice-2)! Mais avant, lisez la section suivante et suivez les instructions pour installer deux petits utilitaires qui rendront votre expérience linux plus agréable. 


## Utilitaires pratiques
Nous allons nous équiper de deux outils très utiles pour les débutants. Il nous faudra les installer et pour ce faire, vous n'avez qu'à suivre les commandes. En règle générale, lorsqu'il s'agit d'espace partagé de travail, demandez plutôt à votre administrateur système de vous installer les logiciels ou confirmer avec lui avant.

### tldr: un aide mémoire.

Pour vous aider à vous rappeler des commandes linux à travers des exemples pratiques, nous allons installer `tldr`. L'installation de programme sous linux requiert souvent les permissions d'administrateurs (commande `sudo`). Toutefois, dans certains cas, il est possible d'installer des programmes de façon locale, c'est-à-dire pour l'utilisateur courant uniquement. 

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

- Essayez maintenant d'avoir un résumé de la commande `cp` avec :
```bash
tldr cp
```

- Essayez les autres commandes que nous avons vues.

### micro, l'éditeur de texte simple !

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

-------------------------------------------

## Commandes avancées

Vous pouvez utiliser `tldr` avec les commandes ci-après pour avoir leur résumés avec des exemples pratiques

### Recherche de caractères

La commande UNIX **grep** (**g**lobal search for **r**egular **e**xpression and **p**rint) permet de chercher différents motifs dans un fichier. Grep imprime les lignes du fichiers contenant le motif.
```bash
grep motif Fichier
```

Vous pouvez utiliser des <a href="https://web.archive.org/web/20171005075328/https://www.digitalocean.com/community/tutorials/using-grep-regular-expressions-to-search-for-text-patterns-in-linux">expressions régulières avec grep</a>. Notez qu'il existe plusieurs types de regexp et qu'il faut parfois le <b> specifier </b> avec les options `-E, -G, -P`. Voici quelques opérateurs regexp de base :</p>
<table class="table table-hover">
<thead>
<tr>
  <th>Méta-caractère</th>
  <th>Correspondance</th>
</tr>
</thead>
<tbody>
<tr>
  <td><code>^</code></td>
  <td>La correspondance commence la chaîne recherchée (juste avant le premier char du mot)</td>

</tr>
<tr>
  <td><code>$</code></td>
  <td>La correspondance fini la chaîne recherchée (juste après le dernier char du mot)</td>

</tr>
<tr>
  <td><code>.</code></td>
  <td>n'importe quel caractère unique</td>
</tr>
   <tr>
  <td>\*</td>
  <td>répétition du caractère précédent, 0 ou plusieurs fois</td>
</tr>
<tr>
  <td><code>[ ]</code></td>
  <td>n'importe lequel des caractères cités entre les crochets</td>
  </tr>
<tr>
  <td><code>[^ ]</code></td>
  <td>n'importe quels caractères sauf ceux présents entre les crochets</td>
  </tr>
<tr>
  <td><code>\</code></td>
  <td>escape le caractère qui suit (pour ne pas qu'il soit considéré special: <span class="underline">ex</span> : `\*`)</td>
</tr>

<tr>
  <td><code>\t</code></td>
  <td>Correspond à une tabulation</td>
</tr>

<tr>
  <td><code>\n</code></td>
  <td>Correspond à un saut à la ligne</td>
</tr>

<tr>
<td><code>\s</code></td>
  <td>Correspond à un espace blanc (\t, \n, " ")</td>
</tr>
</tbody>
</table>

La commande suivante affichera toutes les lignes du fichier _fichier.txt_ finissant par une voyelle suivie d'un "." (point). Notez le `\` qui permet d'escaper le caractère `.`
```bash
grep "[aeiouy]\.$" fichier.txt
```

L'option `-i` permet d'ignorer la casse et l'option `-v` permet d'afficher les résultats qui ne _matchent_ pas.
```bash
grep -i -v motif fichier
```

L'option -o permet d'afficher indépendamment chaque _match_ sur une ligne.
```bash
grep -o motif fichier
```


### Récupérer des colonnes

La commande **cut** permet de récupérer des colonnes d'un fichier. Elle est très utile lorsque le fichier est organisé en colonnes distinctes (pas exemple un fichier csv). On peut également spécifier un séparateur de champs avec l'option `-d`:
```bash
cut [-d<separateur>] −f<colonnes> nomDuFichier
```
où `<Colonnes>` désigne un intervalle ou une liste de colonne (par exemple: 1-3 ou 1,5,6).

### Compter le nombre de lignes d'un fichier
Compter le nombre de ligne dans un fichier se fait avec wc: **w**ord **c**ount.
```bash
wc -l nomDuFichier
```

wc permet également de compter le nombre de mot dans un fichier !
```bash
wc -w nomDuFichier
```

### Transformation

Substituer des caractères dans un fichier ou un flux de données par d'autres avec **tr**.

Pour remplacer les minuscules par les majuscules.
```bash
tr '[a-z]' '[A-Z]'' < fichier
```
Notez la syntaxe particulière en ce qui concerne le fichier en entrée. 

Pour Remplacer "a" par "d", "b" par "e" et "c" par "f"
```bash
tr '[abc]' '[def]' < fichier 
```

Remplacer _n_ occurences contiguës du même caractère par une seule occurence. Par exemple pour remplace tous les suites de 'c' par un seul unique caractère 'c':
```bash
tr -s 'c' < fichier
```

Supprimer toutes les occurences d'un caractère. Pour supprimer toutes les occurences de 'c':
```bash
tr -d 'c' < fichier
```

### Manipulation de texte avec sed

Sed est une utilitaire Unix très puissant qui permet de manipuler du texte. Comme grep nous pouvons également utiliser des regexps comme motifs. Nous n'explorerons toutefois que 2 commandes sed.

Extraction de lignes précises d'un fichier
```bash
sed -n "ligne_de_départ,ligne_de_finp;ligne_de_fin+1q" fichier
```

Par exemple `sed -n "2,10p;11q" nomDuFichier` extrait et affiche les lignes 2 à 10 inclusivement.

Si vous souhaitez substituer un motif par un autre:
```bash
sed -e s/ancien_motif1/nouveau_motif1/g -e s/ancien_motif2/nouveau_motif2/g [...] nomDuFichier
```

Vous pouvez modifier des fichiers sur place avec sed en utilisant l'option `-i` . 
<strong> <span style="color: red">Noter que l'action est irréversible donc à éviter si vous n'êtes pas sûr !</span></strong>
```bash
sed -i [...] nomDuFichier
```

-----------------------------------

## Pipe et redirection

Il est possible de rediriger l'output d'une commande dans un fichier avec l'option `>`. Cette option écrase le contenu du fichier. À la place nous pouvons rajouter les nouvelles lignes à la fin du fichier avec `>>`

```bash
echo "ligne1" > fichier1
# le fichier 1 contient "ligne1"
echo "ligne2" > fichier1
# le fichier 1 contient uniquement "ligne2" maintenant. 
```
Dans l'exemple précédent, si on avait utilisé `echo "ligne2" >> fichier1` alors fichier1 contiendrait les deux lignes. 

À la place de sauvegarder l'output d'une commande dans un fichier, nous pouvons directement la passer comme input pour la commande suivante avec le pipe: `|`

```bash
echo "uneeee faute de frappe" | tr -s 'e'
```

Dans cet exemple, la commande `echo` affichera **uneeee faute de frappe** seule, mais grâce à `tr` nous pouvons remplacer toutes les lettres `e` contiguës par une seule. Ce qui affichera donc **une faute de frappe**.

`>`, `>>`, `&&`,  `|` peuvent être utilisé ensemble pour enchaîner plusieurs petites commandes et produire des résultats étonnants. 

```bash
echo "unee ligne à corriger." | sed -e 's/unee/Une/g' > test1.txt &&  echo 'Une nouvelle ligne.' >> test1.txt
```


--------------------------------------


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

Pour cet exercice (et les suivants), vous devez travailler dans un répertoire réservé. 
<ol class="exo">
<li>Commencez par créer un dossier appelé <code>TPLinux</code> et à l'intérieur un autre répertoire <code>test1</code> dans votre <code>$HOME</code>

<details><summary><code><span style="color: #EEEE22">Solution 1</span></code></summary>

<pre><code>mkdir -p ~/TPLinux/test1
</code></pre>
</details>
</li>

<li>Aller dans le répertoire <code>test1</code>
<details><summary><code><span style="color: #EEEE22">Solution 2</span></code></summary>

<code>test1</code> se trouve dans le répertoire <code>$HOME/TPLinux</code>. Pour y accéder il faut donc faire: 

<pre><code>cd ~/TPLinux/test1
</code></pre>

Si vous vous trouvez déjà dans votre <code>$HOME</code>, vous pouvez utiliser <code>cd TPLinux/test1</code>. Essayer de taper juste une partie du chemin, puis appuyer sur la touche de tabulation pour voir l'autocomplètion qui vous sera proposée. 
</details>
</li>

<li>Comment pouvez vous assurez que vous êtes dans le bon répertoire ? 

<details><summary><code><span style="color: #EEEE22">Solution 3</span></code></summary>

<pre><code>pwd
</code></pre>
</details>
</li>

<li>Vérifier le contenu du dossier courant (<code>test1</code>), il devrait être vide.

<details><summary><code><span style="color: #EEEE22">Solution 4</span></code></summary>

<pre><code>ls
</code></pre>
</details>
</li>

<li>Télécharger l'archive qui contient les données pour l'exercice sur <code>https://raw.githubusercontent.com/maclandrol/intro-linux/master/data.zip</code>. Essayer d'utiliser les lignes de commande pour le faire. Si vous n'êtes pas sûr de la commande complète, mais connaissez le programme à utiliser, essayer son help/manuel ou plus simplement <code>tldr commande</code>. Vérifier ensuite le contenu de votre répertoire actuel. 

<details><summary><code><span style="color: #EEEE22">Solution 5</span></code></summary>

<pre><code>wget https://raw.githubusercontent.com/maclandrol/intro-linux/master/data.zip
ls
</code></pre>
Dans ce cas, nous n'avons pas besoin de spécifier un fichier output. Vous remarquerez avec que <code>ls</code> retourne un nouveau fichier <code>data.zip</code>.
</details>
</li>

<li>Décompressez l'archive. Sachant qu'il faudrait utiliser la commande <code>unzip</code>, trouvez la ligne complète qu'il faut entrer. Vérifier ensuite le contenu de l'archive
    
<details><summary><code><span style="color: #EEEE22">Solution 6</span></code></summary>

Pour avoir un exemple du fonctionnement de <code>unzip</code>

<pre><code>tldr unzip
</code></pre>
Il suffit donc de faire :

<pre><code>unzip data.zip
ls
# doit indiquer la présence d'un nouveau dossier 'data'
ls data/
# affiche le contenu de data
</code></pre>

Si vous êtes dans un dossier qui ne contient pas <code>data.zip</code>, utilser le chemin vers <code>data.zip</code> à la place.
</details>
</li>
<li>Afin d'organiser notre répertoire, déplacez le nouvellement créé et qui contient les fichiers décompressés dans le répetoire parent <code>TPLinux</code>. Supprimez l'archive `.zip` puis retournez dans votre <code>$HOME</code>
    
<details><summary><code><span style="color: #EEEE22">Solution 7</span></code></summary>

<pre><code>mv data ..
rm -i data.zip
cd
</code></pre>
</details>
</li>

<li>Parmi les fichiers téléchargés, il y a un fichier <code>pdf</code> mal nommé. Trouvez le, puis renommer le __notesLinux.pdf__ en le maintenant dans le même répertoire. Ouvrez ensuite le fichier <code>pdf</code>.
    
<details><summary><code><span style="color: #EEEE22">Solution 8</span></code></summary>

<pre><code>find . -name '*.pdf'
mv ./TPLinux/data/xxxlinxx.pdf ./TPLinux/data/notesLinux.pdf
# ouvrir un fichier pdf 
okular ./TPLinux/data/notesLinux.pdf 
</code></pre>
</details>
</li>
</ol>

## Exercice 2
<ol>
<li>Parmi les fichiers téléchargés, se trouvent également des séquences avec une extension <code>fasta</code>. Combien de fichiers avec cette extension il y a t'il ?
    
<details><summary><code><span style="color: #EEEE22">Solution 1</span></code></summary>

<pre><code>find ~/TPLinux -name '*.fasta' | wc -l
# find retourne une ligne par fichier trouvé
# et wc permet de compter le nombre de lignes
# Alternativement
ls -1 ~/TPLinux/data/*fasta| wc -l
</code></pre>
</details>
</li>
</ol>



