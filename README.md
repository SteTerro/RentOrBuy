# RentOrBuy

Il _Rent or Buy Problem_ è un problema classico nella teoria degli algoritmi online che modella una situazione decisionale in cui un agente deve scegliere se noleggiare un'attrezzatura giorno per giorno o acquistarla definitivamente, senza conoscere in anticipo la durata effettiva del suo utilizzo.

Nel paper _Algorithms with Predictions_ di Mitzenmacher e Vassilvitskii, sono stati presentati dei framework che combinano l'approccio classico degli algoritmi online con tecniche di Machine Learning per migliorare le prestazioni decisionali. Le applicazioni di questo approccio sono numerose, come i _Learned Bloom Filters_ o il _Caching_. Uno dei modelli proposti mirava a risolvere il *Rent or Buy Problem* presentato come lo _Ski Rental Problem_. 

L'obiettivo è presentare un algoritmo che possa essere ottimale quando il predittore è corretto, mantenendo comunque garanzie teoriche minime nel caso peggiore quando il predittore sbaglia.

### Formulazione del Problema

Il problema simula lo scenario di uno sciatore (o, in questo caso, un giocatore di tennis) all'inizio della stagione che deve decidere se noleggiare o acquistare la propria attrezzatura:
- **Costo del noleggio**: 1 dollaro al giorno.
- **Costo di acquisto**: Un importo fisso di _b_ dollari.
- **Incertezza**: Lo sciatore non sa in anticipo per quanti giorni $(d^*)$ scierà (o giocherà) effettivamente durante la stagione.

L'obiettivo è minimizzare la spesa totale senza conoscere il futuro.

In questo notebook, miriamo ad affrontare questo problema utilizzando un approccio alternativo. I due algoritmi classici per risolvere un problema di _Rent or Buy_ sono:
1. **Algoritmo Offline (Ottimale)**: Con una conoscenza perfetta di _D_, il costo ottimale è `min(D × r, b)`.
2. **Algoritmo Online Deterministico**: Noleggiare finché il costo cumulativo non raggiunge _b_, quindi procedere all'acquisto.
