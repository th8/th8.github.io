## Onder de motorkap

In het tweede hoofdstuk van de cursus duik ik onder de motorkap van prolog. Hier leer ik over unification van prolog en hoe het zoeken naar oplossingen in prolog werkt.

### Unificatie

Ik bespaar de details over de unificatiestrategie van prolog, want anders wordt dit snel een vertaling van de Learn Prolog Now cursus. Wat mij opvalt is hoe unificatie van prolog in zekere zin lijkt op het met `==` vergelijken van twee objecten in Java. Aan de ene kant is prolog een stuk minder streng bij het unificeren van objecten, zo kan 'hans' = X worden gezien als waar omdat er niks is dat tegenspreekt dat X verenigbaar is met 'hans'.

[Gelukkig is prolog niet zo laks als javascript](https://youtu.be/et8xNAc2ic8?t=209) en is het nummer 0 niet verenigbaar met de atom '0'.

### Onder de motorkap

De rest van het hoofdstuk gaat in op het 'proof search' gedeelte van prolog. Wat hier interessant is dat prolog in zekere zin hetgene dat hij probeert op te lossen verkleint naar steeds kleinere proofs die hij probeert op te lossen op basis van de knowledge base, terwijl hij in een soort boom-structuur navigeert door de mogelijke oplossingen. Als een pad doodloopt gaat het proof search mechanisme weer omhoog de boom in opzoek naar andere paden die de knowledge base hem bieden.

### De eerste puzzel

Aan het eind van het hoofdstuk word ik weer uitgedaagd met een aantal opdrachten. Degene die ik deze keer wil uitlichten is opdracht 2.4 waarbij ik een simpele kruiswoordpuzzel moet oplossen. Er zijn 3 horizontale en 3 verticale 7-letterwoorden welke elkaar doorkruizen. De 6 woorden zijn al voor mij gedefinieerd, nu moet ik een definitie maken van `crossword/6` die de mogelijke oplossingen voor deze puzzel kan presenteren.

In mijn eerste oplossing maak ik het volgende feit aan:
```prolog
crossword(word(_, _, X1, _, X2, _, X3, _),
	word(_, _, Y1, _, Y2, _, Y3, _),
	word(_, _, Z1, _, Z2, _, Z3, _),
	word(_, _, X1, _, Y1, _, Z1, _),
	word(_, _, X2, _, Y2, _, Z2, _),
	word(_, _, X3, _, Y3, _, Z3, _)).
```
In het predicaat crossword zitten 6 individuele woorden waarvan de coördinaten van de kruisende lettervakjes zijn gemarkeerd met variabelen die overeen moeten komen. Als ik mijn programma echter vraag naar de oplossing van deze puzzel zie ik dat ik het juiste idee had, maar niet de juiste oplossing. Hij heeft voor mij ingevuld dat ik inderdaad 6 woorden heb, echter met zelf gegenereerde variabelen en niet de bovenstaande woorden. 

Na wat krabben aan mijn hoofd bedenk ik mij dat ik natuurlijk een regel moet maken van mijn kruiswoord, waarbij ik daadwerkelijk de gedefinieerde woorden gebruik. Deze oplossing ziet er als volgt uit: 
```prolog
crossword(V1, V2, V3, H1, H2, H3) :-
	word(V1, _, X1, _, X2, _, X3, _),
	word(V2, _, Y1, _, Y2, _, Y3, _),
	word(V3, _, Z1, _, Z2, _, Z3, _),
	word(H1, _, X1, _, Y1, _, Z1, _),
	word(H2, _, X2, _, Y2, _, Z2, _),
	word(H3, _, X3, _, Y3, _, Z3, _).
  ```
  Nu krijg ik een aantal verschillende manieren om de kruiswoordpuzzel in te vullen te zien, succes! De oplossing laat wel te wensen over, aangezien hij ook oplossingen aanbied waarbij hij woorden dubbel gebruikt. Aangezien ik nog niet goed weer hoe ik dit kan voorkomen, ik weet echter alleen over unificatie niet het tegenovergestelde.

Bij de praktische opdrachten leer ik ook `\=/2` kennen, het tegenovergestelde van unificeren. Dit kan ik gebruiken om mijn kruiswoordpuzzel beter te maken, al is het resultaat in mijn ogen niet ideaal:
```prolog
crossword(V1, V2, V3, H1, H2, H3) :-
	word(V1, _, X1, _, X2, _, X3, _),
	word(V2, _, Y1, _, Y2, _, Y3, _),
	word(V3, _, Z1, _, Z2, _, Z3, _),
	word(H1, _, X1, _, Y1, _, Z1, _),
	word(H2, _, X2, _, Y2, _, Z2, _),
	word(H3, _, X3, _, Y3, _, Z3, _),
	\=(V1, V2), \=(V1, V3), \=(V1, H1), \=(V1, H2), \=(V1, H3),
	\=(V2, V3), \=(V2, H1), \=(V2, H2), \=(V2, H3),
	\=(V3, H1), \=(V3, H2), \=(V2, H3),
	\=(H1, H2), \=(H1, H3),
	\=(H2, H3).
  ```
Voor elke mogelijke combinatie een uitzondering maken, ik hoop dat ik daar een betere oplossing voor vind...

---

#### [Terug naar de hoofdpagina](index.md)
