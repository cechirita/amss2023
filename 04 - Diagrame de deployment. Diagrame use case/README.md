# Diagrame de deployment. Diagrame use case

## Diagrame de deployment

Diagramele de deployment reprezintă legăturile dintre produsele software și hardware-ul pe care vor rula acestea. 

Elementele software (componente, clase, cod compilat) sunt reprezentate ca artefacte (*artifacts*): dreptunghiuri ce conțin numele elementelor și o iconiță sub formă de fișier în colțul din dreapta-sus. 

<img alt="artefact" src="images/a1.png" width="200px">

Artefactele pot avea proprietăți/atribute și operații.

<img alt="artefact" src="images/a2.png" width="400px">

Artefactele reprezintă de regulă tipuri de elemente. Este util să reprezentăm și instanțe ale artefactelor -- subliniind numele elementelor (e.g. copii fizice ale unor fișiere cu cod). Artefactele sunt de regulă manifestări (*manifestation*) are altor elemente UML (componente, de exemplu). Reprezentăm acest lucru prin linii punctate cu eticheta `<<manifest>>`.

Artefactele sunt desenate de obicei în interiorul unor *noduri* (containere) ce reprezintă elemente hardware ce pot găzdui/executa un artefact (dispozitiv, mediu de execuție etc.). Nodurile sunt reprezentate ca paralelipipede dreptunghice etichetate cu nume scrise îngroșat. 

<img alt="node" src="images/n1.png" width="400px">

Un mediu de execuție (*execution environment*) este un nod specializat care găzduiește un tip anume de artefacte. Este de așteptat ca un mediu de execuție să ofere servicii specifice artefactelor găzduite (e.g. o pagină web are nevoie de anumite funcționalități de la un server web: load balancing, compilatoare dedicate, etc.). Putem reprezenta acest lucru prin crearea unui stereotip (e.g. `<<Web Server>>`) și folosirea lui ca nume al unui nod în interiorul unui nod hardware-based.

Communicarea între noduri este reprezentată sub formă de muchii denumite *communication paths*. Comunicarea fiind de regulă bi-direcțională, nu avem nevoie de săgeți, doar de linii (continue). 

<img alt="communication path" src="images/cp.png" width="500px">

Când asociem un artefact cu o țintă de deployment (*deployment target*), spunem că îi facem *deploy*. Reprezentăm deploymentul desenând un artefact în interiorul unui nod, cu o săgeată cu linie punctată și eticheta `<<deploy>>`, sau listând toate artefactele deployed într-un nod.

<img alt="deploy" src="images/d1.png" width="400px">
<img alt="deploy" src="images/d2.png" width="400px">

Pot fi folosite și *specificații de deployment* (liste de proprietăți) pentru detalierea modului în care un artefact trebuie deployed într-un nod țintă.

Diagramele de deployment sunt folosite mai ales de dev ops și administratori de sistem ca să descrie:

- modelarea unei topologii de rețea 
- modelare sistemelor distribuite 
- sisteme de forwards și reverse engineering

### Exemplu

![Exemplu diagrama deployment](https://online.visual-paradigm.com/images/tutorials/deployment-diagram-tutorial/04-deployment-diagram-node-and-artifacts.png)

## Diagrame use case 

### Cazuri de utilizare (use case)

Cazurile de utilizare (use cases) sunt o metodă de a surprinde funcționalitățile și cerințele unui sistem software. Constau într-o listă de acțiuni sau evenimente care definesc interacțiunile dintre un rol (*actor*; persoană sau lucru/sistem extern) și un sistem pentru a îndeplini un scop.

Sunt folosite:

- ca instrument de modelare a comportamentului în UML
- în documentarea cerințelor de sistem (software requirements specifications -- SRS), ca metodă alternativă de înregistrare a cerințelor funcționale
- în dezvoltarea software de tip agile
- în object oriented software engineering

#### Use case = text + diagramă

Definiția unui caz de utilizare în UML presupune:

- o funcționalitate (a unui sistem, a unei componente, a unei clase) cu nume (descriere scurtă a funcționalității)
- actorii care invocă funcționalitatea 
- opțional: elemente responsibile de implementarea cazurilor (subiecți)

Reprezentăm un caz de utilizare (o funcționalitate) folosind un oval cu numele funcționalității. 

<img alt="use case" src="images/uc1.png" width="100px">
<img alt="use case" src="images/uc2.png" width="150px">
<img alt="use case" src="images/uc3.png" width="200px">

### Actor

Un use case trebuie inițiat de *cineva* ori *ceva* din afara domeniului cazului de utilizare: un actor. Acesta nu trebuie să fie o persoană sau un utilizator; un stimul extern poate declanșa un caz de utilizare de asemenea (e.g. un system clock e adesea reprezentat ca un actor ce declanșează un caz de utilizare la un anumit timp sau un anumit interval de timp).

Actorii pot fi reprezentați în mai multe feluri în UML. Cea mai comună este cea a unui *stick figure* însoțit de numele actorului.

<img alt="actor" src="images/actor.png" width="100px">

Putem reprezenta un actor și folosind notația cu clasificatori: un dreptunghi cu numele actorului și cuvântul-cheie `<<actor>>`.

<img alt="actor" src="images/actor2.png" width="200px">

Putem folosi însă și desene custom pentru a distinge între tipurile de actori. De exemplu, putem reprezenta un sistem de baze de date extern folosind o iconiță de bază de date și un administrator de sistem folosind un stick figure.
 
![alternative-icons-for-actors](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:0596007957/files/httpatomoreillycomsourceoreillyimages187496.png)

### Asocieri actor/use case

Actorii sunt asociați unuia sau mai multor cazuri de utilizare. O relație între un actor și un use case poate indica că actorul inițiază cazul de utilizare, că use case-ul oferă actorului niște rezultate, ori ambele. De regulă, actorii sunt reprezentați în partea stânga a diagramei, iar cazurile de utilizare în partea dreaptă. 

Deși nu fac parte din specificația oficială UML, putem folosi și săgeți (direcționale) în relațiile (liniile) de asociere, pentru a indica cine inițiază comunicarea. Săgețile nu restricționează însă neapărat direcția de circulație a informației; doar arată cine inițiază și cine e receiverul în comunicare.

### System boundaries 

Limitele unui sistem pot fi identificate prin izolarea funcționalităților unui subiect anume. Orice nu este îndeplinit de subiect este considerat în afara limitelor sistemului și devine actor. Tehnica este utilă în determinarea/asignarea responsabilităților în etapa de design a unui sistem. Reprezentăm limitele folosind un dreptunghi adnotat cu numele sistemului în partea de sus.

![boundaries](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:0596007957/files/httpatomoreillycomsourceoreillyimages187502.png)

### Generalizare

Putem folosi relații de generalizare între actori și cazuri de utilizare. De exemplu, pentru a reprezenta faptul că un actor poate executa toate sarcinile unui alt actor (abstract): desenăm o săgeată (cu capăt gol) de la actorul mai specific la actorul mai general pentru a indica ca poate iniția și funcționalitățile asociate acestuia, pe lângă cele asociate lui. 

<img alt="use case" src="images/admin.png" width="400px">

Cazurile de utilizare pot fi generalizate de asemenea. Generalizarea se folosește pentru a descrie o cerință funcțională high-level a unui sistem fără a intra în detalii. 

<img alt="use case" src="images/uc4.png" width="300px">

### Incluziunea cazurilor de utilizare

Funcționalitățile comune pot fi extrase din mai multe cazuri de utilizare și incluse în cazuri de utilizare shared. Un caz de utilizare inclus nu este regulă complet de sine stătător (precum clasele abstracte în OOP). E.g. use case "payment" vs. use case "pay with paypal"/"pay with card". 

Incluziunea este reprezentată cu săgeți cu linie punctată (dependență) și etichete cu cuvântul-cheie `<<include>>`.

### Extinderea cazurilor de utilizare

În anumite condiții, un caz de utilizare poate extinde un altul pentru a oferi funcționalități extra. Diferența între incluziune și extindere constă în faptul că un caz de utilizare extins este un caz de utilizare valid în sine.

<img alt="extindere use case" src="images/ext1.png" width="400px">
<img alt="extindere use case" src="images/ext2.png" width="400px">

### Time for lunch?

Ce constituie un bun caz de utilizare și ce nu? 
Regulă nescrisă pentru evaluarea complexității: ne întrebăm dacă utilizatorul "poate merge să ia prânzul" după completarea cazului de utilizare (un scop cu dimensiune rezonabilă a fost atins de inițiator). 

### Exercițiu 

Modelarea interacțiunilor utilizatorilor cu pagina YouTube folosind diagrame use case.

## Cu ce desenăm diagrame?

1. [app.diagrams](https://app.diagrams.net/)
2. [Lucidchart](https://www.lucidchart.com)
3. [Mermaid](http://mermaid.js.org/), 4 Github, a la Markdown.
4. [Visual Paradigm](https://online.visual-paradigm.com/diagrams/solutions/free-class-diagram-tool/)

## Bibliografie

 - *UML 2.0 in a Nutshell*, Dan Pilone, Neil Pitman - Chapter 6, Deployment Diagrams & Chapter 7, Use Case Diagrams
 - *Using UML*, Perdita Stevens, Rob Pooley - Chapter 7, Essentials of use case models & Chapter 8, More on use case models

