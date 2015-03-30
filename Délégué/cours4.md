# Compilation

## Cours 4

### Expressions Régulières

#### Notations
E: mot vide

R1/R2:
         E_(R1)_E
        /        \
depart()          () final
        \E_(R2)_E/
        
R*:
         __<__
        /  E  \
        \_(R)_/
       E/     \E
depart ()     () final
        \__>__/
           E
           
R1R2

(R1)(R2)

S   ()-->--()
  depart  final
  
  
Exemple: (a/b)*abb    
                                     E-fermeture
Objectif: (AEF avec E Non-deterministe) ----> (AEF Déterministe sans E)
          ____________
         /__(2)__(3)__\
        |/            \|
[0]->-(1)             (6)___(7)___(8)___(9)___/10\
         \__(4)__(5)__/
         
         
Table d'états:

__|_E_|_a_|_b_
0 |1,7| - | - 
1 |2,4| - | - 
2 | - | 3 | - 
3 |
..|

//Dot pour faire les graphes.