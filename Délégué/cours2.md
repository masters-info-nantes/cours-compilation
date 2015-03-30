Compilation
==========================
Cours 2
--------------------------
### Les analyseurs
Pour écrire un analyseur, il faut une grammaire.

G=(VT,VN,S,P) où
S= axiome (racine)
VN = vocabulaire non-terminal
VT = vocabulaire terminal (ne se dérive pas, les feuilles)
P = l'ensemble des règles de réécriture

### Arbres de dérivation

Considérons la grammaire G suivante

E ->E+T|T       T->T*F|F

F->(E)|0|1|2|3|4|5|6|7|8|9

=> 15 règles de réécriture

La chaîne donnée étant (5+2)*3+1, l'arbre de dérivation sera
```
        +
       / \
      1   *
         / \
        3   +
           / \
          5   2
          
         E
       / | \
      E  +  T
      |     |
      T     F
    / | \    |
   F  *  3   1
 / | \
(  E  )
 / | \
E  +  T
|     |
T     F
|     |
F     2
|
5
```
Compilateur LL ( analyseur descendant) (analyse)L -> gauche à droite (règles)L -> gauche à droite (80% des compilateurs)
Compilateur LR ( analyseur descendant) (analyse)L -> gauche à droite (règles)R -> droite à gauche

### Grammaire Régulières

définition 1: 

Soit G = (VT,VN,S,P) une grammaire donnée, G est régulière si et seulement si toutes les règles de production sont de la forme :

    A -> aB ou A -> mot vide
    avec A,B éléments de VN
    et a élément de VT
    
définition 2:

    Un automate d'états finis est une machine définie par:
    Q : ensembe des états possibles
    F : ensembles des états finals
    AL: alphabet d'entrée
    𝛿 : fonction de transition
    Q0: état initial
    
Exemple:

S -> +A|-A|+G|-G

A -> dB         B->dB|H|motVide
G -> D          D -> dH         H->dH|mV

voir AEF sur feuille

Matrice:
```
    +   -   .   d   final
S   A'  A'  e   e   faux
A'  e   e   D   B   faux
B   e   e   H   B   vrai
D   e   e   e   H   faux
H   e   e   e   H   vrai
```