# Le jour de l'espace 
On a à notre disposition un oracle de chiffrement, en jouant avec on se rend compte que l'oracle chiffre les messages par blocs de 5 lettres.

En partant du bloc aaaaa et en chiffrant successivement 
baaaa
caaaa
daaaa 

On se rend compte que le chiffrer est calculé de cette manière : 
```

for o in range(5):
     result[o] += (ord(alphabet[i])-97) * 9
     result[o] += (ord(alphabet[i])-97) * 4
     result[o] += (ord(alphabet[i])-97) * 18
     result[o] += (ord(alphabet[i])-97) * 20
     result[o] += (ord(alphabet[i])-97) * 8
     result[o] = result[o] % 25


```

On peut faire la même chose pour le caractère suivant, en chiffrant :
abaaa
acaaa
adaaa

Et ainsi de suite pour les cinq caractère.
La méthode de chiffrement est linéaire pour chaque opération sur chaque lettre.

```
carre = [[9,11,5,13,19],[4,0,6,14,21],[18,2,7,15,22],[20,1,10,16,23],[8,3,12,17,24]]
alphabet = "abcdefghijklmnopqrstuvwxyz"
dic = {}
for i in range(25):
    print(i)
    for j in range(25):
        for k in range(25):
            for l in range(25):
                for m in range(25):
                    result = [0,0,0,0,0]
                    for o in range(5):
                        result[o] += (ord(alphabet[i])-97) * carre[0][o]
                        result[o] += (ord(alphabet[j])-97) * carre[1][o]
                        result[o] += (ord(alphabet[k])-97) * carre[2][o]
                        result[o] += (ord(alphabet[l])-97) * carre[3][o]
                        result[o] += (ord(alphabet[m])-97) * carre[4][o]
                        result[o] = result[o] % 25
                    dic[alphabet[result[0]] + alphabet[result[1]] +alphabet[result[2]] +alphabet[result[3]] +alphabet[result[4]]] = alphabet[i] + alphabet[j] +alphabet[k] +alphabet[l] +alphabet[m]
                   


print(dic["ueoma"] + dic["spblb"] + dic["ppadg"] + dic["idtfn"])

``` 

Maintenant, que l'on sait comment le chiffrement fonctionne, on peut chiffrer tous les blocs de cinq lettres possibles et déchiffrer le texte chiffré et retrouvé le flag.

