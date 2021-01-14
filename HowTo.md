# HelloDojo Marketing

Ce fichier permet de documenter (et logguer) les étapes que vous avez suivies
pour réaliser les demandes du [README.md](README.md).

## Mise en place

Voici les étapes que j'ai suivies pour installer XXX et importer les tables.
e.g. `CREATE SCHEMA `kata-sql` DEFAULT CHARACTER SET utf8mb4 ;`
J'ai choisi d'utiliser phpmyadmin comme client de base de donnée.
J'ai généré le schéma avec draw.io:

![Mon MLD](schema.jpg 'Mon MLD généré avec draw.io')

## Informations à récolter

### Générales

1. La table `people` contient `410` personnes, ma requête est:  
   `SELECT COUNT(*) FROM people`
1. La table `people` contient `20` doublons, ma requête est:

```
SELECT DISTINCT COUNT(*)
FROM people t1
WHERE EXISTS (
              SELECT *
              FROM people t2
              WHERE t1.id <> t2.id
              AND   t1.firstname = t2.firstname
              AND   t1.lastname = t2.lastname
              AND   t1.email = t2.email
			  AND   t1.birthdate = t2.birthdate
			  AND   t1.idnumber = t2.idnumber )
```

1. Cette requête permet de trouver les infos de la personne dont le nom de
   famille est "Warren" ?
   `SELECT * FROM people WHERE lastname="Warren"`
1. La table `people` est triée par nom de famille, ma requête est:  
   `SELECT * FROM people ORDER BY lastname`
1. Les 5 premières entrées de la table `people` sont:

   ```
      Dawn Powell
      Brenna Cain
      Ursula Jacobson
      Claudia Marshall
      Barett Newton
   ```

   `SELECT * FROM people ORDER BY id LIMIT 5`

1. Je trouve toutes les personnes dont le nom ou le prénom contient `ojo`, ma  
   requête est:  
   `SELECT * FROM people WHERE firstname OR lastname LIKE "%ojo%"`
1. Les 5 personnes plus agées sont obtenus avec cette requête:  
   `SELECT * FROM people ORDER BY birthdate ASC LIMIT 5`
1. Les 5 personnes plus jeunes sont obtenus avec cette requête:  
   `SELECT * FROM people ORDER BY birthdate DESC LIMIT 5`
1. La requête suivante permet de trouver l'age en année de chaque personne:  
   `SELECT *, TIMESTAMPDIFF(YEAR, birthdate, NOW()) AS age FROM people`
1. La moyenne d'age est `26.1732`, ma requête est:  
   `SELECT AVG(TIMESTAMPDIFF(YEAR, birthdate, NOW())) FROM people`
1. Le plus long prénom est `Clementine`, ma requête est:  
   `SELECT firstname FROM people WHERE LENGTH(firstname) = (SELECT max(LENGTH(firstname)) FROM people)`
1. Le plus long nom de famille est `Christensen`, ma requête est:  
   `SELECT lastname FROM people WHERE LENGTH(lastname) = (SELECT max(LENGTH(lastname)) FROM people)`
1. La plus longue paire nom + prénom est `TEXT`, ma requête est:  
   `SELECT XXX FROM XXX`

### Invitations

1. Pour lister tous le membres de plus de 18 ans:  
    `SELECT XXX FROM XXX`
   a. et de moins de 60 ans:  
    `SELECT XXX FROM XXX`
   a. qui ont une addresse email valide:  
    `SELECT XXX FROM XXX`
1. Pour ajoutez une colonne `age` dans le résultat de la requête:  
   `SELECT XXX FROM XXX`
1. Pour générer une liste contenant `Prénom Nom <email@provider.com>;`:  
   `SELECT XXX FROM XXX`
1. Avec cette requête:  
    `SELECT XXX FROM XXX`  
   je peux estimer que `NUMBER` personnes habitent en Suisse.

### Countries

1. La requête qui permet d'obtenir la liste d'options
   sous la forme: `<option value="XXX">XXX</option>` est:  
   `SELECT XXX FROM XXX`
1. Pour avoir la liste d'options en plusieurs langues, je procède de la manière suivante:  
   `STRING`

### Jointure

1. Avec cette requête:  
    `SELECT XXX FROM XXX`  
   je sais que `NUMBER` personnes habitent en Suisse.
1. Avec cette requête:  
    `SELECT XXX FROM XXX`  
   je sais que `NUMBER` personnes n'habitent pas en Suisse.
1. Avec cette requête:  
    `SELECT XXX FROM XXX`  
   je liste (nom & prénom) des membres habitants de France, Allemagne, Italie, Autriche
   et Lischenchtein.
1. Cette requête:  
    `SELECT XXX FROM XXX`  
   permet de compter combien il y a de personnes par pays.
1. Cette requête:  
    `SELECT XXX FROM XXX`  
   liste les pays qui ne possèdent pas de personnes.
1. En exécutant cette requête:  
    `SELECT XXX FROM XXX`  
   je sais que `NAME`, `NAME` et `NAME` sont liés à plusieurs pays.
1. En exécutant cette requête:  
    `SELECT XXX FROM XXX`  
   je sais que `NAME` est lié à un pays qui n'existe pas dans la base.
1. De la manière suivante:  
    `SQL`  
   nous pouvons afficher le pourcentages de personnes par pays.

### Procédures

1. Cette requête permet d'extraire `tld` de l'adresse email et de le lier à la
   table `countries`:  
    `SELECT XXX FROM XXX`
1. Pour ajouter une chaine si la jointure ne retourne rien, j'ai procédé de la
   manière suivante:  
    `STRING`
1. Avec `STRING`, nous pouvons partager le mécanisme qui extrait le `tld`.

### Vue

1. J'ai créé une vue bien pratique contenant toutes les infomrations utiles à
   un humain. Ma requête est:  
   `CREATE XXX`

### Finances

1. J'ai créé une table pour les finances. Ma requête est:  
   `CREATE XXX`
1. J'ai modifié la vue en y ajoutant les finances. Ma requête est:  
   `UPDATE XXX`
