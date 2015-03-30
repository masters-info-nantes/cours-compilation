Compilation 
===================
TD N°2
-------------------
### Exo 1

- S -> aSBC 
- S -> aBC
- CB-> BC
- aB -> ab
- bB ->bb
- bC -> bc
- cC -> cc

Type de grammaire: 1
L(G):
S => a<sup>n-1</sup> S(BC)<sup>n-1</sup>

=> a<sup>n-1</sup> aB (BC)<sup>n-1</sup>C

=> a<sup>n-1</sup> a B<sup>n</sup>C<sup>n</sup>

=>a<sup>n-1</sup>abB<sup>n-1</sup>C<sup>n</sup>

=>a<sup>n</sup>b<sup>n</sup>C<sup>n</sup>

=> a<sup>n</sup>b<sup>n-1</sup>bc C<sup>n-1</sup>

=> a<sup>n</sup>b<sup>n</sup>c<sup>n</sup>
            
### Exo 2

L(G){w | |w|<sub>a</sub>=|w|<sub>b</sub>,|w|>=2}

- S -> ab|ab|aSb|bSa|abS|Sab|baS|Sba