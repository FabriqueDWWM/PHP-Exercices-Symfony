# Symfony 5
## Démarrage
### Pré-requis pour l'environnement de développement
Symfony 5 nécessite PHP 7.2.5 au minimum.<br>
Un environnement type LAMP, XAMPP, ou WAMP (Windows) convient très bien (nous avons mis à jour nos installations).<br>
Nous travaillerons avec MySql (d'autres systèmes sont possibles).
### Pré-requis pour l'exercice
1. Vous avez (normalement) fait l'exercice PHP/include/ppj qui consistait à découper un template en partie et à créer une architecture d'application permettant notamment la duplication de code ;-).<br>
Ce projet contient 5 pages (Accueil, Produits, Blog, Contact, About) réalisées avec Bootstrap. Les produits sont situés dans datas/produits.json tandis que les articles de blog sont situés dans datas/blog.json.<br>
Vous vous êtes également imprégnés de la structure d'application présentée.
2. Vous avez suivi la section `Getting Started` de la [documentation de Symfony](https://symfony.com/doc/current/index.html#gsc.tab=0).
### Votre mission
(Re)créer les pages dans Symfony et stocker les données (produits, articles de blog) en bdd. Faisons cela en plusieurs étapes...
 ## On y va
 ### 1ère étape : des vues et de l'intégration
 1. Dans la console, créez un controller avec `make`.
 2. Dans le controller, créez vos routes pour les différentes pages avec les méthodes associées.
 3. Intégrez vos ressources (Bootstrap, css, images) dans le dossier `public`.
 4. Adaptez les balises `link` et placez-les dans le block `stylesheets`.
 5. Créez les vues : vous pouvez utiliser le même découpage que dans l'exercice ppj. C'est là que les difficultés commencent...<br>
 Il va falloir traduire le code Php des vues en code [Twig](https://twig.symfony.com/), en ayant au prélable passé les données (produits ou articles) à la vue correspondante. La récupération de ces données se fera dans le controller.<br>
 Il faudra également adapter les attributs `src` des images ainsi que les attributs `href` des liens de menu.
 ### 2ème étape : gestion des données
 Jusqu'à présent, les données étaient stockées dans des fichiers json (produits, blog).<br>
 Il est temps de les stocker en bdd.
 1. Repérez le fichier .env à la racine du projet et ouvrez-le !
 2. Ce fichier contient des données de configuration pour le projet. Créez un nouveau fichier .env.local et copiez la ligne suivante :
 
 `DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name"` en remplaçant : 
    - db_user par l'identifiant de mysql (typiquement root)
    - db_password par le mot de passe de mysql (là c'est vous qui savez)
    - db_name par le nom de votre choix pour la base de données (attention à la casse => tout en minuscules)
 4. Dans le terminal, dans le dossier du projet, créez la base données en saisissant la commande :
    - php bin/console doctrine:database:create
    - Cela crée une base de données vide portant le nom que vous avez configuré dans le fichier .env
 5. Créez une entity Produit avec 2 champs : libelle (type string) et img (type string), à l'aide de la commande `php bin/console make:entity`.
 6. Créez une entity Blog avec 2 champs : titre (type string) et texte (type text) de la même façon.
 7. Générez les tables de la bdd avec les 2 commandes suivantes :
    - php bin/console make:migration
    - php bin/console doctrine:migrations:migrate
 8. Créez une méthode de controller associée à une route nommée `/produit/add`. 
 Le rôle de cette méthode va être de créer un nouveau produit (vous créerez des formulaires par la suite).
 Inspirez-vous du paragraphe *"Persisting Objects to the Database"* de la [documentation](https://symfony.com/doc/current/doctrine.html).
 8. Toujours en vous inspirant de la documentation, créez des méthodes de mise à jour (update), de suppression (delete).
 9. Adaptez le code d'affichage des produits (la page Produits) de manière à afficher les produits stockés en bdd => *"Fetching Objects from the Database"* de la [documentation](https://symfony.com/doc/current/doctrine.html).
 10. Répétez les points 7 à 9 pour l'entity `Blog`.
 

    Vous avez bien mérité un p'tit café !

 > Prochaine étape : [les formulaires](https://symfony.com/doc/current/forms.html)
 
