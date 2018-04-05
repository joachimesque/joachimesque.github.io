---
title: Générateurs de sites statiques, c'est toujours le bordel
layout: redirect
redirectTo: 'https://joachimesque.com/blog/2018-01-25-generateurs-de-sites-statiques-c-est-toujours-le-bordel'
date:   2018-01-25 03:38:04
categories: blog
---


On va parler de générateurs de sites statiques, et de leur utilisation par des gens qui ne sont pas portés sur la technique, mais qui veulent avoir un site à eux.

Cet article a généré quelques réponses très intéressantes suite à la publication : [@joachimesque][2]

Je voulais faire un tutoriel pour [Julien](https://twitter.com/mariejulien/status/956289601295077376), mais je me suis un peu perdu en route, en comparant l’User Experience de mes sites sous WordPress ou Kirby et celle de ce blog sous Jekyll.

J’ai appris les sites avec b2, qui a donné WordPress. À cette époque, la plupart des CMS utilisables par des nouveaux venus avaient la même approche : des scripts PHP et une base de données MySQL. Les sites sont dynamiques : à chaque requête d’un navigateur, le serveur va exécuter des scripts PHP qui vont composer le HTML, qui est ensuite envoyé au navigateur. La composition de ces pages dépend des contenus dans la base de données.    
On n’a qu’à voir les espaces perso chez Free ou les offres d’hébergement mutualisé, on fonctionne sur du PHP et du MySQL (c’est l’environnement *LAMP* : Linux, Apache, MySQL, PHP).

En 2011 ou 2012, j’ai découvert Stacey puis Kirby, des CMS *flat file*. Toujours dynamiques, toujours en PHP, ces CMS présentaient une différence de taille avec WordPress, on n’a plus besoin d’une base de données. Les contenus sont stockées dans des dossiers et fichiers (les contenus textuels sont au format [Markdown][1]). Trois avantages de ne plus avoir de base de donnée : on diminue le temps de latence du serveur, on diminue les risques liés à la sécurité et surtout on simplifie énormément la migration d’un serveur à l’autre (merci Julien pour le rappel).

Les sites dynamiques peuvent s’aider d’un système de *cache* : lors de la première requête sur une page, le CMS va garder une copie du HTML généré, pour ne pas avoir à la re-générer à chaque requête suivante. Ces systèmes peuvent être épineux à mettre en œuvre (comme pour WordPress) ou être inclus par défaut (comme dans Kirby) : ils rendent la réponse du serveur plus rapide, mais il y a toujours des scripts qui sont exécutés pour servir la bonne version des contenus, voire pour regénérer les pages qui en ont besoin.

Puis, il y a un ou deux ans j’ai commencé à entendre parler des générateurs de sites statiques. Le principe est simple : au lieu d’un site dynamique, le CMS va générer tout le site en pages HTML en une fois. Là, le serveur ne va plus avoir besoin d’exécuter des scripts pour servir le contenu, ce qui va encore limiter le temps de latence et diminuer les risques d’erreurs (si erreur il doit y avoir, elles se présenteront lors de la génération du site, sous les yeux du développeur, qui peut ainsi les corriger plus rapidement).

Des générateurs de sites statiques, il y en a de toutes les formes, dans tous les langages, avec tous les types de stockage. Certains peuvent utiliser des bases de données, certains peuvent utiliser des fichiers Markdown, et d’autres encore peuvent aller se connecter à des API et des services de contenus.    

Les CMS dynamiques offraient une expérience à peu près simple :

1. Upload des fichiers sur un FTP
2. Configuration du site en ligne (5 minutes pour WordPress, 1 minute pour Kirby)
3. Login dans l’interface d’administration
4. Premier post, w00t !

Les CMS statiques peuvent offrir des expériences très différentes :

1. Création du site en ligne de commande
2. Configuration en éditant le fichier de config
3. Écrire « Premier post, w00t ! » dans un nouveau fichier
4. Selon le système :
  - Générer le site en ligne de commande puis uploader sur FTP
  - Utiliser git :
    1. Commit du projet
    2. Push sur un dépôt de code (comme GitHub)
  - Paramétrer le serveur web sur le système, pour pointer vers le  répertoire du site généré

Mais il y a d’autres options (notamment pour les sites avec une base de donnée, ou qui utilisent une API), d’autres outils (comme Netlify).

## Expérience pour les gens qui n’ont pas un profil dev

On a donc deux principes totalement différents du point de vue de l’utilisat·eur·rice.

Du côté des CMS dynamiques, on a une procédure de mise en place qui est très simple : on déplace des scripts dans un dossier (en local ou sur un FTP), on paramètre la base et on a une interface de gestion. Simple. C’est l’héritage de nombreuses années de développement et la maturité de concepts orientés vers l’utilisat·eur·rice, et surtout une prise en compte que cette personne n’est pas forcément geek, juste quelqu’un qui veut un site à soi.

De l’autre côté, c’est beaucoup moins approchable :

- Il faut apprendre git.
- Il faut apprendre la ligne de commande.
- Il faut installer le CMS. Pour installer le CMS il faut :
  - Installer et apprendre à utiliser un gestionnaire de paquets système (Homebrew pour MacOS, Chocolatey pour Windows, Aptitude pour Debian…)
  - Installer l’interpréteur du langage (Ruby, NodeJS, Go, Python…) sur sa machine (tu as les droits d’admin ?)
  - Apprendre à utiliser le gestionnaire de paquets du langage utilisé (gem, npm, dep, pip)
  - Installer le CMS
- Ok, certains CMS n’ont besoin qu’on connaisse que le gestionnaire de paquets système (Hugo par exemple est installable directement avec Homebrew)
- Il faut apprendre les commandes du CMS.
- Si possible on installe et on paramètre les extensions pour son éditeur HTML (SublimeText, VS Code…), s’il y en a.
- Avec un peu de chance on a réussi à ne pas faire de `rm -rf /` jusque là.

Puis vient la question du déploiement, il faudra quasiment toujours faire appel à un service tiers (GitHub, Netlify…). Parce que si on ne fait pas l’upload du répertoire sur le FTP à chaque mise à jour du site, on peut dire adieu aux hébergements mutualisés (les moins chers et plus répandus), mais plutôt se tourner vers des serveurs plus gros, y installer un dépôt git et des systèmes de déploiement continu.

À ce moment du processus, si on compte les minutes, on est à quelques centaines de fois ce que WordPress ou Kirby proposent. Le nouveau paradigme poussé par les Générateurs Statiques a encore une faille fondamentale, que WordPress avait résolu de son côté il y a dix ou quinze ans. Une install de 5 minutes. On n’a pas besoin d’apprendre la ligne de commande, ni le PHP. On pose sur le FTP, et voilà.

Voilà un classement tout à fait subjectif des différentes manières d’avoir un site :

| Catégorie | Type | Exemples |
|:---------:|------|:---------|
|    **1**  | Clé-en-main | Wordpress.com, Tumblr, Squarespace… |
|    **2**  | CMS Personnalisable | WordPress ou Kirby sur serveur mutualisé |
|    **3**  | CMS statique | Hugo ou Jekyll sur GitHub Pages ou Netlify |
|    **4**  | CMS custom | Framework à la Symfony, ou système développé de rien |
|    **5**  | Tout à la main | Comme en 1995 |

En **1**, on dépend de fournisseurs tiers. C’est pas idéal quand ceux-ci enferment leurs utilisat·eur·rice dans des silos, mais au moins c’est pas dur.

En **2**, on peut avoir son propre site en 5 minutes, le customiser comme on veut, et rester propriétaire de ses données. C’est idéal.

En **3**, il faut apprendre toutes les techniques de développeurs, sans pour autant avoir besoin de développer. Si on veut pouvoir se passer de fournisseurs tiers, le principe est très contraignant (upload FTP à chaque mise à jour, on se passe de ça depuis quinze ans avec WordPress).

En **4**, c’est l’option des développeurs purs et durs

En **5**, l’option Stallman fait encore des émules

Il y a quinze ans, on n’avait pas les choix 2 et 3. Et encore, les solutions clé-en-main étaient vraiment pas top avant l’arrivée de Blogger. Puis b2/WordPress est arrivé, et ça a tout changé. Pour que les CMS Statiques soient véritablement révolutionnaires, il faut absolument rejoindre WordPress ou Kirby dans la deuxième catégorie.

On a besoin d’outils.

- Pour simplifier l’installation (la ligne de commande n’est pas suffisante)
- Pour mieux gérer mes contenus via une interface graphique (je veux pouvoir cliquer sur un bouton sur une page web, poster depuis mon ordi, mon téléphone ou la bibliothèque)

Sans ça, les Générateurs Statiques ne sont qu’une mode de plus limitée aux développeurs.

---

## Addendum, deux semaines plus tard

Parmi les outils :

- Une alternative libre à Kirby, [Grav][3], qui a un "cache intelligent".
- Un générateur de sites statiques via une app, [Publii][4]. Le principal souci que je vois, c’est que je ne peux pas poster depuis mon mobile.

Une discussion a eu lieu avec [@borisschapira][5]. Son avis est plus nuancé que le mien, c’est pas dur :) De cet échange, il ressort que les devs et les gens qui veulent créer un site mais qui ne sont pas dev (mais qui peuvent bidouiller un peu), ont des attentes très différentes. Pour un dev, l’avantage c’est de n’avoir aucune page dynamique, même pour un système de gestion de contenus. D’où l’essor des [CMS Headless][6]. La séparation des fonctions (des données d’un côté, le générateur de l’autre, le CMS encore ailleurs) n'est pas forcément argumentée pour expliquer les bénéfices à des non-devs. Ce qui me chagrine vraiment, c’est qu’il n’y a que des solutions déjà hébergées, qui dépendent de fournisseurs cloud comme Netlify, Forestry, etc… De ce que j’ai vu, on n‘a pas de solution vraiment libre et hébergeable sur son propre espace, via par exemple [Yunohost][7].

Au final, ma conclusion reste la même : les générateurs de sites statiques ne sont qu’un outil pour développeur, et de gens qui ne se soucient pas d’héberger simplement leurs propres contenus (sans avoir à installer un Gitlab sur leur espace Free). Tant qu’on n’aura pas de solution qu’un graphiste/intégrateur peut vendre à ses clients, les générateurs de sites statiques resteront le domaine de développeurs. Une sorte de chasse gardée, en somme.

Prévenez-moi quand il y aura du nouveau, de l’auto-hébergeable, basé sur le web.

---

[1]: https://daringfireball.net/projects/markdown/
[2]: https://twitter.com/joachimesque/status/956512246137544704
[3]: https://getgrav.org/
[4]: https://getpublii.com/
[5]: https://twitter.com/borisschapira/status/956597944895066112
[6]: https://jamstatic.fr/2017/12/15/cms-headless/
[7]: https://yunohost.org/