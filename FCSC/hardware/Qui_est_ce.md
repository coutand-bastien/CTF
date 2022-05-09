# Qui est ce

> On vous donne le circuit logique en pièce jointe, et on vous demande de donner une entrée sous forme décimale correspondante à la sortie ```y = 8549048879922979409```, avec ```yi``` les bits de ```y``` où ```y62``` est le MSB et y0 le LSB : ```(y62, ..., y0) = (1, 1, 1, 0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 1, 0, 1, 0, 0, 0, 1)```.
> 
> Encadrez votre réponse entre ```FCSC{}``` pour obtenir le flag.
> 
> Exemple : si on avait donné ```y = 1333333333333333337```, alors le flag aurait été ```FCSC{6497282320360345885}```.
> 
> SHA256([circuit.pdf](./circuit.pdf)) = ```8355cb066c0a500faab5aa916f7ba6e8d896243868c00836d3359c332c7f68f2```.


## Analysis

The statement says that ```y62``` is the MSB and ```y0``` is the LSB. Therefore ```x62``` is the MSB and ```x0``` is the LSB.

## Resolution

A bit of a grind, but we are in CTF, so there is no time to dither about other methods. 

With Logisim, we reproduce the circuit from ```circuit.pdf```. We reproduce the outputs ```(y62, ... , y0) = (1, 1, 1, 0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 1, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 1, 0, 1, 0, 0, 0, 1)```.

We then simply rewrite the corresponding entries ```(x62, ..., x0)```. Then we convert to decimal, we get ```7364529468137835333```.

The flag is therefore: ```FCSC{7364529468137835333}```
