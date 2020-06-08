## Programmeeropdracht paradigma's


Voor de programmeeropdracht paradigma's moet ik aantonen dat ik mijzelf een nieuwe programmeertaal kan aanleren in een ander paradigma dan ik gewend ben en mijn kennis daarbij delen met jou, mijn lezer. In deze blog behandel ik mijn weg bij het leren van de logische programmeertaal prolog en mijn poging tot het door deze taal laten oplossen van een nonogram.

### Een nonogram?

Ik kijk vaak over de schouder van mijn jongere zusje mee als zij weer bezig is met haar 'Japanse puzzel', waarvan ik door deze opdracht leerde dat zij [nonogrammen](https://nl.wikipedia.org/wiki/Nonogram) heten. Deze puzzel bestaat uit een grid met nummers langs de boven- en linkerkant die aangeven hoeveel blokjes er ingevuld moeten worden op een bepaalde regel, aan de speler de taak om het patroon te ontdekken en dit grid zo in te vullen op een manier die aansluit bij de nummers langs de rand.

Ik zie het plezier niet zo in zulke puzzels, ik krijg mijzelf er überhaupt niet toe gezet om mijn energie te steken in zulke puzzels. Een ideale taak dus om uit te besteden aan mijn computer, laat hem dat saaie denkwerk maar doen.

Van de toegestane talen leek prolog mij geschikt om deze puzzels voor mij op te gaan lossen. Mijn voorkennis van deze taal is dat je door middel van het opstellen van feiten en regels programmeert en zodoende vragen kunt stellen waarop jouw programma dan aan de hand van deze regels antwoorden geeft. Een puzzel is in essentie niet anders dan een setje regels en feiten die wij als mensen tot uitvoering moeten brengen om een resultaat te krijgen. De feiten in de vorm van cijfertjes langs de rand, en de regels die bepalen dat deze nummers iets betekenen voor het invullen van het grid van de puzzel, een betere match kan ik me niet voorstellen.

Daarom mijn idee om tot een prolog programma te komen dat een door [deze site](https://nl.puzzle-nonograms.com/) gegenereerde 5x5 nonogram kan oplossen. Als deze uitdaging te makkelijk blijkt kan ik de opdracht vermoeilijken door ook kleurennonogrammen te ondersteunen, waarbij rekening moet worden gehouden met verschillende kleuren voor de vakjes.

### Hoe ga ik prolog leren?

Nu kan ik met een vaag idee dat prolog een taal van feiten en regeltjes is niet meteen een puzzeloplosprogramma maken. Vandaar dat ik de online cursus ['Learn Prolog Now!'](http://www.learnprolognow.org/index.php) heb uitgekozen om bekend te raken met de taal. Deze twaalfdelige cursus dekt alle onderdelen die op dit moment relevant klinken voor het oplossen van mijn puzzel, en bevat een goede hoeveelheid opgaven om te kunnen oefenen met prolog.

Als fervent gebruiker van JetBrains-IDE's werd ik echter wel teleurgesteld in het gebrek aan ondersteuning voor prolog in een van haar producten. Daarom heb ik na het bekijken van alle gedateerd uitziende software die voor het ontwikkelen van prolog bestaat gekozen voor de ['Prolog Development Tool'](https://sewiki.iai.uni-bonn.de/research/pdt/docs/start), een plugin voor Eclipse in samenwerking met [SWI-Prolog](https://www.swi-prolog.org/). Omdat dit de meest complete IDE-like ervaring was die ik kon vinden voor prolog.

## Feiten en regels

Het eerste hoofdstuk van de cursus gaat in op de dingen die mij al bekend waren over prolog, namelijk het opstellen van feiten en regels, op welke basis je daarna jouw programma kunt bevragen. 

### De Knowledge Base

Het opstellen van deze feiten en regels doe je in een 'Knowledge Base', tijdens het maken van de opdrachten meer hierover. Wat hier opvalt is dat de syntax voor het opstellen van deze zaken sterk afwijkt van hoe dingen worden gedefinieert in object georienteerde talen. Hoewel elke taal enigsinds verschilt van syntax, zijn er voor elk verschil honderde overeenkomsten. Prolog heeft bij zijn fundering echter al dingen die erg afwijken zoals `:-` voor het aangeven van een regel, al zijn deze keuzes voor de syntax mogelijk eerder een product van de tijd waarin deze werd opgesteld dan inherent aan het afwijkende paradigma.

### De syntax

Wat verder aan bod komt zijn de syntax technische zaken zoals wat atoms, nummers, variabelen, etc. zijn. Deze doen denken aan zaken die ik leerde tijdens het maken van een parser voor een CSS-dialect. Belangrijk om te onthouden zijn dat variabelen altijd beginnen met een hoofdletter of underscore, terwijl atoms altijd beginnen met een kleine letter, zijn omringd door een `'`, of betaan uit andere speciale tekens. 

De feiten en regels die we opstellen in onze 'Knowledge Base' zijn complexe termen. Zij bestaan uit een 'functor' en zijn argumenten. Bijvoorbeeld een feit dat ik een programmeur ben: `programmer(thomas)` hierin is `programmer` de functor en atom `thomas` het argument van deze functor.

Omdat de functor van complexe termen vaker kunnen voorkomen is het ook belangrijk om de zogenoemde 'arity' te weten. De arity komt neer op hoeveel argumenten een complexe term kan hebben. Om deze complexe termen uit elkaar te houden wordt de arity toegevoegd aan de naam van zo'n term, hierdoor zal de `programmer(thomas)` met een arity van 1 in de 'context view' van mijn IDE dus `programmer/1` zijn, en bijvoorbeeld `loves(jan, hans)` vertalen naar `loves/2`.

Dit lijkt enorm veel op 'function overloading' in object georienteerde talen, waarbij de arity lijkt te dienen ter verduidelijking bij gebrek aan een function signature, zoals bijvoorbeeld `public boolean loves(Person person1, Person person2)` in Java.
