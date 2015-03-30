# Compilation
## Cours 7
### Grammaire LL(k)

LL(k) C_ LR(k)
 
Ex

S -> U$
U -> aAB
A -> cA
A -> c
B -> bB
B -> b

ac^nb^n$
n,m>=1

S => U$
  => aAB$
  => acAB$
  => accB$
  => accb$
  
  LL(1) => 1 est le degré de profondeur
  
### First (Premiers) et Follow (Suivants)

#### First(N)
1) Si N-> A... alors First(N)=First(A)
2) Si N->c... alors First(N)={c}                          //Singleton petit c
3) Si N-> A.B.c et si A =*> E Alors First(N)=First(B)     // =*> veut dire dérive étoile // E signifie epsilon

Ex1: Trouver les First

S ->E$
E -> E+T
E -> T
E -> T*F
T -> F
F -> (E)
F -> id
  
First(S) = First(E)
First(E) = First(T)
First(T) = First(F)
First(F) = {( id}

Ex2:

M -> A d|e
A -> b* c*


First(A) = { b (règle 2) c (règle 3 et 2) }
First(M) = { First(A) e d }
First(M) = { b c d e }

#### Follow(N)

1)si A -> ... Nc ... Alors Follow(N)={c}
2)si A -> ... NB ... Alors Follow(N)=First(B)
3)si A -> ... N      Alors Follow(N)=Follow(A) 

Ex: cf(Exemple 1)

Follow(E) = { $ + ) }
Follow(T) = { Follow(E) * }
Follow(F) = { Follow(T) }

#### Grammaire LL(1)

1) A -> a1 | a2 | ... | an
    First(ai) inter  First(aj) = Ens. vide
    pour i != j
    
2) A =*> Epsi 
    on doit avoir First(A) inter Follow(A) = ens. vide

Ex 3:

S -> Aa
A -> b* | a

Est-elle LL(1)?

First(A) = { b a }
Follow(A) = { a }

First(A) inter Follow(A) = { a }
Donc Non LL(1)

  X                                                                 X
 / \                                                               /|\
/ ! \ Toutes les grammaires récursives à gauche ne sont pas LL(1) / | \



  