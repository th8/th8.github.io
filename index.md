## Programmeeropdracht paradigma's


Voor de programmeeropdracht paradigma's moet ik aantonen dat ik mijzelf een nieuwe programmeertaal kan aanleren in een ander paradigma dan ik gewend ben en mijn kennis daarbij delen met jou, mijn lezer. In deze blog behandel ik mijn weg bij het leren van de logische programmeertaal prolog en mijn poging tot het door deze taal laten oplossen van een nonogram.

### Een nonogram?

Ik kijk vaak over de schouder van mijn jongere zusje mee als zij weer bezig is met haar 'Japanse puzzel', waarvan ik door deze opdracht leerde dat zij [nonogrammen](https://nl.wikipedia.org/wiki/Nonogram) heten. Deze puzzel bestaat uit een grid met nummers langs de boven- en linkerkant die aangeven hoeveel blokjes er ingevuld moeten worden op een bepaalde regel, aan de speler de taak om het patroon te ontdekken en dit grid zo in te vullen op een manier die aansluit bij de nummers langs de rand.

Ik zie het plezier niet zo in zulke puzzels, ik krijg mijzelf er überhaupt niet toe gezet om mijn energie te steken in zulke puzzels. Een ideale taak dus om uit te besteden aan mijn computer, laat hem dat saaie denkwerk maar doen.

Van de toegestane talen leek prolog mij geschikt om deze puzzels voor mij op te gaan lossen. Mijn voorkennis van deze taal is dat je door middel van het opstellen van feiten en regels programmeert en zodoende vragen kunt stellen waarop jouw programma dan aan de hand van deze regels antwoorden geeft. Een puzzel is in essentie niet anders dan een setje regels en feiten die wij als mensen tot uitvoering moeten brengen om een resultaat te krijgen. De feiten in de vorm van cijfertjes langs de rand, en de regels die bepalen dat deze nummers iets betekenen voor het invullen van het grid van de puzzel, een betere match kan ik me niet voorstellen.

Daarom mijn idee om tot een prolog programma te komen dat een door [deze site](https://nl.puzzle-nonograms.com/) gegenereerde 5x5 nonogram kan oplossen. Als deze uitdaging te makkelijk blijkt kan ik de opdracht vermoeilijken door ook kleurennonogrammen te ondersteunen, waarbij rekening moet worden gehouden met verschillende kleuren voor de vakjes. En mocht deze opdracht te moeilijk blijken kan ik terugschalen door een enkel nummer te ondersteunen in de zijbar in plaats van meerdere nummers te ondersteunen.

### Hoe ga ik prolog leren?

Nu kan ik met een vaag idee dat prolog een taal van feiten en regeltjes is niet meteen een puzzeloplosprogramma maken. Vandaar dat ik de online cursus ['Learn Prolog Now!'](http://www.learnprolognow.org/index.php) heb uitgekozen om bekend te raken met de taal. Deze twaalfdelige cursus dekt alle onderdelen die op dit moment relevant klinken voor het oplossen van mijn puzzel, en bevat een goede hoeveelheid opgaven om te kunnen oefenen met prolog.

Als fervent gebruiker van JetBrains-IDE's werd ik echter wel teleurgesteld in het gebrek aan ondersteuning voor prolog in een van haar producten. Daarom heb ik na het bekijken van alle gedateerd uitziende software die voor het ontwikkelen van prolog bestaat gekozen voor de ['Prolog Development Tool'](https://sewiki.iai.uni-bonn.de/research/pdt/docs/start), een plugin voor Eclipse in samenwerking met [SWI-Prolog](https://www.swi-prolog.org/). Omdat dit de meest complete IDE-like ervaring was die ik kon vinden voor prolog.

---

## Hoofdstukken

1. [De bijtjes en de feitjes](bees.md) 
2. [Onder de motorkap](hood.md)
3. [Overmoed](attempt1.md)
4. [De missende lijst](list.md)
