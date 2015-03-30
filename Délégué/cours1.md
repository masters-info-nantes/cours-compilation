Compilation
====================
Cours 1
--------------------

### Références

    - Alfred AHO and Al
    - "Comilateurs" Principes, techniques et outils InterEditeurs, 1990

### But du cours

L'objectif visé est de présenter les principaux problèmes de la compilation et en particulier:

    - l'analyse syntaxique (l'alphabet, grammaire)
    - l'analyse sémantique et la génération de code
    - l'organisation du compilateur
    
### Introduction à la compilation

Définition simplifiée: Un compilateur est un programme qui lit un programme écrit dans un premier langage - Le langage source - et le traduit en un programme équivalent dans un autre langage - le langage cible.

Programme source -> Compilateur -> Programme cible ou Messages erreurs

#### Compilation par analyse et synthèse:

Il y a deux parties dans la compilation:

l'analyse et la synthèse

- la partie "analyse" partitionne le programme source en ses constituants et en crée une représentation intermédiaire (arbre)
    
- l'analyse linéaire appelée l'analyse lexicale
    
    - y := 234A
    - y := 3+4*2 
    - => Analyse lexicale correcte, analyse syntaxique fausse
    - boolean B, real R
    - R := B 
    - => Analyse sémantique fausse

- Autre exemple:

    - a := b*-c+b*-c
    - symboles: := , * , -
    - identificateurs: a , b , c

    - Arbre:

            :=
           /  \
          a    +
              / \
             *   *
            /|  /|
           b - b -
             |   |
             c   c
                                      
### Rappel classification grammaire

- Grammaire:  
    - S-> AsB (1)
    - S-> ab (2)  
- Vocabulaire:
    - Vn = {S}
    - Vt = {a,b}
    
- Mots possibles: { an, bn }

            S       (1)
          / | \
         a  S  b    (1)
          / | \
         a  S  b    (2)
           / \
          a   b

- Type de grammaire:

    - Type 0
    - Type 1  context_sensitive CS
            alpha->Beta où |alpha|<=|Beta|
    - Type 2  context_free      CF
            A -> B où A € Vn    V = Vn U Vt (Vn = vocabulaire non terminal, Vt = vocabulaire terminal)
                      B € Vt
    - Type 3  régulière
            { A -> aB
            { A -> a
             ou
            { A -> Ba
            { A -> a
      
| 3 | 2 | 1 | 0 | 1 | 2 | 3 |