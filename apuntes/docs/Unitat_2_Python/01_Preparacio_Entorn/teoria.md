# 1. Preparació de l'entorn

## 1. Preparant l'Entorn en Python

Abans de començar a programar en Python hem de preparar la nostra màquina per a tal tasca. Està clar que podem tenir un superordenador i instal·lar tot al complet, però al poc de temps ens adoanrem que perdrem el control del que tenim. Varies versions dels intèrprets de Python (2 o 3) i dins de la 3, 3.7, 3.9, etc... Ademés tenim tota la col·lecció de llibreries que podem instal·lar amb pip per a fer-les servir al nostre programa. Espai i més espai.. versions i més versions.

Per a evitar aquestes instal·lacions massives de incloure-ho tot, ens ajuden els gestors de dependències, com els que ja coneixereu ```Maven```, ```Ant```, ```Gradle``` per a ```Java```, per exemple el Node Package Manager de ```node.js```. Els gestors de dependencies ens permeten crear una mena d'entorns aïllats on podem indicar quines llibreries i dependències ens calen per al nostre projecte. Aquestes llibreries no depenen del sistema anfitrió, i a més a més, permeten una exportació fàcil, ja que no hem de copiar ni d'exportar les llibreries, ja que al destí s'agafaran de nou.

En resum, els entorns virtuals ens permeten:

- Organitzar i tindre millor controlades totes les llibreries
- Estabilitat, ja que sempre tenim la llibreria exacta del nostre entorn i no la de la màquina real
- Version distintes


???+ success "Atenció"
    Recomanem per tant, crear un entorn virtual per a cadascun dels projectes que desenvoluparem.

## 2. Instal·lació de Python 3

### 2.1. Instal·lar Python 3

=== "Windows"

    1. Ves a [https://www.python.org/downloads/](https://www.python.org/downloads/) i descarrega l'última versió de Python 3.

    2. Durant la instal·lació, assegura't de seleccionar l'opció **"Add Python to PATH"**.

    3. Un vegada instal·lat, obre un terminal i comprova la versió amb:

    ```bash
    python --version
    ```

=== "macOS"

    1. Si tens Homebrew:

    ```bash
    brew install python
    ```

    2. Comprova amb:

    ```bash
    python3 --version
    ```

=== "Linux (Ubuntu/Debian)"

    ```bash
    sudo apt update
    sudo apt install python3 python3-venv python3-pip
    python3 --version
    ```
## 2.2. Introducció a **venv**: Creació d'entorns virtuals a Python

### 2.2.1. Què és un entorn virtual?

Un entorn virtual és una carpeta especial que conté una còpia de Python i de totes les biblioteques que utilitzarem en un projecte. D'aquesta manera, mantenim els nostres projectes aïllats, evitant problemes de compatibilitat entre versions de Python i biblioteques.

### 2.2.2. Com crear un entorn virtual amb venv

1. Crear l'entorn virtual:

Navega fins a la carpeta del projecte i crea l'entorn virtual amb: 

```bash linenums="1" title="Bash"
    python3 -m venv nom_entorn
```
```nom_entorn``` es el nom que donem a l'entorn (pots posar, per axemple, ```.venv``` o ```env```).

2. **Activar l'entorn virtual**:

=== "Windows"

    ```bash linenums="1" title="Bash"
    .\nom_entorn\Scripts\activate
    ```

=== "macOS/Linux"

    ```bash linenums="1" title="Bash"
    source nom_entorn/bin/activate
    ```

Quan l'entorn estigua actiu, veuràs el nom de l'entorn entre parèntesis abans del teu prompt.

3. **Instalar paquets dins del entorn**:

Una vegada activat l'entorn, podem instal·lar paquets amb ```pip```, aquets paquets només s'instal·laran dins del entorn:

```bash linenums="1" title="Bash"
pip install nom_del_paquet
```

4. **Desactivar l'entorn virtual**:

Una vegada hem acabat, podem desactivar l'entorn amb:

```bash linenums="1" title="Bash"
deactivate
```

### 2.2.3. **Beneficis d'utilitzar entorns virtuals**:

- Separar les dependències entre projectes.
- Evitar problemes de compatibilitat entre versions de Python i paquets.
- Facilitar la reproducció d'entorns en altres màquines.

### 2.2.4. Exemple pràctic:

1. Crear un projecte nou:
    ```bash linenums="1" title="Bash"
    mkdir projecte
    cd projecte
    python3 -m venv env
    ```
2. Activar l'entorn:
    ```bash linenums="1" title="Bash"
    source env/bin/activate  # O \env\Scripts\activate a Windows
    ```
3. Instal·lar un paquet, com ara ```requests```:
   ```bash linenums="1" title="Bash"
   pip install requests
   ``` 
4. Desactivar l'entorn quan acabem: 
   ```bash linenums="1" title="Bash"
   deactivate
   ``` 

# 3. Jupyter notebooks

Els Jupyter Notebooks són una eina fonamental en el món de la programació i la ciència de dades que ha revolucionat la manera en què els professionals treballen i col·laboren en l'anàlisi de dades, el desenvolupament de programari i la recerca científica. Aquesta plataforma, que es va originar com a derivació del projecte ```IPython```, ofereix un entorn interactiu que combina codi, text, imatges i gràfics en un únic document web, permetent als usuaris crear i compartir continguts dinàmics i ben documentats.

Un dels elements més destacats dels Jupyter Notebooks és la seva capacitat d'integrar codi executable (Python) amb text explicatiu (Markdown), la qual cosa facilita la creació de documents que expliquen i demostren pas a pas els processos analítics i els resultats obtinguts. Aquesta funcionalitat fa que sigui una eina ideal per a científics de dades, enginyers, estudiants i professionals que volen comunicar les seves idees i resultats de manera clara i efectiva.

A més de ser utilitzats per a l'exploració de dades i l'anàlisi estadística, els Jupyter Notebooks també són àmpliament emprats en l'aprenentatge de programació i la docència, ja que permeten als estudiants escriure, provar i comprendre el codi en un entorn interactiu i amigable.

Per començar a desenvolupar amb Jupyter Notebooks, hauràs d'instal·lar algunes eines i dependències al teu sistema. Aquí tens els passos bàsics per a la instal·lació:

1. **Python**: Els Jupyter Notebooks són més comunsment utilitzats amb Python. Assegura't de tenir Python instal·lat al teu sistema. És recomanable utilitzar Python 3, ja que Python 2 ja no rep suport.

2. **Gestor de paquets de Python**: Si no ho tens ja instal·lat, és aconsellable utilitzar un gestor de paquets de Python com ```pip``` o ```conda```. Aquestes eines et permetran instal·lar i gestionar les llibreries i paquets necessaris.

3. **Jupyter Notebook**: Pots instal·lar Jupyter Notebook executant la següent comanda a la terminal utilitzant ```pip```:

```bash linenums="1" title="Bash"
pip install notebook
```

Si utilitzes l'entorn de conda, també pots instal·lar-lo amb:

```bash linenums="1" title="Bash"
conda install notebook
```

Un vegada instal·lats tots els components, ja estem preparats per començar a treballar amb Jupyter Notebooks. Pots iniciar un servidor de Jupyter Notebook amb la ordre:

```bash linenums="1" title="Bash"
jupyter notebook
```

Aquesta ordre obrirà el teu navegador web amb l'entorn de Jupyter Notebook, on podràs crear nous fitxers de notebook, obrir-ne de existents i començar a escriure codi i text interactius.

Recorda que potser també voldràs utilitzar un entorn virtual (com virtualenv o conda) per gestionar les dependències i els paquets específics del teu projecte, especialment si treballes en diversos projectes amb versions diferents de les llibreries.

# 4. Jupyter i Visual Studio Code

Si prefereixes utilitzar Visual Studio Code (VS Code) per desenvolupar amb Jupyter Notebooks, també pots fer-ho. VS Code és una excel·lent opció per als desenvolupadors de Python i ofereix una integració nativa amb Jupyter que facilita la creació i l'execució de notebooks. Aquí tens com fer-ho:

1. **Instal·la Visual Studio Code**: Si encara no tens VS Code instal·lat, descarrega'l i instal·la'l des del lloc web oficial.

2. **Instal·la l'extensió de Jupyter**: Una vegada obert VS Code, ves a l'Explorador d'Extensions (Extensions Marketplace) fent clic a l'ícona d'extensions a la barra lateral esquerra o amb ```Ctrl+Shift+X```. Cerca "Jupyter" i instal·la l'extensió "Python" que ofereix Microsoft. Aquesta extensió proporciona suport complet per als Jupyter Notebooks.

3. **Crea o obre un Jupyter Notebook**: Des de VS Code, pots crear un nou Jupyter Notebook fent clic a l'opció "Create new Jupyter Notebook" a la vista d'Explorer. També pots obrir notebooks existents fent clic amb el botó dret sobre ells i seleccionant "Open with Jupyter Notebook."

4. **Selecciona l'entorn de Python**: VS Code permet gestionar entorns virtuals amb l'extensió "Python" i pots seleccionar l'entorn que vulguis utilitzar per al teu notebook.

5. **Desenvolupa amb Jupyter Notebooks**: Un cop hagis creat o obert un notebook, podràs escriure codi, text i afegir cel·les de manera similar a com ho faries amb l'entorn de Jupyter Notebook independent. Pots executar les cel·les mitjançant les opcions a la barra d'eines o amb atajos de teclat.

6. **Gestiona les extensions**: VS Code ofereix moltes extensions útils per a la ciència de dades i l'anàlisi de dades. Pots explorar i instal·lar extensions addicionals des de l'Explorador d'Extensions.

Aquesta integració de Jupyter a Visual Studio Code ofereix una experiència de desenvolupament completa i molt potent per als usuaris de Python que vulguin treballar amb notebooks i codi en un mateix entorn.

# 5. Google Colab

Google Colab (abreviació de Colaboratory) és una plataforma en línia que permet executar Jupyter Notebooks directament al núvol, sense necessitat de configurar res al teu propi sistema. És una excel·lent opció si vols treballar amb Jupyter Notebooks sense preocupar-te de la instal·lació d'entorns i llibreries al teu propi dispositiu. Aquí tens com fer servir Google Colab:

1. **Accedeix a Google Colab**: Obre el teu navegador web i accedeix a [Google Colab](https://colab.research.google.com/). Hauràs d'iniciar sessió amb el teu compte de Google si encara no ho has fet.

2. **Crea un nou notebook o importa-ne un**: Pots crear un nou notebook fent clic a "File" > "New notebook" o importar un notebook existent des del teu Google Drive o des d'un enllaç a GitHub fent servir les opcions disponibles a la vista "File".

3. **Treballa amb el teu notebook**: Un vegada has creat o importat un notebook, pots escriure codi, text, i executar cel·les com ho faries amb un Jupyter Notebook convencional. Utilitza les cel·les de codi i text per a la teva anàlisi o projecte.

4. **Entorns i llibreries**: Google Colab ofereix un entorn de Python prèviament configurat que inclou moltes llibreries comunes per a la ciència de dades (com NumPy, pandas, Matplotlib, etc.). Si necessites instal·lar altres llibreries, pots fer-ho executant comandes pip directament en una cel·la (per exemple, ```!pip install numpy```).

5. **Guarda el teu treball**: Pots desar el teu notebook a Google Drive o descarregar-lo localment mitjançant l'opció "File" > "Save" o "File" > "Download .ipynb."

6. **Comparteix i col·labora**: Google Colab et permet compartir els teus notebooks amb altres persones perquè puguin veure i editar el teu treball en temps real. Pots compartir mitjançant enllaços o afegir col·laboradors directament a través de les opcions de compartició.

Google Colab és una eina excel·lent per als projectes de ciència de dades i l'aprenentatge automàtic que es volen executar en un entorn de computació més potent que el teu dispositiu local o per a la col·laboració en línia amb altres persones. És una opció molt popular a la comunitat de la ciència de dades i és gratuït per a ús personal.

# 6. Estructura d’un programa en Python

Un programa en Python te una estructura molt simple, si ho comparm en altres llenguatges de programació; simplement hem d'escriure les nostres linies de codi i ja està, però pot tenir més coses

Qualsevol programa escrit en Python té la següent estructura: 

```bash linenums="1" title="Estructura"
[Descripció del programa]
[Directives]
[Importació de Libreria]
[Definició de classes]
[Funcions]
Entrada de dades
Processament de dades
Sortidad de dades
```

Els claudàtors indiquen que eixos apartats són opcionals. Per tant, veiem que l’única part necessària en un programa és l'entrada, el processament i la sortida de dades, com en qualssevol algorisme. Notar que en Python tots aquests poden canviar la posició. Vejam uns exemples i els analitzem.

El més simple, mostra un missatge per pantalla:

```py linenums="1" title="Python"
print("Hola món")
```

Altre una mica més complet:

```py linenums="1" title="Python"
import time

def areaRectangle(base,altura):
    return base*altura

base=int(input("Dis-me la base del rectangle: "))
altura=int(input("Dis-me l'altura del rectangle: "))
time.sleep(2)   # Espera dos segons

area=areaRectangle(base,altura)

print("L'area del rectangle és " + str(area))
```

Comentaris:

- Les 3 primeres línies sob una descripció del que fa el programa. Son comentaris, que no s'executen
- Al ```import``` indiquem que necessitem una llibreria. Això es veurà més endavant, però les llibreries són un conjunt de funcions que ja venen implementades i les podem fer servir als nostres programes. La funció que farem servir és ```time.sleep()``` que fa que el programa es pause durant una quantitat de segons.
- Desprès tenin la definició d'una funció, que comença amb la paraula reservada ```def```. Notar que tot el que pertany a la funció està indentat una tabulació (al nostre cas sols la instrucció del ```return```).
- Desprès ja tenim el nostre programa pròpiament dit:
    - Les línies no tenen cap indentació (pegades a l'esquerre)
    - La primera part és la que l'algorisme ha d'aconseguir la informació. En aquest cas a preguntem a l'usuari mitjançant input.
    - La segona part és el fer el càlcul. Pot veure's que es crida a la funció que hem definit anteriorment
    - Finalment mostrem a l'usuari el resultat (print).

# 7. Noms i paraules reservades en Python

Nosaltres per a programar, com hem vist abans, li hem posat nom a les variables i funcions. Per a posar nom a les variables hem de complir unes regles, que tenen tots els llenguatges de programació:

1. Són una combinació de lletres minúscules [a..z], majúscules [A..Z], dígits [0..9] i el caràcter subratllat[_].
2. No poden començar amb dígit.
3. Poden contenir accents i altes caràcters (ñ,ç,...)
4. No poden ser paraules reservades o keywords del sistema (veure taula a continuació)
5. No poden haver símbols especials ni operadors [!, @, #, $, %, ...] etc.
6. Poden tenir qualsevol longitud

Paraules reservades:

| False  | class    | finally | is       | return |
| ------ | -------- | ------- | -------- | ------ |
| None   | continue | for     | lambda   | try    |
| True   | def      | from    | nonlocal | while  |
| and    | del      | global  | not      | with   |
| as     | elif     | if      | or       | yield  |
| assert | else     | import  | pass     |        |
| break  | except   | in      | raise    |        |

Existeixen algunes més, com els tipus de dades (int, float, str, complex, etc). La facilitat és que els editors ens colorejen les paraules reservades, llavors sabrem que no les podem utilitzar per als nostres identificadors.

Les variables són els llocs on es guarda la informació. Poden ser de distints tipus, segons el lloc on es fan servir i des d'on es poden accedir. Una primera distinció és entre globals i locals:

- Les globals són aquelles que es creen fora de qualssevol funció i, per tant, són accessibles des de qualsevol punt del fitxer o programa.
- Les locals són les que es creen dins d’alguna funció i, per tant, només són accessibles des de les instruccions de dins d’eixa funció. Dins de una funció es pot accedir a les variables locals seues, així com a les variables globals
- Les variables de classe són com les variables locals a les funcions. S'estudiaràn dins de la POO

# 8. Comentaris

Els comentaris, com ja s'ha dit abans, són sentències les quals no s'executen, però serveixen per a poder entrendre i recordar què voliem fer dins del nostre codi. Si escrivim un codi, i el tornem a revisar al cap d'unes setmanes, segur que no recordem certes coses. L'ús de comentaris ens ajudarà a recordar.

També servieix quan altre programador ens revisa el nostre codi poder entrendre el que voliem fer.

## 8.1. Tipus de comentaris

- D'una línia, venen precedits pel caràcter coixinet #
- De més d'una línia, quan tanquem diverses línies entre dos parelles de tres cometes simples '''
- De documentació docstring, són una línia o línies de text intercalades al principi d'un mòdul, mètode, classe o funció. Pot ser:
    - Línia simple: com per exemple ```'Documentació.'```
    - Línia múltiple: tancada entre tres parelles de cometes dobles ```"""```

```py linenums="1" title="Python"
import time
# declarem una funció
def areaRectangle(base,altura):
    """
    Aquest funció calcula el àrea d'un rectangle
    Paràmetres:
        base -> La base del rectangle
        altura -> La altura del rectangel
    Errors: 
        No implentat
    """
    return base*altura

def areaQuadrat(base):
    'Calcula el area  de un quadrat de costat pasat.'
    return base**2

#demanem les dades a l'usuari
base=int(input("Dis-me la base del rectangle: "))
altura=int(input("Dis-me l'altura del rectangle: "))
time.sleep(2)   # Espera dos segons

area=areaRectangle(base,altura)
#mostrem el resultat
print("L'area del rectangle és " + str(area))

area=areaQuadrat(base)
#mostrem el resultat
print("L'area del quadrat és " + str(area))
```
# 9. Delimitadors

Són símbols especials que permeten al compilador separar i reconéixer les diferents unitats sintàctiques del llenguatge. En molts llenguatges de programació es fa servir un ```;``` (C i en Java ) com a finalitzador, però ```Python``` fa servir el bot de línia. De tota manera indiquem els més habituals per a tots els llenguatges.

| DELIMITADOR | NOM        | UTILITAT                                                |
| ----------- | ---------- | ------------------------------------------------------- |
| ,           | Separador  | Separar els elements d’una llista                       |
| ( )         | Parèntesis | Agrupar operacions i per als paràmetres de les funcions |
| [ ]         | Claudàtors | Per als vectors, llistes i demés                        |
