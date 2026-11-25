+++
title = "Veille technologique"
weight = 1
+++

## Premier prompt avec `Claude Sonnet 5.5`

> [!INFO]Prompt  
> Peut tu me parler d'avantage du sujet de l'émergence dans les logiciels et le lien avec `Game of life` et les `Boids`.

L'émergence est une réalité quotidienne en logiciel, souvent subie plutôt que choisie. On peut la voir sous deux angles : celle qu'on provoque volontairement, et celle qu'on subit.

**Émergence subie: quand le système surprend ses auteurs**

Chaque composant est correct, testé, compris, et pourtant l'ensemble se comporte d'une façon que personne n'a conçue.

- *Tempêtes de retries* : un service ralentit, ses clients réessaient, ce qui augmente la charge, ce qui le ralentit davantage. Aucune règle locale n'est absurde (« réessaie si ça échoue »), mais leur combinaison crée une boucle de rétroaction positive.
- *Pannes en cascade et défaillances métastables* : un système peut rester coincé dans un état dégradé même après la disparition de la cause initiale, parce que la charge de récupération entretient la panne elle-même.
- *Thundering herd et cache stampede* : quand un cache expire, des milliers de requêtes se ruent simultanément sur la base de données.
- *Synchronisation involontaire* : des tâches planifiées « à peu près » au même moment finissent par se caler les unes sur les autres, comme des métronomes sur une même planche, ou des cron jobs à minuit pile.
- *Concurrence* : les conditions de course et les interblocages (deadlocks) n'existent dans aucune ligne de code isolée. Ils apparaissent dans l'entrelacement des exécutions.
- *Interactions de fonctionnalités* : deux fonctions parfaitement spécifiées produisent un cas limite que personne n'avait imaginé.

C'est ce qui rend ces bugs si difficiles : lire le code ne suffit pas, parce que le défaut vit dans les interactions, pas dans les composants. On les trouve par l'observabilité, les tests de charge, l'ingénierie du chaos (Chaos Monkey) et la simulation.

**Émergence recherchée: concevoir à partir de règles locales**

- *Protocoles de gossip (Cassandra, Consul, SWIM)* : chaque nœud ne parle qu'à quelques voisins au hasard, et l'information se propage à tout le cluster comme une épidémie, sans coordinateur.
- *CRDT* : des structures de données où chaque réplica applique des règles locales, et où la convergence globale est garantie mathématiquement.
Réseaux pair-à-pair (BitTorrent, DHT) : la robustesse et le routage naissent du comportement de millions de participants.
- *Consensus de type blockchain* : la sécurité émerge d'incitations locales, ce qui reste d'ailleurs plus fragile qu'on le dit.
- *Algorithmes bio-inspirés* : colonies de fourmis, essaims particulaires, algorithmes génétiques, où une solution globale émerge de nombreux agents simples.
- *Jeux vidéo* : le « gameplay émergent » (Dwarf Fortress, Minecraft, Breath of the Wild) vient d'un système de règles physiques et chimiques cohérentes qui se combinent de façons non scriptées. Les designers parlent de systèmes « systémiques » plutôt que scriptés.
- *Simulation multi-agents* : épidémiologie, trafic routier, économie, urbanisme.

**Émergence organisationnelle et d'écosystème**

- *Loi de Conway* : l'architecture d'un logiciel finit par refléter la structure de communication de l'organisation qui le produit. Personne ne le décide, ça émerge.
- *Loi de Hyrum* : avec assez d'utilisateurs, tout comportement observable de ton API, même non documenté, sera utilisé par quelqu'un. Le « contrat réel » émerge de l'usage, pas de la spécification.
- *Écosystèmes de paquets (npm, PyPI)* : des graphes de dépendances géants, avec leurs risques systémiques (l'incident left-pad) que nul n'a conçus.
La philosophie Unix : de petits outils composables produisent des capacités que leurs auteurs n'avaient pas prévues, simplement via les pipes.
- *Wikipédia, Linux, le web lui-même* : de la structure et de la qualité naissant de règles de contribution simples.

**Émergence dans l'apprentissage automatique**

- Un réseau de neurones n'est qu'un empilement d'opérations simples, mais il développe des représentations internes (détecteurs de bords, de visages, circuits d'induction) que personne n'a programmées.
- Les **LLM** montrent des capacités qui semblent apparaître avec l'échelle (arithmétique, raisonnement en plusieurs étapes). Un article connu a toutefois soutenu qu'une partie de ces « sauts » vient du choix des métriques : avec des mesures plus continues, la progression paraît plus graduelle. Le débat est ouvert.
- Le **grokking** : un modèle qui semble avoir simplement mémorisé finit, après beaucoup plus d'entraînement, par généraliser brusquement.
Les systèmes multi-agents de LLM : des agents qui se parlent produisent des dynamiques collectives (boucles, spécialisation, dérives) qu'aucun prompt individuel ne prévoit.

**Ce que ça change pour l'ingénieur**

1. *Penser en dynamique, pas seulement en structure* : files d'attente, boucles de rétroaction, gains, délais. La théorie du contrôle et la théorie des files sont des alliées sous-estimées.
2. *Ajouter des amortisseurs* : backoff exponentiel avec jitter, disjoncteurs (circuit breakers), limitation de débit, délestage de charge. Ce sont littéralement des mécanismes pour empêcher une émergence indésirable.
3. *Observer le système global* : métriques, traces distribuées, tableaux de bord, car on ne peut pas déduire le comportement d'ensemble des parties.
4. *Tester à l'échelle réelle* : certaines propriétés n'apparaissent qu'à partir d'un certain nombre de composants ou de charge.
5. *Rester humble face à la prédiction* : parfois, la seule façon de savoir ce que fera le système est de le faire tourner, d'où l'intérêt des simulations, des environnements de préproduction et des déploiements progressifs.
6. *Parfois, exploiter l'émergence plutôt que la combattre* : des règles locales simples sont souvent plus robustes et plus évolutives qu'un contrôle central compliqué.

**Une mise en garde sur le vocabulaire**

Le mot est parfois utilisé comme une excuse (« c'est un comportement émergent ») pour éviter d'expliquer un phénomène. Une bonne pratique est de se demander : peut-on, après coup, identifier le mécanisme (la boucle de rétroaction, l'interaction) qui produit l'effet ? Si oui, c'est de l'émergence au sens faible, et c'est analysable.

Si tu veux aller plus loin, je peux détailler un cas précis, comme l'anatomie d'une tempête de retries avec un petit modèle, ou les défaillances métastables. Je peux aussi te faire une démo interactive qui simule une cascade de pannes pour qu'on voie le phénomène naître.

**Game of Life (Conway, 1970)**

Les règles tiennent en quatre lignes. Sur une grille, chaque cellule est vivante ou morte, et à chaque tour :

- une cellule vivante avec 2 ou 3 voisines vivantes survit;
- une cellule morte avec exactement 3 voisines vivantes naît;
- tout le reste meurt (solitude ou surpopulation).

Rien dans ces règles ne parle de mouvement, de formes ou de calcul. Pourtant on voit apparaître :

- des planeurs (glider), de petits motifs qui se déplacent en diagonale, alors que chaque cellule, elle, ne bouge jamais;
- des oscillateurs et des natures mortes stables;
- des canons qui produisent des planeurs à l'infini;
- et surtout, la preuve que le jeu est Turing-complet: on peut y construire des portes logiques, de la mémoire, et même faire tourner Game of Life dans Game of Life.

**Les Boids (Craig Reynolds, 1986)**

Reynolds voulait simuler des vols d'oiseaux sans chorégraphier chaque trajectoire. Chaque « boid » suit seulement trois règles, basées sur ses voisins proches :

1. *Séparation* : éviter de percuter les voisins;
2. *Alignement* : s'orienter comme la moyenne des voisins;
3. *Cohésion* : se rapprocher du centre du groupe voisin.

Résultat: des nuées fluides qui se divisent autour d'obstacles, se reforment, tournent en bloc. Il n'y a ni chef, ni plan global, ni notion de « troupeau » dans le code. Le troupeau est une propriété du collectif. Reynolds a d'ailleurs reçu un prix technique pour cette technique, utilisée au cinéma (les chauves-souris de Batman Returns, par exemple).

**Ce que les deux ont en commun**

- Règles locales, effets globaux: chaque agent ne voit que son voisinage.
- Pas de contrôle central.
- Imprévisibilité pratique: même en connaissant les règles, on ne peut souvent prédire le comportement qu'en simulant. C'est ce que Wolfram appelle l'irréductibilité computationnelle.
- Sensibilité aux paramètres: un petit changement de règle (dans Life, par exemple) donne un monde mort, chaotique ou riche. La complexité intéressante vit souvent « au bord du chaos ».