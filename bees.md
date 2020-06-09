
## De bijtjes en de feitjes

Het eerste hoofdstuk van de cursus gaat in op de dingen die mij al bekend waren over prolog, namelijk het opstellen van feiten en regels, op welke basis je daarna jouw programma kunt bevragen. 

### Knowledge Base

Het opstellen van deze feiten en regels doe je in een 'Knowledge Base', tijdens het maken van de opdrachten meer hierover. Wat hier opvalt is dat de syntax voor het opstellen van deze zaken sterk afwijkt van hoe dingen worden gedefinieert in object georienteerde talen. Hoewel elke taal enigsinds verschilt van syntax, zijn er voor elk verschil honderde overeenkomsten. Prolog heeft bij zijn fundering echter al dingen die erg afwijken zoals `:-` voor het aangeven van een regel, al zijn deze keuzes voor de syntax mogelijk eerder een product van de tijd waarin deze werd opgesteld dan inherent aan het afwijkende paradigma.

### Syntax

Wat verder aan bod komt zijn de syntax technische zaken zoals wat atoms, nummers, variabelen, etc. zijn. Deze doen denken aan zaken die ik leerde tijdens het maken van een parser voor een CSS-dialect. Belangrijk om te onthouden zijn dat variabelen altijd beginnen met een hoofdletter of underscore, terwijl atoms altijd beginnen met een kleine letter, zijn omringd door een `'`, of betaan uit andere speciale tekens. 

De feiten en regels die we opstellen in onze 'Knowledge Base' zijn complexe termen. Zij bestaan uit een 'functor' en zijn argumenten. Bijvoorbeeld een feit dat ik een programmeur ben: `programmer(thomas)` hierin is `programmer` de functor en atom `thomas` het argument van deze functor.

Omdat de functor van complexe termen vaker kunnen voorkomen is het ook belangrijk om de zogenoemde 'arity' te weten. De arity komt neer op hoeveel argumenten een complexe term kan hebben. Om deze complexe termen uit elkaar te houden wordt de arity toegevoegd aan de naam van zo'n term, hierdoor zal de `programmer(thomas)` met een arity van 1 in de 'context view' van mijn IDE dus `programmer/1` zijn, en bijvoorbeeld `loves(jan, hans)` vertalen naar `loves/2`.

Dit lijkt enorm veel op 'function overloading' in object georienteerde talen, waarbij de arity lijkt te dienen ter verduidelijking bij gebrek aan een function signature, zoals bijvoorbeeld `public boolean loves(Person person1, Person person2)` in Java.
