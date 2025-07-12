# 2. Exercici pràctic

## 1. Proves de rendiment

En aquesta pràctica anem a fer una prova de rendiment de 3 llenguatges de programació: C, Python i Python amb numpy.

Els programes fan la multiplicació de dues matrius de 2048x2048 elements, amb un total de 8.589.934.592 operacions.

Per a la realització del exercici necessitaràs:

- Tenir instal·lat el compilador de C (per defecte a Ubuntu)
- Tenir instal·lat un JDK
- Tenir instal·lat Python i la llibreria `numpy`


???+ pied-piper "Codi en C"
    ``` c linenums="1" title="matrix.c"
    --8<-- "snippets/matrix.c"
    ```

???+ example "Codi en Python"
    ``` py linenums="1" title="matrix.py"
    --8<-- "snippets/matrix.py"
    ```

???+ example "Codi en Java"
    ``` py linenums="1" title="Matrix.java"
    --8<-- "snippets/matrix.py"
    ```

## 2. Compilació i llançament dels programes

1. Compilar cada programa (si cal).
2. Executar 5 vegades cada programa.
3. Anotar els temps en un full de càlcul.

### Ordres bàsiques:

???+ example "Compilació i execució dels programes"
    ``` bash linenums="1" title="Bash"
    #C
    gcc MatrixMultiplication.c -o matrix
    ./matrix
    #Java
    javac MatrixMultiplication.java
    java MatrixMultiplication
    #Python
    python MatrixMultiplication.py
    ```

Anota els resultats i compara'ls. Torna a compilar els programes C de la següent forma:

???+ example "Compilació optimitzada en C"
    ``` bash linenums="1" title="bash"
    gcc -O2 MatrixMultiplication.c -o matrixO2
    ./matrix02
    gcc -O3 MatrixMultiplication.c -o matrixO2
    ./matrix03
    ```

## 3. Llibreria d'alt rendiment: ```numpy```
Torna a fer la prova amb el següent programa:

???+ example "Python amb numpy"
    ``` py linenums="1" title="matrixnp.py"
    --8<-- "snippets/matrixnp.py"
    ```