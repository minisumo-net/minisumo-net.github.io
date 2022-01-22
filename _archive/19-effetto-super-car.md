---
title: "Modding: effetto super car"
excerpt: "In questa guida vedremo come inserire nel frontale del nostro Computer un semplice gioco di luci regolato da un 555."
permalink: /tutorial/modding-effetto-super-car
author: "Antonio Rutigliano"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/effetto-super-car/Scheda1.jpeg
  teaser: /assets/images/tutorial/effetto-super-car/Scheda1.jpeg
---

Quante volte ci è capito di vedere il nostro case “depresso”. In questa guida vedremo come inserire nel frontale del nostro Computer un semplice gioco di luci regolato da un 555.

> **Definizione**
> L’effetto che adotteremo sarà quello quello della mitica serie televisiva degli anni 80 “SuperCar” Creando quindi un effetto luminoso all’interno del case che emuli la scia luminosa della macchina.
> 
>Detta in parole povere riecreeremo attravero 3 LED il movimento di questa scia. Una per volta, via via, partendo dalla prima ed arrivando sino all’ultima ed infine tornare a riaccendere a ritroso le luci precendentemente spente.
> Questo ciclo lo effettuerà periodicamente.

*Schema circuito e PCB:*

{% include figure image_path="/assets/images/tutorial/effetto-super-car/schema2.jpg" alt="Schema" caption="Schema" %}

{% include figure image_path="/assets/images/tutorial/effetto-super-car/sbroglio2.jpg" alt="Sbroglio" caption="Sbroglio" %}

*Elenco componenti:*

* R1=1KOHM
* R2=10KOHM
* R3-4-5-6=1KOHM
* C1=10uF 16V
* C2=100.000pf –forse e meglio se ne usate una da 10.000pF o 47.000pF–
* D1-2-3-4-5-6=1N4148
* LED1-2-3=LED (colore e dimensione a vostro gusto)
* IC1=555
* IC2=4017

(disponibile in area download)

# Funzionamento

I 3 LED, chiamati LED1, LED2, LED3 connessi al 4017 si avvieranno in sequenza seguendo l’ordine dei collegamenti dello stesso integrato. Quindi si accenderanno nel seguente modo: LED1 LED2 LED3 LED3 LED2 LED1.

{% include figure image_path="/assets/images/tutorial/effetto-super-car/img2.gif" alt="Pinning Diagram" caption="Pinning Diagram" %}

Il 4017 citato in precedenza utilizzando il clock generato dal 555 attiva una alla volta le sue 10 uscite in sequenza numerica, infatti questo è un Decoder Counter/Divider, un contatore o divisore per 10. L’integrato possiede anche un pin di reset, che permette la riproduzione “eterna” della scia luminosa.

Un singolo ciclo dura 6 impulsi, e grazie al pin in questione, pin15, il settimo impulso del 555 costringerà il reset del 4017, riprendendo il ciclo dall’inizio.

Le uscite dell’integrato sono numerate da 0 a 9, e le collegheremo ai 3 LED in questo modo:

* USCITA 0 e USCITA 5 al LED1
* USCITA1 e USCITA4 al LED2
* USCITA 2 e USCITA 3 al LED3.

{% include figure image_path="/assets/images/tutorial/effetto-super-car/Scheda1.jpeg" alt="Scheda completata" caption="Scheda completata" %}

Il 4017 Manda ad ogni impulso che arriva in ingresso dall’ 555 un valore alto (5V) partendo dalla USCITA0 fino ad arrivare alla USCITA5. Per sicurezza, evitando possibili danneggiamenti dell’integrato, utilizzermo i comuni diodi 1N4148, per proteggere ogni singola uscita da possibili ritorni di tensione.

# Il 555

{% include figure image_path="/assets/images/tutorial/effetto-super-car/Scheda2.jpeg" alt="Retro scheda" caption="Retro scheda" %}

Per generare l’impulso richiesto, come abbiamo detto in precedenza useremo il 555.
Un integrato che può definirsi “multi uso”, infatti questo viene utilizzato in parecchie applicazioni.

Può svolgere svariate funzioni in base al tipo di elettronica che vorremo adottare.Per questo integrato non mi dilungerò a spiegare come funziona perché in rete esiste molto materiale a merito.

* http://www.williamson-labs.com/pu-aa-555-timer_fast.htm (Animazione)
* http://www.uoguelph.ca/~antoon/gadgets/555/555.html (tutorial in inglese con alcune appicazioni)

Noi in questo articolo lo utilizzeremo in configurazione di multivibratore astabile, per generatore il clock necessario al funzionamento.

# Risultato Finale

{% include figure image_path="/assets/images/tutorial/effetto-super-car/pc.jpg" alt="Assemblato sul PC" caption="Assemblato sul PC" %}


## Note applicative

Il circuito va alimentato a 5Volt.
I LED vanno collegati sull connettore a 4 poli in questo modo: i catodi vanno collegati insieme sul PIN4. I anodi rispettivamente sui PIN 1 2 3.

# Altre configurazioni

Un’altra possibile configurazione può essere quella di linearizzare il tempo di accensione per singolo LED infatti nel modo citato di questo articolo la durata di accensione è differente a seconda degli stessi. Eliminando il diodo D4 D2 sull’uscita 4  e 5 del 4017. Collegando il segnale di reset dall’uscita 6 all’uscita 4. Collegare il catodo del diodo D6 non con quelo di D5 ma con quello del diodo D3.

{% include figure image_path="/assets/images/tutorial/effetto-super-car/modifica.gif" alt="Modifica" caption="Modifica" %}

In questo modo avremo l’accensione dei LED secondo la sequenza LED1 LED2 LED3 LED2.

