# Compilation
## Cours 9
### Projet Compilo

Construction de la G0 Action

De Quoi à-t-on besoin?

- Un tableau pile Pile[i]
- 2 Dictionnaires:
    DICOT
    DICONT
    
    
Procedure G0Action(act: int)
    var T1,T2: PTR;
début
    case act of
1: debut
    depiler(T1);
    depiler(T2);
    A[T2 î cod+5]:=T1;
fin
2: Empiler( GenAtom(Recherche(DICONT),Action,ca-type)))
3: debut
    dépiler(T1)
    dépiler(T2)                                    // Je prends le T1, je prendre le T2 et je rajoute le GenUnion de T1 et T2
    Empiler(GenUnion(T2,T1));
fin
4: début
    dépiler(T1);
    dépiler(T2);
    Empiler(GenConc(T2,T1));
fin
5: if ca-type = Terminal then
    Empiler(GenAtom(Rechercher(DICOT), act,terminal))
    else
    Empiler(GenAtom(Rechercher(DICONT),Act,NonTerminal))
6: Début
    Dépiler(T1);Empiler(GenStar(T1));
fin
7: Début
Dépiler(T1);Empiler(GenUn(T1));
fin

Pile: Array[1..50] of PTR;
DICOT,DICONT: Dico;
Dico: Array[1..50] of String(200);

/!\ Questions partiel /!\

Q: Quel est le rôle de G0 action?
R: Construire automatiqument les arbres syntaxiques de la GPL

Q: Montrer que la Petite Grammaire GPL composée d'une seule rêgle appartient à G0

Q: Remplisser DICOT et DICONT 

Q: Donner l'état de la pile pour cette GPL
