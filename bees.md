
## De bijtjes en de feitjes

Het eerste hoofdstuk van de cursus gaat in op de dingen die mij al bekend waren over prolog, namelijk het opstellen van feiten en regels, op welke basis je daarna jouw programma kunt bevragen. 

### Knowledge Base

Het opstellen van deze feiten en regels doe je in een 'Knowledge Base'. Wat hier opvalt is dat de syntax voor het opstellen van deze zaken sterk afwijkt van hoe dingen worden gedefinieerd in object georiënteerde talen. Hoewel elke taal enigszins verschilt van syntax, zijn er voor elk verschil honderden overeenkomsten. Prolog heeft bij zijn fundering echter al dingen die erg afwijken zoals `:-` voor het aangeven van een regel, al zijn deze keuzes voor de syntax mogelijk eerder een product van de tijd waarin deze werd opgesteld dan inherent aan het afwijkende paradigma.

De opdrachten horende bij dit hoofdstuk zijn voornamelijk oefenen op het droge. De meest interessante is opdracht 1.4 waarbij je zelf een aantal zinnen moet omzetten naar prolog feiten en regels. Hier heb ik zelf nog een aantal afgeleide zaken bij bedacht om meer te oefenen.
De om te zetten regels zijn:

1. Butch is a killer.
2. Mia and Marsellus are married.
3. Zed is dead.
4. Marsellus kills everyone who gives Mia a footmassage.
5. Mia loves everyone who is a good dancer.
6. Jules eats anything that is nutritious or tasty.

Zelf heb ik hier aan toegevoegd:

1. Anyone who kills is a killer.
2. Anyone who is killed is dead.
3. People that're married love eachother. (I hope)

De uitwerking van deze regels ziet er als volgt uit:

```prolog
killer(butch).
killer(X) :- kills(X, _).

married(marsellus, mia).
married(mia, marsellus).

dead(zed).
dead(X) :- kills(_, X).

givesFootMassage(hans, mia).
goodDancer(jan).

kills(marsellus, X) :- givesFootMassage(X, mia).

loves(mia, X) :- goodDancer(X).
loves(X, Y) :- married(X, Y).
```

Een simpel feit als "butch is a killer" kun je definiëren met `killer(butch)`. 

Wat ingewikkeldere regels zoals "Marsellus kills everyone who gives Mia a footmassage." geef je aan door het nieuwe feit `kills(marcellus, X)` waarbij marcellus persoon X is vermoord **als** (`:-`) persoon X een voetmassage geeft aan mia, gerepresenteerd door `givesFootMassage(X, mia)`. 

Mijn eigen afgeleide toevoeging "Anyone who kills is a killer." heeft als nieuw feit `killer(X)` persoon X is een moordenaar **als** `kills(X, _)` persoon X iemand (`_`) vermoord. 

### Syntax

Wat verder aan bod komt zijn de syntax technische zaken zoals wat atoms, nummers, variabelen, etc. zijn. Deze doen denken aan zaken die ik leerde tijdens het maken van een parser voor een CSS-dialect. Belangrijk om te onthouden zijn dat variabelen altijd beginnen met een hoofdletter of underscore, terwijl atoms altijd beginnen met een kleine letter, zijn omringd door een `'`, of bestaan uit andere speciale tekens. 

De underscore, leerde ik van mijn IDE is een speciale variabele die een verder anoniem iets of iemand aanduid. In de opgaven die in het vorige hoofdstuk werden besproken werd er iemand vermoord, wie dat is maakt verder niet uit voor de regel dus markeer je dat met een underscore.

De feiten en regels die we opstellen in onze 'Knowledge Base' zijn complexe termen. Zij bestaan uit een 'functor' en zijn argumenten. Bijvoorbeeld een feit dat ik een programmeur ben: `programmer(thomas)` hierin is `programmer` de functor en atom `thomas` het argument van deze functor.

Omdat de functor van complexe termen vaker kunnen voorkomen is het ook belangrijk om de zogenoemde 'arity' te weten. De arity komt neer op hoeveel argumenten een complexe term kan hebben. Om deze complexe termen uit elkaar te houden wordt de arity toegevoegd aan de naam van zo'n term, hierdoor zal de `programmer(thomas)` met een arity van 1 in de 'context view' van mijn IDE dus `programmer/1` zijn, en bijvoorbeeld `loves(jan, hans)` vertalen naar `loves/2`.

Dit lijkt enorm veel op 'function overloading' in object georiënteerde talen, waarbij de arity lijkt te dienen ter verduidelijking bij gebrek aan een function signature, zoals bijvoorbeeld deze java functie:
```java
public boolean loves(Person person1, Person person2)
``` 

### Recap

Dit eerste hoofdstuk was nog niet bijzonder uitdagend. Ik wist al dat prolog werkte zoals ik het nu heb geleerd, en het opstellen van deze regels en feitjes is redelijk simpel. Het bevragen van prolog op basis van mijn opgestelde knowledge base is wel erg leuk om te doen, maar doet meer denken aan een slimme vorm van SQL queries dan aan programmeren met een object georiënteerde of een functionele taal. 

Ik snap op dit moment nog niet goed de toepassing van prolog in echte programmeercontexten. Het bevragen van zo'n knowledge base is leuk, maar het lijkt mij niet bijzonder zinnig zonder een dynamische "database" te hebben met feiten en regels zoals een SQL-database zou hebben ofwel voor hele specialistische toepassingen zoals het invoeren van een puzzel zoals ik van plan ben te doen.

---

#### [Terug naar de hoofdpagina](index.md)
