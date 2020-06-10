## De missende lijst

Met mijn eerste poging om nonogrammen in het achterhoofd ging ik nadenken over de kennis die ik nodig zou hebben om mijn nonogramoplosser te upgraden zodat deze voldeed aan mijn doel. Ik kwam al snel tot de conclusie dat ik daarvoor zou moeten leren hoe lijsten in prolog werken, om zo rijen en kolommen met meerdere nummers als hint te ondersteunen.

Ik sloeg hiervoor hoofdstuk drie van mijn cursus over, aangezien recursie in prolog sterk lijkt op recursie zoals ik het ken uit java.

### Prop alles er maar in

Wat mij allereerst opviel aan lijsten in prolog is dat je er van alles samen in kan stoppen. In object georienteerde talen definieer je gewoonlijk het type/generic die in de lijst of array komt. In prolog kun je alles samen gooien in een lijst; atoms, nummers, termen en zelfs andere lijsten.

### Kop en staart

Dan het tweede verschil met wat ik gewend was. Lijsten hebben een kop en een staart, die je doormiddel van de `|` operator van elkaar kan scheiden. Lijsten in prolog zijn naar mijn impressie volledig gebouwd op het gebruik in recursieve functies, door de head te gebruiken in de huidige functie en de tail door te geven aan de recursieve call.

Ook bijzonder is de lege lijst. Hoewel deze in java vaak voor heibel zorgt is deze in prolog juist van essentieel belang. Omdat een lege lijst niet kan worden gescheiden met de pipe-operator zorgt deze als het ware voor een basecase van je recusieve functie.

### Verdubbeling

Om te oefenen met mijn nieuwe lijstkennis licht ik opdracht 4.6 van de cursus uit. Het is hierbij de bedoeling dat je een predicaat `twice/2` maakt waarin je een lijst stopt, welke dan op zijn tweede argument een lijst maakt met elk element uit de eerste lijst twee keer.

De uiteindelijke code is hiervoor alsvolgt:
```prolog
twice([], []).
	
twice([In | Tail], [In, In | Out]) :-
	twice(Tail, Out).
```
Om tot deze oplossing te komen heb ik erg veel geëxperimenteerd. Door mijn OO-mindset was ik constant bezig met het meegeven van `[In, In | Out]` aan de recusieve twice, in plaats van dat ik het bij de verwachtte inputkant toevoegde. Uiteindelijk heb ik de oplossingen van deze opgave moeten bekijken om tot dit antwoord te komen omdat ik was vastgelopen. Toen ik eenmaal zag dat de kop van de `In` lijst samen met de `Out` kwamen viel alles op zijn plek.

Het blijft moeilijk niet de jaren lange patronen vanuit java toe te passen, daar zou je immers geen manipulatie van input argumenten toepassen om tot een oplossing te komen.

---

#### [Terug naar de hoofdpagina](index.md)
