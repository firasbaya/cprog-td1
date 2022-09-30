# Compléments de programmation - TD 1

## Remarques préliminaires
* Pour l'ensemble des TDs, vous créerez un compte individuel sur [github](https://github.com/) si vous n'en possédez pas déjà un.
Vous nommerez ce compte de la façon suivante: `uvsq<MonNuméroÉtudiant>`.
Par exemple, pour un étudiant de numéro *21601234*, le compte sera `uvsq21601234`.
* Les commandes `git` sont à taper en ligne de commande dans un *shell*.
* Vous pouvez utiliser l'IDE de votre choix.
Sur le cartable numérique, [Eclipse](www.eclipse.org), [IntelliJ IDEA](http://www.jetbrains.com/idea/) et [Visual Studio Code](https://code.visualstudio.com/) sont installés.
* Vous répondrez aux questions directement dans ce fichier en complétant les emplacements correspondants.
Ajoutez ensuite ce fichier au dépôt `git`.

## Partie I (à faire durant le TD) : découverte de `git`
Dans cet exercice, vous créerez une classe `Fraction` représentant un nombre rationnel et une classe `Main` qui testera les méthodes de la classe `Fraction` **avec des assertions** (cf. [Utilisation d'assertions](https://koor.fr/Java/Tutorial/java_assert.wp)).
À chaque étape, consultez le statut des fichiers du projet (`git status`) ainsi que l'historique (`git log`).

1. Sur la forge, créez le dépôt (_repository_) `SimpleFraction`;
En terme de *commits*, quelle différence constatez-vous entre cocher une (ou plusieurs) des cases *Initialize this repository with* et n'en cocher aucune ?
    > Répondre ici

    *Pour la suite, ne cochez aucune de ces cases*.
1. Localement, configurez `git` avec votre nom (`user.name`) et votre email (`user.email`) (cf. [Personnalisation de Git](https://git-scm.com/book/fr/v2/Personnalisation-de-Git-Configuration-de-Git));
    ```bash
     $ git config --global user.name "firasbaya"
    $ git config --global user.email firasbaya@hotmail.com

    ```
1. Initialisez le dépôt `git` local pour le projet (cf. [Démarrer un dépôt Git](https://git-scm.com/book/fr/v2/Les-bases-de-Git-D%C3%A9marrer-un-d%C3%A9p%C3%B4t-Git));
    ```bash
     
    $ git init
    $ git add *.c
    $ git add LICENSE
    $ git commit -m 'initial project version'
    ```
1. Dans votre IDE, créez la classe `Fraction` (vide pour le moment) et la classe `Main` (avec un simple affichage) dans le projet (cf. [Méthode `main`](https://docs.oracle.com/javase/specs/jls/se19/html/jls-12.html#jls-12.1.4));
Vérifiez que le projet compile et s'exécute dans l'IDE;
Validez les changements (cf. [Enregistrer des modifications dans le dépôt](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Enregistrer-des-modifications-dans-le-d%C3%A9p%C3%B4t));
    ```bash
    $ git commit
    ```
1. Ajoutez la méthode `toString` à la classe `Fraction` (cf. [`Object.toString`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Object.html#toString())) qui retournera la chaîne `"Je suis une fraction."` et modifiez la classe `Main` en conséquence;
Validez les changements;
    ```Java
  
    Classe Fraction:
    	public String toString() {
		return "je suis une fraction";
	}
    Main:
    Fraction f =new Fraction();
	f.toString();
	
    ```
1. Publiez vos modifications sur le dépôt distant (cf. [Travailler avec des dépôts distants](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Travailler-avec-des-d%C3%A9p%C3%B4ts-distants));
Vous utiliserez le protocole `https` pour cela;
Vérifiez avec le navigateur;
    ```bash
    # git remote add firastd1 https://github.com/firasbaya/mon-premier-td
    ```
1. Sur la forge, ajoutez un fichier de documentation `README.md`.
Quelle syntaxe est utilisée pour ce fichier ?
    > git add README.md && git commit -m "added readme" README.md.
1. Récupérez localement les modifications effectuées sur la forge.
    ```bash
    # git pull 
    ```
1. Ajoutez les répertoires et fichiers issus de la compilation aux fichiers ignorés par `git` (cf. [`.gitignore` pour Java](https://github.com/github/gitignore/blob/main/Java.gitignore));
    ```bash
     /.metadata/

    ```
1. Retirez les fichiers de configuration de l'IDE du projet;
    ```bash
    # Répondre ici
    ```
    Ajoutez-les aux fichiers ignorés par `git`.
    ```bash
    # Copier ici les modifications de `.gitignore`
    ```
1. Configurez l'accès par clé publique/clé privée à la forge (cf. [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)).
    1-On vérifie s'il ya déjà une clé ssh, aprés on génere une nouvelle clé ssh et on l'ajoute à notre machine ssh agent,aprés on execute la commande :clip < ~/.ssh/id_ed25519.pub dans notre cli et on ajoute la clé dans la partie access,SSH Keys dans settings 

## Partie II (à faire durant le TD) : compléter la classe `Fraction`
Dans cet partie, vous compléterez les classes `Fraction` et `Main`.
Un exemple d'interface pour une telle classe est donné par la classe http://commons.apache.org/proper/commons-math/javadocs/api-3.6.1/org/apache/commons/math3/fraction/Fraction.html[`Fraction`] de la bibliothèque http://commons.apache.org/math/[Apache Commons Math].

Vous respecterez les consignes ci-dessous :
* chaque méthode de `Fraction` sera testée dans `Main` **avec des assertions** (cf. [Utilisation d'assertions](https://koor.fr/Java/Tutorial/java_assert.wp));
* à la fin de chaque question, consultez le statut des fichiers du projet (`git status`) ainsi que l'historique (`git log`) puis validez les changements.

1. Ajoutez les attributs représentants le numérateur et le dénominateur (nombres entiers).
    ```Java
   public int a;
   public int b;
    ```
1. Ajoutez les constructeurs (cf. [Constructor Declarations](https://docs.oracle.com/javase/specs/jls/se19/html/jls-8.html#jls-8.8)) suivants :
    * initialisation avec un numérateur et un dénominateur,
    * initialisation avec juste le numérateur (dénominateur égal à _1_),
    * initialisation sans argument (numérateur égal _0_ et dénominateur égal à _1_),
    ```Java
    // Assertions pour tester les constructeurs (avec toString)
    ```
1. Ajoutez les fractions constantes ZERO (0, 1) et UN (1, 1) (cf. [Constants in Java](https://www.baeldung.com/java-constants-good-practices)),
    ```Java
  	 public static final Fraction zero = new Fraction(1,1);
	public static final Fraction un = new Fraction(0,1);
    ```
1. Ajoutez une méthode de consultation du numérateur et du dénominateur (par convention, en Java, une méthode retournant la valeur de l'attribut `anAttribute` est nommée `getAnAttribute`),
    ```Java
    	public int getNumérateur() {
		return numérateur;
	}
		public int getDéumérateur() {
		return dénumérateur;
	}


    ```
1. Ajoutez une méthode de consultation de la valeur sous la forme d'un nombre en virgule flottante (méthode `doubleValue()`) (cf. [`java.lang.Number`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Number.html)),
   ```Java
    // Assertions pour tester la conversion
    ```
1. Ajoutez une méthode permettant l'addition de deux fractions (la méthode `add` prend en paramètre *une* fraction et *retourne* la somme de la fraction courante et du paramètre),
   ```Java
    // Assertions pour tester l'addition
    ```
1. Ajoutez le test d'égalité entre fractions (deux fractions sont égales si elles représentent la même fraction réduite) (cf. [`java.lang.Object.equals`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Object.html#equals(java.lang.Object))),
   ```Java
    // Assertions pour tester l'égalité
    ```
1. Ajoutez la comparaison de fractions selon l'ordre naturel (cf. [`java.lang.Comparable`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Comparable.html)).
   ```Java
    // Assertions pour tester la comparaison
    ```
1. Faites hériter votre classe `Fraction` de la classe [`java.lang.Number`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Number.html) et complétez les méthodes
   ```Java
    // Vérifiez avec le code ci-dessous
    Number aNumber = java.math.BigDecimal.ONE;
    Number anotherNumber = new Fraction(0, 2);
    assert java.lang.Math.abs(aNumber.doubleValue() + anotherNumber.doubleValue() - 1.5) < 1E-8;
    ```

## Partie III (à faire à la maison) : révisions et perfectionnement *shell* et *IDE*
### Maîtriser le *shell* de commandes
L'objectif de cet exercice est de vous faire réviser/découvrir les commandes de base du *shell* de votre machine.
Vous pouvez répondre en utilisant le shell de votre choix (*bash*, *Powershell*, …).
Pour répondre à ces questions, vous devez effectuer les recherches documentaires adéquates (livre, web, …).

1. Quel OS et quel shell de commande utilisez-vous ?
    > Windows,git bash
1. Quelle commande permet d'obtenir de l'aide ?
Donnez un exemple.
    ```bash
   git help
    ```
1. Donnez la ou les commandes shell permettant de
    1. afficher les fichiers d'un répertoire triés par taille (taille affichée lisiblement)
        ```bash
        ls -lsha
        ```
    1. compter le nombre de ligne d'un fichier
        ```bash
      	wc -l fichier
        ```
    1. afficher les lignes du fichier `Main.java` contenant la chaîne `uneVariable`
        ```bash
        #grep "uneVariable" Main.java
        ```
    1. afficher récursivement les fichiers `.java` contenant la chaîne `uneVariable`
        ```bash
       grep -r "uneVariable" Main.java
        ```
    1. trouver les fichiers (pas les répertoires) nommés `README.md` dans une arborescence de répertoires
        ```bash
        find / -name README.md
        ```
    1. afficher les différences entre deux fichiers textes
        ```bash
       diff file1 file2

        ```
1. Expliquez en une ou deux phrases le rôle de ces commandes et dans quel contexte elles peuvent être utiles pour un développeur.
    * `ssh`
        >Fournit une connexion cryptée sécurisée entre deux hôtes sur un réseau non sécurisé
    * `screen`/`tmux`
        > tmux:est un multiplexeur de terminaux, outil permettant d'exploiter plusieurs terminaux au sein d'un 	         seul et même affichage
        > screen:permettant d'ouvrir plusieurs terminaux dans une même console, de passer de l'un à l'autre et 		de les récupérer plus tard.
    * `curl`/[HTTPie](https://httpie.org/)
        > Permet de tester des API.
    * [jq](https://stedolan.github.io/jq/)
        > jq peut modifier le format de données que vous avez dans celui que vous voulez avec très peu d'effort

### Découverte de votre *IDE*
Dans cet exercice, vous expliquerez en quelques phrases comment vous réalisez les actions ci-dessous dans votre IDE.
Vous pouvez choisir l'IDE/éditeur de texte de votre choix.
Pour réaliser cette exercice, vous devez bien évidemment vous reporter à la documentations de l'IDE ([IntelliJ IDEA](https://www.jetbrains.com/help/idea/discover-intellij-idea.html#developer-tools), [Visual Studio Code](https://code.visualstudio.com/docs), [Eclipse](https://help.eclipse.org/2020-09/index.jsp), …).

1. Quels IDE ou éditeurs de texte utilisez-vous pour le développement Java ?
    > Eclipse

    Pour la suite, ne considérez que l'un de vos choix.
1. Comment vérifier/définir que l'encodage utilisé est *UTF-8* ?
    > Window -> Preferences -> General -> Workspace : Text file encoding
1. Comment choisir le JDK à utiliser dans un projet ?
    > Java > Compiler", et dans "Compiler compliance level" selectionnez le JDK voulu
1. Comment préciser la version Java des sources dans un projet ?
    > Répondre ici
1. Comment ajouter une bibliothèque externe dans un projet ?
    >Sélectionnez votre projet dans l'explorateur de paquetages (Package Explorer).
	Sélectionnez l'entrée Properties du menu Project.
	Dans la boîte de dialogue qui s'ouvre, sélectionnez l'entrée Java Build Path.
	Activez l'onglet Libraries et cliquez sur Add External JARs…. Dans la boîte de dialogue qui s'ouvre, 	     choisissez le fichier JAR que vous désirez utiliser, puis cliquez sur Ok.
1. Comment reformater un fichier source Java ?
    > Répondre ici
1. Comment trouver la déclaration d'une variable ou méthode ?
    > Répondre ici
1. Comment insérer un bloc de code prédéfini (*snippet*) ?
    > Ctrl + Shift + C ou Ctrl + Shift + / pour mettre en commentaire.
1. Comment renommer une classe dans l'ensemble du projet ?
    > click droit sur la classe
    > refractor
    > rename
1. Comment exécuter le programme en lui passant un paramètre en ligne de commande ?
    > Configurations… du menu Run. La fenêtre qui s'ouvre alors liste sur la gauche la totalité des configurations d'exécution existantes, tandis que les paramètres de la configuration sélectionnée apparaissent à droite de cette liste. Ces paramètres sont répartis sur plusieurs onglets, le seul qui nous intéressant ici étant celui nommé Arguments.
1. Comment déboguer le programme en visualisant le contenu d'une ou plusieurs variables ?
    > Run,debug ou f11
1. Quels paramètres ou fonctionnalités vous semblent particulièrement importants/utiles pour le développement Java ?
    > La plus part de ces fonctionnalités sont importantes et utiles, ils nous facilitent les taches.
