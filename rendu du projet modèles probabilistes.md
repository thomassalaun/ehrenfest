==task(faire une courte introduction rappelant le pourquoi de ce projet et la référence de l'énoncé)==

L'introduction dit,
> ([[sujet.pdf#page=1&selection=55,0,80,11&color=yellow|p.1]])
> Considérons deux pièces $A$ et $B$ hermétiquement closes et de même volume. On fait le vide dans la pièce $B$ puis on pratique un minuscule trou dans la cloison séparant ces deux pièces et l’on mesure l’évolution de la pression dans chacune des pièces. Il paraît raisonnable de penser que la pression va s’équilibrer.

Montrons que l'intuition de l'équilibre des pressions n'est pas difficile.
Admettons que le gaz considéré est parfait, càd que l'on peut considérer la relation suivante comme vérifiée,
$$ PV = nRT$$
- $P$, la pression
- $V$, le volume du système : ici, $V_A = V_B = V /2$
- $n$, le nombre de moles du système
- $T$, la température du système
- $R \approx 8.31 ~ J \cdot mol^{-1} \cdot K^{-1}$, la constante des gaz parfaits 

*Remarque* : le nombre $n$ exprimé en moles ($mol$) n'est rien d'autre que le nombre de molécules comptées par paquet de $N_A = 6.02214076 \times 10^{23} ~ \textrm{mol}^{-1}$ entités chimiques. 

Il semble logique de considérer qu'à la fin de la transformation, le nombre de moles s'équilibre dans les deux urnes (ceci est vrai car le tuyau est petit). Ainsi, 
$$n_{A} = n_{B} = n/2$$
En utilisant la loi des gaz parfaits,
$$ P_{A} = \dfrac{n_{A}RT}{V} = \dfrac{1}{2}\dfrac{nRT}{V} $$
$$P_{B} = \dfrac{n_{B}RT}{V} = \dfrac{1}{2}\dfrac{nRT}{V}$$
D'où, 
$$ P_{A} = P_{B} $$
## Question 1

> ([[sujet.pdf#page=6&selection=320,3,324,26&color=yellow|p.6]])
> Justifier le lien entre l’évolution de la pression abordée dans l’introduction et le modèle de l’urne d’Ehrenfest.

Comme énoncé dans la section précédente ==task{à bien identifier lors de la restructuration du rapport}== , il existe un lien clair entre la pression et le nombre de molécules présente dans le modèle. Si l'on considère un modèle de gaz parfaits, nous voyons que cette relation est même linéaire,
$$ P = \dfrac{RT}{V} \times n \Rightarrow P = c \times n $$
Dans le cas de notre expérience, nous pouvons considérer que la température $T$ est constante (bien qu'elle varie sûrement au moins un peu en réalité) et le volume de l'urne $V$ est bien constant ici.

Cela correspond bien à l'interprétation intuitive de la pression. La pression exercée par un gaz sur une paroi de l'urne provient de la somme des chocs de chaque molécule sur cette paroi. On comprend alors que plus il y a de molécules, plus il y a de potentiels chocs et donc plus de pression.

Comprendre dans quelle urne se trouve les molécules ; ou plus simplement de comprendre combien de molécules sont dans quelle urne, ce que modélise le modèle d'Ehrenfest, permet donc de comprendre l'évolution de la pression dans chacune des urnes et donc de la dynamique de pression du système global.

## Question 2

> ([[sujet.pdf#page=6&selection=325,3,359,15&color=yellow|p.6]])
> Commenter et illustrer la proposition 1.2. On pourra mettre en évidence par la simulation la vitesse de croissance de $a \mapsto m^a_a$ et le fait qu’à $a$ fixé, $d \mapsto m^a_d$ croît mais lentement.

### Notations et définitions du modèle
==nb{ceci est nécessaire avant de parler et comprendre la proposition 1.2. ; section copier-coller de l'énoncé plus ou moins}==
#### Configuration et espace d'états (définition)
On considère $a$ boules dans les urnes $A$ et $B$, où chaque boule se trouve soit dans l'une soit dans l'autre. Une configuration des molécules est representée par un $a$-uplet de la forme,
$$
\begin{align*}
x &= \left( x_1, \dots, x_a \right) \\
\forall i \in \{1, \dots, a\}, x_i &= 
\begin{cases}
1 ~ \text{si la boule $i \in A$} \\
0 ~\text{si la boule $i \in B$}
\end{cases}
\end{align*}
$$
*Remarque* : ces boules représentent nos molécules.
L'espace d'états que l'on considèrera ici est donc,
$$ 
F = \Bigl\{ x = \left( x_1, \dots, x_a \right)~; \forall i \in \{1, \dots, a\}, x_i \in \{0,1\}  \Bigr\} \\
$$
Autrement dit,
$$ F = \{0,1\}^a $$
#### Distance entre configurations
On définit aussi la distance entre deux configurations comme suit,
$$
\begin{align*}
d: F \times F & \longrightarrow \mathbb{N}\\
(x,y)&\longmapsto \sum_{i=1}^{a} ~\lvert x_i - y_i \rvert
\end{align*}
$$
càd le nombre de coordonnés dont les deux configurations diffèrent. 

*Remarque* : $d$ n'est rien d'autre que la distance de Manhattan ==task(référence ici)== sur $F\times F$.

Autre définition, par confort d'écriture, on notera
$$ \forall x \in F, V(x) = \{y\in F, y\sim x\}$$
càd que $V$ est l'ensemble des voisins d'une configuration $x \in F$ donnée.
#### Configurations voisines
On dira que deux configurations $x, y \in F$ sont voisines, ce que l'on notera $x \sim y$, si elle diffère d'une coordonnée, autrement dit, s'il n'y a qu'une seule boule qui a changé d'urne entre les deux configurations. Ainsi,
$$
x \sim y \Longleftrightarrow d(x,y) = 1
$$
*Remarque* : bien que la notation pourrait le suggérer, la relation de "voisins" entre deux configurations n'est pas une relation d'équivalence,
- elle n'est pas réflexive : $d(x,x) = 0 \neq 1$
- elle n'est pas transitive : soient $x,y,z \in F, x\sim y$ et $y \sim z$, il est possible que $x \nsim z$ ; en effet, la coordonnée $i \in \{1, \dots, a\}$ dont diffère $x$ et $y$ n'est pas forcément égale à la coordonnée $j \in \{1, \dots, a\}$ dont diffère $y$ et $z$, i.e, $d(x,z) = 2 \Rightarrow x \nsim z$
#### Processus de Markov : suivi de l'évolution des configurations
Pour finir avec les définitions, nous définissons le processus de Markov $(Y_n)_{n\in\mathbb{N}} \in F^{\mathbb{N}}$ associé aux configurations, 
$$
\begin{align*}
\forall n \in \mathbb{N}, ~ & ~~~ Y_n \in F \\
\forall n \in \mathbb{N} \smallsetminus \{0\}, ~
&\begin{cases}
Y_n \in V(Y_{n-1})\\
Y_n \sim \mathrm{Uniforme}\Bigl( \#V(Y_{n-1}) \Bigr)
\end{cases}
\end{align*}
$$
autrement dit, à chaque étape, la chaîne choisit une configuration voisine selon une loi discrète uniforme (ayant pour paramètre le nombre de configuration voisines à l'étape considérée).

==nb(il est clair que ce processus est de Markov étant donné que la sélection de la nouvelle configuration ne dépend que de la précédente, i.e. ce processus vérifie la propriété de Markov, cependant il est peu satisfaisant de l'annoncer et de ne pas le démonter, à voir si on a le temps)==

==suite du travail :== 
	- ==expliquer la proposition 1.1==
- ~~pour cela, il faut aussi comprendre et formaliser la logique d'ordre des états, càd comment les mettre dans un ordre (on diffère les coordonnées une à une en partant de la dernière mais pas encore super clair)~~
en fait il faut voir cela comme un nombre binaire, par exemple, $(0,0,1)$ peut-être representé par $001$ en binaire etc. donc l'ordre suit une logique binaire ascendante, càd, que les couples sont dans l'ordre décimal mais représenté en binaire

il y a $a$ états qui sont voisins avec $x\in F$, pour construire une configuration voisine de $x$, on choisit une coordonnée parmi les $a$ et on la modifie, toutes les autres doivent être égales à celles de $x$, on a donc bien $a$ choix

est-ce qu'il est possible de trouver un schéma qui à parti d'une configuration $x$ donnée de trouver ses voisins, en notation décimale -> cela permettrait de savoir les nombres avec des coefficients non nuls sur la matrice, c'est le produit scalaire des coordonnées avec le vecteur des puissance de 2 de a-1 à 0. 

- ~~comprendre plus en détail irréductible que l'intuition que j'en ai : tous les états communiquent (montrer que toute configuration a une voisine, c'est assez ogique, un simple raisonnement par l'absurde suffira sûrement)~~
Soit $x = (x_1, \dots, x_a) \in F$, on peut construire une configuration $y \in F$, telle que $x\sim y$.
Prenons, pour $i \in \{1, \dots, a\}$,
$$
\begin{align*}
& y_1 = 1-x_1\\
i > 1,~& y_i = x_i  
\end{align*}
$$
l'idée est simple, on garde toutes les composantes identiques sauf la première qu'on modifie dans le sens où s'il s'agit d'un $0$, on la définit égale à 1 et inversement. Dès lors,
$$
\begin{align*}
d(x,y) &= \sum_{i=1}^a ~ \lvert x_i - y_i \rvert \\
&= \lvert x_1 - y_1 \rvert + \sum_{i=2}^a \lvert x_i - y_i \rvert \\
&= \lvert x_1 - (1-x_1) \rvert + 0 \\
&= \lvert 2x_1 -1 \rvert \\
d(x,y) &= 1 \Longrightarrow x \sim y 
\end{align*}
$$
	- ==comprendre récurrente (j'ai perdu cette notion)==
	- ==comprendre périodique==
	- ==comprendre bistochastique==
	- ==revoir châine invariante et comment démontrer (c'est la solution d'un système je crois)==
	- ==comprendre ce qu'est le temps retour (ou temps moyen de retour jsp quelle est la différence)==
- ==définir les quantités $a \mapsto m^a_a$ et $d \mapsto m^a_d$ et démontrer empiriquement et mathématiquement la proposition 1.2==
- ~~corriger la définition, on remplacera les X_n du processus marovien par des Y_n car ce n'est pas le processus principal des urnes d'ehrenfest.~~

