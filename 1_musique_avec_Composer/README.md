# Partie 1 : En avant la musique !

## Compétences associées

> - Développer la partie back-end d'une application web ou web mobile. Niveaux : `Comprendre` `Dupliquer` `Appliquer`

## Installation

L'univers (on dit aussi écosystème) **PHP** est empreint de références musicales.

A tout seigneur, tout honneur, voici **Composer** !

Allez, on l'installe => [Composer](https://getcomposer.org/). Cliquer dur Download. Pour **Linux**, c'est le paragraphe intitulé **Command-line installation**. ;-)

Ok, maintenant, assurez-vous que **Composer** est intallé globalement en tapant la commande `composer -v` dans un terminal.

## A quoi ça sert ?

Bon d'accord, mais ça sert à quoi ?

Tu connais **npm** le gestionnaire de librairies de **NodeJs** ? Ben c'est la même chose, mais pour **PHP**.

Avec **Composer**, on peut donc installer n'importe quelle librairie hébergée sur **Packagist** pour l'utiliser dans notre projet. Enorme !

Allez, on se lance, on va installer une librairie (on dit package aussi) qui sert à afficher des **var_dump** plus jolis !

## Création d'un projet Php

Ben, on crée juste un dossier dans notre répertoire web.

## Installation du package VarDumper

On va sur [Packagist](https://packagist.org/packages/symfony/var-dumper). On trouve le package **symfony/var-dumper**.

Dans le terminal (dans le répertoire du projet), on colle la commande `composer require symfony/var-dumper`.

Et bam, le package est installé ! On a un répertoire **vendor** qui contient les fichiers du package (on dit aussi Component chez **Symfony**), un fichier **composer.json** et un fichier **composer.lock**. Allez donc voir ce que contiennent ces 2 fichiers !

## Utilisation du package

Sur la page [Packagist](https://packagist.org/packages/symfony/var-dumper), il y a un lien [Documentation](https://symfony.com/doc/current/components/var_dumper.html) qui dirige vers la doc de **Symfony** :-o.

Testez la fonction dump().

...si vous n'y arrivez pas, parlez-vous ! ;-)

Lorsque vous utiliserez **Symfony**, vous vous servirez beaucoup de la commande `composer require` pour installer des packages (ou encore components, ou encore bundles...jargon quoi...).

Bon c'est bien, c'est un peu magique, alors jetez quand même un oeil au code du fichier `vendor/autoload.php`, c'est quand même lui qui fait le taf ( on voit ça juste après ;-) ) !

## La fête !

Pour terminer cette petite mise en bouche, installons un autre package via la commande `composer require symfony/http-foundation`.

Amusez-vous un peu avec les classes `Symfony\Component\HttpFoundation\Request` et `Symfony\Component\HttpFoundation\Response`. Vous pouvez par exemple récupérer les paramètres de la requête Http et renvoyer une réponse via la classe Response. `use` vous sera utile...

Testez également les sessions. Vous pouvez créer un script `flash_message.php` qui crée le flash message (il faudra exécuter le script) et en récupérer le contenu dans `index.php`.

Y a la doc quoi...

C'est d'la musique !

> Ok j'ai testé, mais c'était pas plus simple d'utiliser la superglobale $_SESSION ?

> Tu n'as pas tort, jeune Padawan, mais aujourd'hui ta vie change, tout sera `Objet` : les requêtes Http, les réponses Http, les sessions, les cookies...tout !

## Et Git au fait ?

Ah, oui !

> Ne faites pas un `git add .` tout de suite ! Cela versionnerait les librairies contenues dans le dossier `vendor`, et nous ne souhaitons pas nous retrouver à pusher tout ça sur notre Github !

C'est pas moi qui le dit : 

![info Composer](images/info_github.png)

Créez donc un fichier `.gitignore` (n'oubliez pas le point au début) à la racine du projet. Dans ce fichier, écrivez simplement `vendor/` et enregistrez. Vous l'aurez compris, cela va exclure le dossier **vendor** des commits. Nickel !

Maintenant vous pouvez faire vos `add .`, ` commit` et `push`. Cool !

> Hola, attends, mais comment je fais moi si je veux récupérer mon projet sur Github si y a pas les librairies ?

Ben, c'est ce qu'on voit maintenant...:sunglasses:

# C'est tout ?

Bon, ok, puisque vous insistez, voyons quelques cas d'utilisation un peu plus "touchy"...

## Partie 2 : composer install

Pour ne pas vous emmêler les gaules, créez un nouveau répertoire dans votre dossier web.

A la racine de ce projet, créez un fichier `composer.json`.

Mettez-y le code suivant :

```json
{
    "require" :{
        "symfony/routing": "^4.3"
    }
}
```

Et maintenant, dans le terminal, tapez la commande `composer install`.

Eh oui ! C'est bon, le composant Routing de Symfony est installé dans votre dossier `vendor`. Dingue !

Et là, vous venez de comprendre (ou pas ?!) comment vous pouvez installer vos dépendances (tiens, encore du jargon !) - ou librairies - dans une application dont vous n'avez "commité" que le fichier `composer.json` et pas tout le dossier `vendor`.

Si vous n'êtes pas convaincu, reprenez le fichier du projet précédent, et testez-le en faisant un `git clone` du projet puis `composer install`.

## Plus de pouvoirs

Composer permet de créer des applications complètes via la commande `composer create-project`.

Par exemple, pour créer un projet Symfony : `composer create-project symfony/skeleton blog`.

> Maintenant tu es prêt jeune Padawan.
> ...
