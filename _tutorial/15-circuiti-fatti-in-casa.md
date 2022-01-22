---
title: "I circuiti stampati fatti in casa"
excerpt: "I circuiti stampati fatti in casa"
permalink: /tutorial/i-circuiti-stampati-fatti-in-casa
author: "Andrea Di Pietrantonio"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/circuiti/clip_image012.jpg
  teaser: /assets/images/tutorial/circuiti/clip_image012.jpg
---

Negli articoli precedenti eravamo rimasti con la realizzazione di un bromografo, ma ci sono giunte molte domande su come realizzare un circuito stampato e come utilizzare al meglio il bromografo.
Con questa guida analizzeremo al meglio come fare un circuito stampato.

# Scopo del documento

Questo documento vuole descrivere le varie fasi di realizzazione di un circuito stampato (basetta PCB) partendo dallo schema elettrico.

Per seguire tale attività sono necessari:

* un personal computer con stampante
* un software grafico per disegnare il circuito elettrico ed il circuito stampato;
* un bromografo dotato di lampada UVA; ( Costruiamo un bromografo, parte 1, parte 2, parte 3 )
* acidi rilevatori e di incisione e relative vaschette in plastica;
* trapano a colonna, raccomandato ma non indispensabile, con punte da 0,8 a 1,2 mm

# Struttura del documento

Il documento è strutturato nei seguenti capitoli il cui contenuto può essere riassunto come segue:
* Scopo del documento: il presente capitolo;
* Come realizzare una basetta PCB: descrive le varie fasi di realizzazione di una basetta PCB.

# Come realizzare una basetta PCB

## Circuito elettrico e circuito stampato

Un circuito stampato è la realizzazione pratica di uno schema elettrico e per disegnarlo utilizziamo come detto un software che installiamo su un PC. Nel nostro caso abbiamo utilizzato EAGLE, molto pratico e ricco di librerie di componenti

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image001.jpg" alt="Sbroglio circuito" caption="Sbroglio circuito" %}

Dopo la realizzazione dello schema elettrico si passa alla fase di sbrogliatura che porterà al disegno del circuito stampato (vedi figura).

A questo punto siamo pronti per procedere con la stampa del circuito che andremo a realizzare.

Il passo successivo e’ di stampare il circuito su carta o lucido. Con il lucido il processo di foto incisione è più veloce vista la trasparenza del supporto, ma ogni volta che se ne deve realizzare uno o ci si accorge di aver fatto qualche errore e doverlo ristampare si sprecherà un foglio di lucido e quindi denaro.

Utilizzando della normale carta bianca invece, diventa necessario aumentare il tempo di esposizione agli ultravioletti, ma permette di risparmiare l’acquisto di costosi fogli lucidi e se si sbaglia qualcosa basta ripetere la stampa su un altro foglio di carta bianca.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image002.jpg" alt="Stampa" caption="Stampa" %}

L’accortezza durante la stampa è di regolare al massimo la quantità di inchiostro nero che viene stampato. Fate attenzione a non utilizzare dell’inchiostro nero creato con cartucce colorate in quanto non è mai totalmente nero. La migliore soluzione è di utilizzare una stampante laser.

## Impressione del circuito con il bromografo

Come detto la carta bianca non e’ trasparente, ma i raggi ultravioletti in parte riescono a passarla e quindi e’ sufficiente aumentare il tempo di esposizione. Conviene fare qualche prova: io ad esempio con il lucido accendo la lampada per 1 minuto, mentre con la carta bianca la lascio accesa per 8-10 minuti.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image003.jpg" alt="Bromografo" caption="Bromografo" %}

Il bromografo che abbiamo costruito (così si chiama questo strumento che si vede in figura) è una semplice scatola di legno con un coperchio al cui interno sono installate 2 lampade che emettono raggi UVA, utili ad impressionare le basette presensibilizzate che poi utilizzeremo. I collegamenti elettrici delle lampade sono uguali a quelli delle normali lampade al neon.
Su internet si possono trovare facilmente progetti di diversi tipi di bromografi fatti in casa.
( Costruiamo un bromografo, parte 1, parte 2, parte 3 )

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image004.jpg" alt="Preparazione per l'incisione" caption="Preparazione per l'incisione" %}

Le basette presensibilizzate sono vendute nei negozi specializzati con una pellicola protettiva, questa evita che la superficie sensibile venga esposta alla luce ambiente prima dell’utilizzo.
Quando si dispone del foglio lucido o bianco con il disegno del circuito, si toglie la pellicola e si posiziona la basetta con la parte sensibile a diretto contatto del foglio, sul lato dove è l’inchiostro.
Questo attenzione permette che le piste siano ben definite, in quanto anche se il foglio ha uno spessore minimo, se messo al contrario provoca comunque una leggera sfumatura dovuta all’ombra della luce proiettata.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image005.jpg" alt="Incisione" caption="Incisione" %}

Per far aderire bene la carta alla basetta presensibilizzata si può premere questa con un po’ di libri (i vocabolari Zanichelli sono il massimo!). Se tenete premuto con le mani rischiate di fare dei piccoli movimenti involontari che sfumano anche di poco il risultato dell’impressione.

**!!! ATTENZIONE !!!** Cercate di non guardare la luce azzurrina prodotta dalle lampade UVA, non è consigliabile, potrebbe creare qualche disturbo alla vista.

Io utilizzo questo metodo: posiziono il tutto sopra il vetro, sposto molto lentamente il tutto sotto il letto, attacco la spina dell’alimentazione, attendo il tempo necessario e poi stacco la spina e vedo il risultato.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image006.jpg" alt="Primo risultato" caption="Primo risultato" %}

Sulla basetta impressionata correttamente si noterà il disegno delle piste in leggero colore verde sullo sfondo marrone chiaro. Appena constatate che è tutto a posto evitate di far prendere ulteriore luce ambiente alla basetta (non fate tutto ciò ad esempio sul terrazzo di casa in pieno giorno!!).

## Incisione del circuito

Subito dopo si può mettere la basetta nell’acido rilevatore ed attendere alcuni minuti che lo strato fotosensibile illuminato dai raggi si distacchi dal rame. Io passo un po’ di nastro adesivo sul lato opposto del rame e lo utilizzo per maneggiare o scuotere la basetta dentro gli acidi.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image007.jpg" alt="Acido rivelatore" caption="Acido rivelatore" %}

L’acido rilevatore viene venduto normalmente sotto forma di una soluzione in polvere da sciogliere in una bottiglia d’acqua da 1 litro.
Io ne ho preparata una bottiglia, che conservo chiusa al buio in un armadio, e ne verso ad ogni utilizzo quel tanto che basta a ricoprire la basetta in una vaschetta di plastica.
Dopo un solo utilizzo non è più quasi efficace per un’altra basetta.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image008.jpg" alt="Durante l'attesa" caption="Durante l'attesa" %}

Durante l’azione dell’acido, si vedranno comparire nitidamente le piste in verde disegnate con lo strato di fotosensibile, che era sotto l’ombra dell’inchiostro nero nel bromografo.
Quando non si stacca più nulla dal rame, si può risciacquare sotto un po’ d’acqua la basetta ed asciugarla, facendo attenzione a non graffiare il fotosensibile rimasto, altrimenti si avranno piste interrotte.
Il passo successivo è di immergere la basetta nell’acido di incisione, che porterà via tutto il rame ad eccezione di quello sotto le piste coperte dal fotosensibile.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image009.jpg" alt="Cloruro Ferrico" caption="Cloruro Ferrico" %}

Il processo chimico di rimozione del rame impiega del tempo per terminare del tutto. Per accelerare I tempi si può scaldare il liquido, ad esempio puntandoci contro il getto d’aria calda di un asciugacapelli, avendo accortezza di non alzare schizzi di acido che provocano macchie impossibili da pulire, e in particolar modo questo acido corrode facilmente tutti i minerali.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image010.jpg" alt="Durante l'azione dell'acido" caption="Durante l'azione dell'acido" %}

Se risciacquate la basetta dai vari acidi in una vasca da bagno di casa o nel lavandino della cucina, fate scorrere molta acqua durante e anche dopo che l’acido se ne e’ andato, così eventuali residui non rimarranno sulla ceramica o nelle tubazioni.

Al contrario dell’acido per lo sviluppo, quello per l’incisione può essere riutilizzato altre volte, ma con l’utilizzo la sua capacita di erosione diminuisce.

Naturalmente gli acidi che rimangono nelle vaschette non vanno assolutamente buttati nei normali scarichi di casa, ma vanno smaltiti portandoli nelle varie raccolte di rifiuti pericolosi della propria città.
Prima di passare alla fase di foratura si può pulire la basetta dei residui dello strato fotosensibile utilizzando un panno con dell’alcool o dell’acetone.

## Foratura

A questo punto si passa alla fase di foratura utilizzando le classiche punte da 0,8 o 1 mm. E’ preferibile utilizzare un trapano a colonna che fora perfettamente a 90° la basetta.

Quando si poggia la punta questa tende sempre un po’ a scivolare di lato e spesso i piccoli fori in fila, ad esempio degli integrati, non vengono mai tutti allineati. Prima di forare, con martelletto ed un piccolo punteruolo oppure un chiodo ben appuntito, pratico delle piccole incisioni in modo che le punte ci si appoggeranno senza scivolare via.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image011.jpg" alt="Foratura" caption="Foratura" %}

Dopo la foratura si possono togliere i bordini intorno al foro che la punta crea passando a mano leggera una punta più grande. Di seguito il risultato finale.

{% include figure image_path="/assets/images/tutorial/circuiti/clip_image012.jpg" alt="Risultato Finale" caption="Risultato Finale" %}