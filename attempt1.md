## Overmoed

Na het oplossen van de kruiswoordpuzzel uit het vorige hoofdstuk voelde ik mezelf moedig. Als ik een kruiswoordpuzzel kon oplossen dan kon ik toch zeker ook wel een nonogram oplossen?!

### Waar

Ik begon op dezelfde manier als bij de kruiswoordpuzzel aan mijn nonogram oplosser. Wat nodig de nodige strijd opleverde omdat ik op dit punt nog niet had gewerkt met nummers in prolog. Ook bleken nummers helemaal niet zo makkelijk te zijn als ik had gehoopt. Met unification nummers met een som van andere nummers vergelijken werkte in ieder geval niet. Na te duiken in StackOverflow en SWI-Prolog documentatie kwam ik tot `is/2` welke mij zou kunnen helpen. Dat alles resulteerde in de volgende code:

```prolog
space(0).
space(1).
	
row(N, N1, N2, N3, N4, N5) :-
	space(N1),
	space(N2),
	space(N3),
	space(N4),
	space(N5),
	(N is N1+N2+N3+N4+N5).

column(N, N1, N2, N3, N4, N5) :-
	space(N1),
	space(N2),
	space(N3),
	space(N4),
	space(N5),
	(N is N1+N2+N3+N4+N5).
	
	
grid(V1, V2, V3, V4, V5, H1, H2, H3, H4, H5) :-
	row(V1, X1, Y1, Z1, XX1, XY1),
	row(V2, X2, Y2, Z2, XX2, XY2),
	row(V3, X3, Y3, Z3, XX3, XY3),
	row(V4, X4, Y4, Z4, XX4, XY4),
	row(V5, X5, Y5, Z5, XX5, XY5),
	column(H1, X1, X2, X3, X4, X5),
	column(H2, Y1, Y2, Y3, Y4, Y5),
	column(H3, Z1, Z2, Z3, Z4, Z5),
	column(H4, XX1, XX2, XX3, XX4, XX5),
	column(H5, XY1, XY2, XY3, XY4, XY5),
```

Door aan grid de 5 begingetallen voor de verticale en horizontale as mee te geven zal hij proberen zijn rijen en kolommen (die hetzelfde zijn, maar ik voor de leesbaarheid heb gescheiden) proberen te vullen met 0 (lege vakjes) of 1 (zwarte vakjes). Ik toets een simpel voorbeeld `grid(1, 3, 5, 3, 1, 1, 3, 5, 3, 1,).` in en krijg terug: `true`. Je krijgt terug waarom je vraagt, maar dat was ik even vergeten.

### Meer dan waar

Ik wil natuurlijk weten of er een nul of één staat in mijn variabelen X1 t/m XY5. Dit blijkt nog lang niet zo makkelijk als ik hoopte. Het printen van de row-termen levert namelijk enkel met dezelfde gegenereerde variabelen die ik ook bij mijn eerste kruiswoordpuzzeloplossing tegenkwam. Ook vanuit het row predicaat zelf printen biedt geen soelaas, die wordt immers ook aangeroepen (en print dus waardes) voor de proof-search pogingen die niet tot succes leiden.

De uiteindelijke oplossing is niet erg majestueus te noemen, maar op dit moment schiet mijn kennis over het printen van informatie en het samenstellen van strings om te printen zwaar tekort. De oplossing is overigens het toevoegen van de volgende termen aan het grid predicaat:
```prolog
	writeln("[" - X1 - Y1 - Z1 - XX1 - XY1 - "]"),
	writeln("[" - X2 - Y2 - Z2 - XX2 - XY2 - "]"),
	writeln("[" - X3 - Y3 - Z3 - XX3 - XY3 - "]"),
	writeln("[" - X4 - Y4 - Z4 - XX4 - XY4 - "]"),
	writeln("[" - X5 - Y5 - Z5 - XX5 - XY5 - "]").
```

Een ander probleem waar ik tegenaan loop is het kunnen ondersteunen van meerdere nummers in de zijlijn. Zo zou de horizontale eerste rij ook '1, 1' kunnen bevatten ipv een enkel nummer omdat er 2 losstaande zwarte vlakken moeten zijn op die rij. Hiervoor zal ik eerst moeten leren hoe lijsten werken in prolog, daarnaast zou hiervoor de huidige definitie van de rij en de kolom flink moeten worden aangepast.

Hiermee heb ik echter wel een werkende versie van de versimpelde opdracht die ik had gesteld indien het hoofddoel te moeilijk zou blijken.

---

#### [Terug naar de hoofdpagina](index.md)
