## Er zijn fouten in de oplossing van de puzzel.

Met de kennis van lijstjes en recursie op zak ga ik door naar mijn tweede en laatste poging mijn doel te halen. Ik heb 2 punten die ik wil aanpakken voor het verbeteren van mijn nonogramoplosser. 

1. Het mooier printen van de oplossing.
2. Het ondersteunen van meerdere cijfers per rij of kolom.

### De printer

Ik besluit eerst mijn printer te verbeteren met de lijstjes en kennis over recursie. Hier liep ik tegen een probleem aan, ik wilde in plaats van eentjes en nullen zwarte en lege vakjes printen. Echter had ik een soort if-else constructie nodig om mijn eentjes en nulletjes daarin om te zetten.

Op het internet vond ik de syntax voor conditionals in prolog. Door `conditie -> effect` op te schrijven kon ik een if bouwen, de else if werd makkelijk gemaakt met de `;`-operator, die ik al kende uit de cursus.

Hieruit volgde de volgende code voor de printer: 
```prolog
writeGrid([]).
writeGrid([Row | RowTail]) :-
	writeRow(Row),
	write("\n"),
	writeGrid(RowTail).


writeRow([]).	
writeRow([Write | Tail]) :-
	(Write == 0 -> write(" ");
	Write == 1 -> write("■")),
	writeRow(Tail).
```
De `writeGrid/1` methode stuurt aan de hand van een lijstje geneste lijstjes met daarin de status van elk vakje van elke rij de `writeRow/1` methode aan. Deze methode gaat recursief door het lijstje met de status van elk vakje van de rij heen en print in het geval van een 1 een `■` en in het geval van een 0 een spatie-karakter.

Dit levert bij een input van:
```
   1   3   5   3   1
1
3
5
3
1
```
De volgende output op:
```
  ■  
 ■■■ 
■■■■■
 ■■■ 
  ■  
true 
```
Succes!

### Ruzie met de rijtjes

Dan komt echter de volgende taak. De grid moet een input van lijstjes gaan ondersteunen, want in de zijlijn kan bijvoorbeeld ook `1 1 1` zijn aangegeven voor de invulling van de corresponderende rij of kolom. Dit zou een output van `■ ■ ■` moeten opleveren.

Ik heb hiervoor van alles geprobeerd. Rijen die zichzelf recursief aanroepen per nummer in de lijst. Rijen die vakje voor vakje werden opgebouwd in een recusieve term. Maar ik moet onderkennen dat dit mij niet is gelukt.

Het vullen van de rij aan de hand van de nummers wil nog wel lukken, maar het volgordelijk houden van de nummers in de lijst in relatie tot de ingevulde vakjes en de vereiste dat er bij meerdere nummers een leeg vakje tussen elke samenstelling van blokjes zit heb ik niet helemaal werkend gekregen.

De code die het dichtst bij komt is de volgende:
```prolog
list_total([], 0).
list_total([Head | Tail], Sum) :-
	list_total(Tail, Res),
	(Sum is Head + Res).
	
row(N, N1, N2, N3, N4, N5) :-
	space(N1),
	space(N2),
	space(N3),
	space(N4),
	space(N5),
	list_total(N, Total),
	(Total is N1+N2+N3+N4+N5),
	
	length(N, Amount),
	check_not_neighbor(Amount, [N1, N2, N3, N4, N5]),
	writeln(Amount).

check_one_break([X1, X2, X3, X4, X5]) :-
	X1 is 1,
	X2 is 0;
	X2 is 1,
	X1 is 0,
	X3 is 0;
	X3 is 1,
	X2 is 0,
	X4 is 0;
	X4 is 1,
	X3 is 0,
	X5 is 0;
	X5 is 1,
	X4 is 0.
	

check_two_break([_, X1, _, X2, _]) :-
	X1 is 0,
	X2 is 0.
	
check_not_neighbor(1, _).	
check_not_neighbor(N, Spaces) :-
	(N is 2 -> check_one_break(Spaces);
	N is 3 -> check_two_break(Spaces)).
```
Deze rekent allereerst het totaal aantal blokjes dat moet worden ingekleurd uit en kijkt daarna of er in het geval van meerdere nummers of er geen blokjes naast elkaar zijn gezet. De methode waarop deze check gaat, zoals te zien in `check_one_break` is in mijn ogen een vrij lelijke 'hack', en maakt de uitbreiding van de grid volledig onmogelijk. Daarnaast bewaakt deze code niet de volgordelijkheid van de nummers.

Het testen van deze code met een puzzel van de site van mijn doelstelling levert dan ook `Er zijn fouten in de oplossing van de puzzel.` omdat hij (naast dat er een hele hoop oplossingen worden aangedragen) op basis van de beschrijving `1 2` de volgende oplossing voor die rij aanbied: `■■ ■  `.

Ik moet dus de overwinning aan mijn doelstelling aanbieden, ik heb meerdere uren geprobeerd te komen met een term die wel de oplossing zou kunnen zijn voor mijn problemen maar mijn vermogen om logisch (zoals het logisch programmeren impliceert) te denken laat mij in de steek.

### Kijken bij de buren

Een laatste poging om misschien tot nieuwe inzichten te komen deed ik door dezelfde strategie toe te passen als bij de lijst opdracht. Eens kijken hoe andere mensen dit probleem hebben opgelost.

Al snel vind ik hiervoor een [nonogramoplosser van Lars Buitinck op github](https://gist.github.com/larsmans/1146705/8ba25a66402adad16a89a09eeb68bf83f8b6f01a). Hoewel ik hier delen van kan begrijpen met mijn huidige prolog kennis zijn er ook een hoop zaken die mij volledig boven de pet gaan. Zijn `arcs/4` functie waar wordt gewerkt met states zegt mij bijvoorbeeld helemaal niks.

In mijn originele doelbeschrijving gaf ik al aan hoe ik mijn opdracht zou kunnen bijsturen mocht deze te moeilijk of te makkelijk blijken. Mijn makkelijkere doelstelling heb ik echter al behaald tijdens het maken van mijn eerste poging.

Zeker deze half geupgrade versie van mijn nonogramoplosser is zeker instaat 5x5 nonogrammen zoals beschreven in de 'makkelijkere' doelstelling op te lossen.

---

#### [Terug naar de hoofdpagina](index.md)
