---
layout: redirect
redirectTo: 'https://joachimesque.com/blog/2017-12-13-des-noms-de-commune-generes-par-une-ia'
title:  "Un ordinateur m’a généré 6526 noms de communes françaises"
date:   2017-12-13 20:02:44 +0200
categories: blog
---

J’aime les noms de villages qu’on découvre au fil de nos déplacements en France. Il y a des Saints à ne plus savoir auquel se vouer, des -ville, des -ac, des -lly, quelques -aye et plein de -heim pour faire bonne mesure.

Il y a quelques temps, je suis tombé sur ce billet : [I trained an A.I. to generate British placenames](https://medium.com/@hondanhon/i-trained-a-neural-net-to-generate-british-placenames-9460e907e4e9) ; l'auteur a généré des noms de villages anglais grâce à une IA… et il donne sa recette.

Enfin, une IA, c'est vite dit. Comme tout ce qui touche à l'Intelligence Artificielle ces temps-ci, il s'agit juste d'apprentissage bête et méchant, et de régurgitation plus tout à fait au hasard.

## Comment j'ai fait ?

J'ai juste suivi la marche à suivre sur le billet de Dan Hon qui m’a inspiré : [I trained an A.I. to generate British placenames](https://medium.com/@hondanhon/i-trained-a-neural-net-to-generate-british-placenames-9460e907e4e9)

1. On commence avec une liste de noms. Là, j'ai pris celle fournie sur le site niap3d : [Liste des communes françaises](https://blog.niap3d.com/fr/4,10,news-50-Liste-des-communes-francaises.html). J'en remercie l'auteur au passage.
2. J'ai suivi le conseil de Dan Hon, et j'ai opté pour [torch-rnn, par jcjohnson](https://github.com/jcjohnson/torch-rnn)
3. Je suis sous Mac, donc j'ai utilisé [l'image Docker de crisbal](https://github.com/crisbal/docker-torch-rnn)
4. J'ai suivi les instructions du README
5. Je suis allé faire mes courses, à base de de cadeaux de noël et de bière
6. J'ai joué un peu avec les résultats
7. Et voilà : [80000 caractères](https://github.com/joachimesque/communes-francaises/blob/master/6526-communes.txt), soit 6526 noms de communes (et conurbations) françaises.

## 99 noms de communes plus vraies que nature

(la 54 va vous surprendre)

- Oz
- Patée
- Galboulhe
- Magniguezheim
- Chiffas-sur-Gruallan
- Flonches-et-Molard
- Curageaux
- Ortillard
- Enville
- Éhilly
- Barcion-sur-Rovigne
- Ralauraderin
- Mertellez-le-Gronces
- Heulles
- Ligny-sur-Toux
- Congniol
- Montchwill
- Maizy-Meurs-en-Bellesse
- Métous-sur-Doux
- Bogrégures
- B'onceuil
- Cloutz
- Le Poong
- Pleuvrinville
- Pléchon
- Bouflac
- Bèss-le-Grozaud
- Puiffontreuis
- Porg-de-Bourgeant-Saint-Jeure-Boolarotte
- Gouchapon
- Moulleuve
- Crâchezé
- Écugny-en-Ahuhé
- La Champagnac
- Castel-de-Paudas
- Compothe-du-Croigu
- Cémisericourt
- Saint-Juve-de-Venoues
- Sainte-Marron-le-Gronche
- Saint-S'fôge
- Sallefrange
- Tailly-sur-Riseuse
- Mausticourt
- Mumerchemolette
- Floustach
- Port-sur-sur-Écoulles
- Neupignol
- Bouille
- Montzery-Bornanthex-Corlencoire-lès-Long-de-Ryailles
- Cradons
- Casteau-sur-Oux
- Gouville-Saint-Geuchef
- Plouille
- Bordelles-les-Baise
- La Poutre-de-Pressin
- Le Chéné-l'Ognar
- Bois-du-Sages
- Boullou
- Groces-sur-Olle
- Manabra
- Saint-Froule
- Saint-Sauvert-le-Mage
- Gruvette
- Zianville
- Saudevin
- Saint-Sullaire-lès-Cattenion
- Beauffeumes
- Bougly
- Meux-le-Coudon
- Suré-Bigarres
- Venis-en-Porzon-des-Dun
- Bandelaing
- Saint-Capul-le-Chartier
- Rinscianville-en-Vringrate
- Cevrô-Saint-Jean-sous-Bois
- Creuvrotte
- Saint-Agnac-le-Pantmaine-le-Foux
- Saint-Maurent-le-Cambre
- Termecourt
- Saint-Martin-de-Girerance
- Cirigny-l'Ableulg
- Chebron
- La Firerue-du-Jaille
- Goblex
- Francheminet
- Valegnou
- Chépiverie
- Faugnou
- Saint-Martint-d'Appinion
- Ligny-la-Pierre-de-Bois
- Nany
- Vauvignolles
- Blatuin-en-Puif
- Saint-Ouin-d'Oruil
- Michel
- Amélinlemil-de-Commie-sur-Avi
- Pérignond-en-Lapevrois
- Licon
- Châtel-Loupcourt-Piol

## Plus de lecture…

[I trained an A.I. to generate British placenames](https://medium.com/@hondanhon/i-trained-a-neural-net-to-generate-british-placenames-9460e907e4e9)
