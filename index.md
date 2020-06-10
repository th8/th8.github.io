## Programmeeropdracht paradigma's


Voor de programmeeropdracht paradigma's moet ik aantonen dat ik mijzelf een nieuwe programmeertaal kan aanleren in een ander paradigma dan ik gewend ben en mijn kennis daarbij delen met jou, mijn lezer. In deze blog behandel ik mijn weg bij het leren van de logische programmeertaal prolog en mijn poging tot het door deze taal laten oplossen van een nonogram.

### Een nonogram?

Ik kijk vaak over de schouder van mijn jongere zusje mee als ze weer bezig is met haar 'Japanse puzzel', waarvan ik door deze opdracht leerde dat ze [nonogrammen](https://nl.wikipedia.org/wiki/Nonogram) heten. Deze puzzel bestaat uit een grid met nummers langs de boven- en linkerkant die aangeven hoeveel blokjes er ingevuld moeten worden op een bepaalde regel, aan de speler de taak om het patroon te ontdekken en dit grid zo in te vullen op een manier die aansluit bij de nummers langs de rand.

Ik zie het plezier niet zo in zulke puzzels, ik krijg mijzelf er überhaupt niet toe gezet om mijn energie te steken in zulke puzzels. Een ideale taak dus om uit te besteden aan mijn computer, laat hem dat saaie denkwerk maar doen.

Van de toegestane talen leek prolog mij geschikt om deze puzzels voor mij op te gaan lossen. Mijn voorkennis van deze taal is dat je door middel van het opstellen van feiten en regels programmeert en zodoende vragen kunt stellen waarop jouw programma dan aan de hand van deze regels antwoorden geeft. Een puzzel is in essentie niet anders dan een setje regels en feiten die wij als mensen tot uitvoering moeten brengen om een resultaat te krijgen. De feiten in de vorm van cijfertjes langs de rand, en de regels die bepalen dat deze nummers iets betekenen voor het invullen van het grid van de puzzel, een betere match kan ik me niet voorstellen.

Daarom mijn idee om tot een prolog programma te komen dat een door [deze site](https://nl.puzzle-nonograms.com/) gegenereerde 5x5 nonogram kan oplossen. Als deze uitdaging te makkelijk blijkt kan ik de opdracht vermoeilijken door ook kleurennonogrammen te ondersteunen, waarbij rekening moet worden gehouden met verschillende kleuren voor de vakjes. En mocht deze opdracht te moeilijk blijken kan ik terugschalen door een enkel nummer te ondersteunen in de zijbalk in plaats van meerdere nummers.

### Hoe ga ik prolog leren?

Nu kan ik met een vaag idee dat prolog een taal van feiten en regeltjes is niet meteen een puzzeloplosprogramma maken. Vandaar dat ik de online cursus ['Learn Prolog Now!'](http://www.learnprolognow.org/index.php) heb uitgekozen om bekend te raken met de taal. Deze twaalfdelige cursus dekt alle onderdelen die op dit moment relevant klinken voor het oplossen van mijn puzzel, en bevat een goede hoeveelheid opgaven om te kunnen oefenen met prolog.

Als fervent gebruiker van JetBrains-IDE's werd ik echter wel teleurgesteld in het gebrek aan ondersteuning voor prolog in een van haar producten. Daarom heb ik na het bekijken van alle gedateerd uitziende software die voor het ontwikkelen van prolog bestaat gekozen voor de ['Prolog Development Tool'](https://sewiki.iai.uni-bonn.de/research/pdt/docs/start), een plugin voor Eclipse in samenwerking met [SWI-Prolog](https://www.swi-prolog.org/). Omdat dit de meest complete IDE-like ervaring was die ik kon vinden voor prolog.

---

## Hoofdstukken

In de onderstaande hoofdstukken beschrijf ik mijn leerproces en meerdere pogingen om tot een oplossing van mijn doelstelling te komen:

1. [De bijtjes en de feitjes](bees.md) 
2. [Onder de motorkap](hood.md)
3. [Overmoed](attempt1.md)
4. [De missende lijst](list.md)
5. [Er zijn fouten in de oplossing van de puzzel](attempt2.md)


## Afsluitend

Het voelt een beetje zuur, ik had graag mijn originele doelstelling behaald en op de momenten dat ik niet bezig ben met de blog blijven er verschillende ideeën opkomen wat ik nog zou kunnen proberen, die al net zo snel weer worden ontkracht als ik ze verder uitdenk.

Het was interessant om mij te verdiepen in prolog en het logische paradigma waar het toe behoort. Ik zie echter nog altijd niet erg goed hoe praktisch de toepassing van deze taal is voor minder puzzelachtige problemen. Ik heb in mijn zoektocht gelezen dat de taal vaker toepassing vind in het uitvoeren van een specifiek concept binnen een ander programma, zoals AI's in een computerspel. Zoiets ingewikkeld produceren is nog een ver van mijn bed show.

Ik blijf het gevoel hebben dat ik te veel gebrand ben op het object georiënteerde paradigma om echt goede logische oplossingen te kunnen visualiseren. Ik blijf terugvallen in oude denkpatronen zoals de verantwoordelijkheid van een functie in haar body leggen in plaats van een regel en de proof-search haar eigen werk te laten doen, zoals te zien was bij de lijstopdracht.

Ik denk niet dat ik snel terug zal keren naar prolog als ik een probleem heb. Ik denk dat ik in de tijd die het eerste hoofdstuk mij kostte een prima nonogramoplosser had kunnen maken in java. Daarnaast woog het plezier van nieuwe concepten leren niet op tegen de frustratie en hoofdpijn oproepende moeite die het mij kostte om zo anders te denken over programmeren. 
