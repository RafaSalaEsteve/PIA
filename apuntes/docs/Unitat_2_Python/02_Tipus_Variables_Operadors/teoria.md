# 2. Tipus de Dades. Operadors

## 2.1 Tipus de dades

Els tipus de dades són els distints tipus d'informació que podem guardar a les nostres variables. Han anat evolucionant al llarg del temps, i cada vegada accepten valors més grans degut a les potències i capacitats cada cop més grans dels ordenadors.

### 2.1.1 Tipus elementals

Partirem de la taula de tipus que s'aplica en C i en Java, que estan molt més detallats.

| TIPUS       | SIGNIFICAT             | BYTES                       | RANG DE VALORS                  |
|-------------|-----------------------|----------------------------|--------------------------------|
| str         | Cadena de caràcters    | 4 per caràcter en UTF-8     | Segons codificació             |
| int         | Enter                  | 2 o 4                       | [-2¹⁵ . . 2¹⁵]                |
| boolean     | Lògic                  | 1 bit                       | True o False                   |
| float       | Real simple precisió   | 4                           | [-3,438 . . 3,438]            |
| double      | Real doble precisió    | 8                           | [1,7308 . . 1,7308]           |
| void o null | (cap valor)            | 0                           | -                              |

El tipus void/null serveix per a representar l’absència de valor, com per exemple en funcions que no retornen cap valor o quan no sabem alguna informació. Imaginem que tenim una variable entera temperatura, de la qual no sabem el valor. No podem dir que la temperatura és zero, ja que podriem pensar que si l'hem medit (i evidentment fa fret).

### 2.1.1. integer o int

Serveix per a representar nombres enters (sense decimals) amb signe. El tamany està limitat a la memòria del dispositiu. Per defecte el número enter es representa en el sistema decimal, però podem representar-lo en binari, octal i hexadecimal, afegint al principi del numero el prefix de la base en la qual ho representem:

```py linenums="1" title="Representacions de nombres enters, Python"
print(11)     # mostra 11
print(0o11)   # mostra 9
print(0x11)   # mostra 17
print(0b11)   # mostra 3
```

| Prefixe     | Significat   | Base |
|-------------|--------------|------|
| 0b o 0B     | Binari       | 2    |
| 0o o 0O     | Octal        | 8    |
| 0x o 0X     | Hexadecimal  | 16   |

Adonar-se que l'ordre de sortida print ho mostra sempre en decimal.

### 2.1.2 float

Serveix per a representar els numeros reals en notació de coma deximal. Podem representar també en notació científica afegint una ```E``` seguit d'un enter positiu o negatiu

```py linenums="1" title="Reals, Python"
>>> 4.27
4.27
>>> type(4.27)
<class 'float'>
>>> 4.
4.0
>>> .27
0.27
>>> .4e7
4000000.0
>>> 4.2e-4
0.00042
```

Els números reals estàn acotats:

- Els numeros més grans, positiu i negatiu: 1.79e308 i -1.79e308
- Els números més xicotets, positiu i negatiu: 5e-324 i -5e-324

> NOTA: Python també supporta els números complexes, que els veurem al llarg del curs

**Modificadors dels tipus elementals**

Servixen per a alterar els rangs dels tipus elementals vistos anteriorment. Existixen 2 tipus de modificadors:

- Modificadors de longitud:
    - ```short``` → per a enters (opció per defecte en alguns compiladors)
    - ```long``` → per a enters i reals. Dobla el rang
- Modificadors de signe (per a enters):
    - ```signed``` → amb signe (opció per defecte)
    - ```unsigned``` → sense signe

Els valors màxims i mínims de cada tipus estan definits en les llibreries de cada llenguatge, i canvia segons els compiladors.

En ```Python``` hi han menys tipus, però tot i això no perdrem res de potència, donat que, per exemple els límits a partir de ```Python3``` no tenen topes

### 2.1.3 bool

Els valors lògis vertader i fals, especificats per ```True``` i ```False```.

```py linenums="1" title="Python"
>>> type(True)
<class 'bool'>
>>> type(False)
<class 'bool'>
```

### 2.1.4 string o str

El tipus ```string``` no existeix al llenguatge ```C```, i es veu com una successió de caràcters. En ```Java``` ja va apareixer com a objecte i en ```Python``` ja és un tipus bàsic. Un ```string``` és una successió de 0 o més caràcters dins de cometes simples o dobles. Aquestes cometes no poden apareixer dins de la cadena, ja que la primera obri i l'última tanca:

```py linenums="1" title="Python"
>>>print("Soc una cadena.")
Soc una cadena.
>>>print("Soc una "cadena.")
SyntaxError: invalid syntax
```

Posibles solucions:

- Intercanviar cometes dobles per simples, segons necessitats
- Fer servir el caracter contrabarra ```\``` que anula el significat dels simbols especials. Aquest caràcter es llig caracter de escape o d'escapament
- Fer servir com a inici de la cadena la cometa simple ```'``` i dins ja podem fer servir la cometa doble o vicerversa.

```py linenums="1" title="Python"
>>>print('Soc una "cadena.')
Soc una "cadena.
>>>print("Soc una \"cadena.")
Soc una "cadena.
>>>print("Soc una 'cadena.")
Soc una 'cadena.
```

Aquest caràcter té molts usos també, ja que de vegades combinat amb altres caràcters podem aconseguir caràcter no imprimibles o de control:

| Seqüència de Escape | Significat                                 |
|--------------------|--------------------------------------------|
| `\a`               | Alert. S'emet un pitit de l'altaveu        |
| `\b`               | Backspace. S'esborra un caràcter          |
| `\n`               | Line Feed. S'avança una línia             |
| `\r`               | Carriage Return. Es torna el cursor al principi |
| `\t`               | Tabulador. S'avança                       |

```py linenums="1" title="Python"
print("Exemple 1")
print("Hola",end='')
print("\t",end='')
print("Adeu")

print("Exemple 2")
print("Hola",end='')
print("\b",end='')
print("Adeu")

print("Exemple 3")
print("Hola",end='')
print("\r",end='')
print("Adeu")

print("Exemple 4")
print("Hola",end='')
print("\n",end='')
print("Adeu")

print("Exemple 5")
print("Hola",end='')
print("\f",end='')
print("Adeu")
```

```py linenums="1" title="Python"
Exemple 1   
Hola    Adeu    
Exemple 2 
HolAdeu
Exemple 3
Adeu                                                                  
Exemple 4
Hola
Adeu  
Exemple 5                                                            
Hola         
    Adeu
```

## 2.2 Tipus compostos

Els tipus simples serveixen quan tenim que guardar una informació simple, és a dir formada per una sóla dada. Exemple són una temperatura, un nom, una edat, etc. La cosa ja canvia quan tenim que guardar una informació formada per varies dades, com per exemple una data de naixement. Com és evident, aquesta informació està formada per 3 informacions simples (dia, mes i any). Altre exemple seria una adreça, formada per tipus de carrer, nom del mateix, número, escala, codi postal, etc.

> Aquest tipus de dades s'estudiaran més endavant, i són tipus que els definirem els programadors, prenent com a base els bàsics que hem vist anteriorment.

## 2.3 Declaració de variables

Una variable és una porció de memòria (RAM), representada per un nom (identificador) on es guardarà un valor que pot variar al llarg de l’execució d’un programa. Els llenguatges de programació, depenent de com es declaren les variables poden ser de tipat fort o dinàmic. Anem a veure-ho i veurem exemples.

Els llenguatges fortament tipat obliguen de indicar la variable de quin tipus serà abans de fer-la servir. Exemples d'aquest llenguatges són C i Java. Desprès al moment de fer servir les variables els llenguatges vigilen i controlen que el valor que s'emmagatzema correspon al tipus de la variable. Cas de no correspondre donarà error.

???+ example "Llenguatge fortament tipat"
    ```py linenums="1" title="Java"
    int n;      // diguem que n és enter
    float x;    // diguem que x és real

    n=10;         // OK
    n="hola";     // ERROR
    x=5.47;       // OK
    x=7;          // conversió:  x valdrà 7.0

    n=4.56        // semierror:  n valdrà 4, es perd la part real
    ```

> El tipat de Python es coneix també com a [Duck typing](https://en.wikipedia.org/wiki/Duck_typing)

## 2.4 Àmbit i visibilitat

Les variables (i constants) poden definir-se/declarar-se en qualsevol part del programa, però segons el lloc on siguen declarades, les podrem fer servir en tot el programa (globals) o només en alguna part (locals).

- La **visibilitat** és la propietat que indica si es pot accedir o no a una variable en un punt determinat del programa.
- **L’àmbit** és la zona del programa on és visible una variable.

A partir d’estos conceptes podem diferenciar entre objectes locals i globals:

- Objectes locals: Variables (o constants) declarades dins d’un bloc o funció i, per tant, visibles només en l’àmbit d’eixe bloc i dins dels seus sub-blocs.
- Objectes globals: Variables (o constants) declarades al programa principal (fora del main) i, per tant, visibles des de qualsevol lloc del programa.

Tenir en compte que:

- En C i Java anomenem bloc a tot allò que està entre claus { }. Per tant, qualsevol funció, com veurem més endavant, és un bloc.
- En Python un bloc són totes aquelles instruccions que estan al mateix nivell d'indentació, mitjançant tabulacions.

Cal tindre clar que si es declaren variables en un bloc (locals) oculten les variables amb el mateix nom globals.

> Aquests conceptes s'estudiaran més endavant, quan treballem en la programació modular

## 2.5 Operadors i Expressions

Per tancar aquest tema anem a estudiar els operadors que disposem als nostres llenguatges, així com la manera d'interactuar amb l'usuari per a demanar-li dades i mostrar-li els resultats. Mitjançant els operadors podrem construir expressions complexes per a formar els nostres algorismes.

### 2.5.1 Operadors aritmètics

Anem a veure els operadors dels llenguatges de programació. La majoria són similars que Java o altres llenguatges, però hi han xicotetes diferències:

| Significat        | Python | Java      | Exemple                                       |
|-------------------|--------|-----------|-----------------------------------------------|
| Potència          | **     | no hi ha   | 3**2 retorna 9                                |
| Producte          | *      | *         | 3*6 retorna 18                                |
| Divisió           | /      | /         | 10/2 retorna 5                                |
|                   |        |           | 11/2 retorna 5.5 en Python                    |
|                   |        |           | 11/2 retorna 5 en Java (divisió entera)      |
| Divisió entera    | //     | (Python)  | 11/2 retorna 5                                |
| Residu            | %      | %         | 12/5 retorna 2 (residu de la divisió entera) |
| Suma              | +      | +         | 12 + 7 retorna 19                             |
| Resta             | -      | -         | 12 - 7 retorna 5                              |

No cal gaire explicació, donat que son els operadors matemàtics de sempre. Tindre especial cura en la divisió entera.

### 2.5.2 Operadors relacionals

Servixen per a comparar 2 expressions, retornant un valor lògic: vertader o fals. Son els mateixos en Python i en Java:

| Operador | Significat      |
|----------|-----------------|
| `<`      | Menor           |
| `>`      | Major           |
| `==`     | Igual           |
| `!=` o `<>` (sols Python) | Distint          |
| `<=`     | Menor o igual   |
| `>=`     | Major o igual   |

### 2.5.3 Operadors lògics

Els operadors lògics són els de la taula següent. Serveixen per a composar distintes expressions lògiques:

| Python | Java | Significat      |
|--------|------|-----------------|
| `or`   | `||` | El OR lògic     |
| `and`  | `&&` | La AND lògica   |
| `not`  | `!`  | El NOT lògic    |

???+ example "Ejemplo"
    ```py linenums="1" title="Python"
    >>> a = True
    >>> b = False
    >>> a and b
    False
    >>> a or b
    True
    >>> not a
    False
    ```

**Curtcircuit d’expressions**

Si recordem les taules de veritat de les expressions lògiques, podem afirmar que:

- ```false AND ... → false```: false and els que siga sempre és false
- ```true OR ... → true```: true or el que siga sempre és true

Per tant, com les expressions s’avaluen d’esquerra a dreta, en el moment en què puga assegurar el valor final de l’expressió lògica (true o false), pararà d’avaluar-la. Esta manera de treballar s’anomena curtcircuit d’expressions. Això ens dóna un benefici pel que fa a control d’errors i a velocitat d’execució.

Exemples:

```java linenums="1" title="Java"
if ( (dto_1>0) || (dto_2>0) || (dto_3>0) )
    printf("S’ha aplicat algun descompte");
```

Si el ```dto_1``` és major que 0, ja no es comproven les altres 2 expressions i passa a executar-se directament el ```print```.

```py linenums="1" title="Python"
(x<0) and print("El valor de la variable x és negatiu")
```

Només es farà el printf si el valor de x és negatiu.

???+ example "Exercici resolt Pensa què passaria en cada cas sense i amb curtcircuit d’expressions."
    ```py linenums="1" title="Python"
    # Versió 1
    x=10
    y=0
    if ((x/y)>2 and (y!=0)):
    pass

    # Versió 2
    x=10;
    y=0;
    if ((y!=0) and (x/y)>2):
    pass
    ```
??? example "Solució"
    A la versió 1:
    ```py linenums="1" title="Python"
    if ((x/y)>2 and (y!=0)):         
    ZeroDivisionError: division by zero
    ```
    A la versió 2 cap error

> NOTA: l'ordre pass es fa servir quan volem deixar en blanc algun bloc de codi, com és el cas que sols volem provar les condicions