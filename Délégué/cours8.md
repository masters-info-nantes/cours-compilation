# Compilation
## Cours 8
### Grammaire LR(k)

S => U$ => aAB$
  => aAbB$
  => aAbb$
  => acbb$
  

S -> U$                   a      c      b      b      $
U -> aAB                   \     |      |      |     /
A -> cA                     \    A      |      B    /
A -> c                       \   |      B ____/    /
B -> bB                       \__U ____/          /
B -> b                            \              /
                                   \___________S  
                                   
Poignée veut dire reconnaissance d'une rêgle

### Definition des handles

\  \|/  |
 o  o   o
  \  \  /     => 5 poignées
   \   o
    \ /
     o
     
     \ /
      o
       \ /       => 4 poignées
        o
         \ /
          o
           \ /
            o
            

S -> E$
E -> E + T
E -> T
T -> T*F
T -> F
F -> ( E )
F -> id

### A.A.P (Automate à pile)

 | |                           fenetre
 | |              --> | a | b | c | ... | $ |
 | |        o   o   
 |_|   <--  \___/
 |_|                    /!\ Shift -> Empiler le caractère puis Scan
 |_|                    /!\ Reduce -> Remplacer la partie droite par la partie gauche
                                         // Opérations //
pile


### Algo de la Table SR

    _________
   |  Scan   |
   |Empile(w)|
   |  Scan   |
    ---------
------->|<-------------------------------
|   ____v____________ Accept            |
|  | Table[Sommet,w] | --> ( success )  |
|  /-----------------                   |
|(Err) /         \                      |
|     v shift     v reduce              |
|  __/______    ___\__________          |
|_|Empile(w)|  |Remplacer     |_________|
  |  Scan   |  |partie droite |
   ---------    --------------
   
#### Table d'analyse SR

Exemple:

S -> A$
A -> aAb  an c bc $
A -> c

   fenetre
   
___|_a_|_b_|_c_|_$_
_a_|_S_|_e_|_S_|_e_
_b_|_e_|_R_|_e_|_R_   pile
_c_|_e_|_R_|_e_|_R_
_A_|_e_|_S_|_e_|_A_

Pour une grammaire, à partir d'une table SR, on déroule l'algorithme, à la fin on saura si le mot a été accepté, sinon c'est une erreur

Pour la construire, regarder au niveau des règles de grammaires, si deux éléments peuvent se suivre, si non, Erreur
Commencer par l'accept, puis par les error.
Puis par les reduce, (si l'élément de la pile termine une partie droite d'une règle)
et tout ce qui n'est pas reduce, ce sont des shift

Exemple:

S -> E$
E -> E + a
E -> a

1) a+a+a+a$
2) Table SR
3) Configuration de la pile

a  +  a  +  a  +  a  $
 \ \  |  |  / /  /  /
  E \ |  | / /  /  /
   \|/  / / /  /  /
    E  / / /  /  /
     \| / /  /  /
      E  / _/  /
       \| /   /
        E    /
         \  /
          S
          
___|_a_|_+_|_$_|
_E_|_e_|_S_|_A_|
_a_|_e_|_R_|_R_|
_+_|_S_|_e_|_e_|
