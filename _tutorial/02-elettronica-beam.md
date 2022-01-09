---
title: "Elettronica BEAM"
excerpt: "Elettronica BEAM per un robot da minisumo"
permalink: /tutorial/elettronica-beam
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/beam/finito.jpg
  teaser: /assets/images/tutorial/beam/finito.jpg
author: "Raffaello Bonghi"
classes: wide
sensori:
  - url: /assets/images/tutorial/beam/s320105.jpg
    image_path: /assets/images/tutorial/beam/s320105.jpg
    alt: "GP2D15"
    title: "GP2D15"
  - url: /assets/images/tutorial/beam/91401.jpg
    image_path: /assets/images/tutorial/beam/91401.jpg
    alt: "QRB1134"
    title: "QRB1134"
circuito-stampato:
  - url: /assets/images/tutorial/beam/SchemaEN.jpg
    image_path: /assets/images/tutorial/beam/SchemaEN.jpg
    alt: "Schema elettrico"
    title: "Schema elettrico"
  - url: /assets/images/tutorial/beam/StampatoEN.jpg
    image_path: /assets/images/tutorial/beam/StampatoEN.jpg
    alt: "Circuto stampato"
    title: "Circuto stampato"
montaggio:
  - url: /assets/images/tutorial/beam/MontaggioSharp.jpg
    image_path: /assets/images/tutorial/beam/MontaggioSharp.jpg
    alt: "Montaggio Sharp"
    title: "Montaggio Sharp"
  - url: /assets/images/tutorial/beam/ColleLinea.jpg
    image_path: /assets/images/tutorial/beam/ColleLinea.jpg
    alt: "Collegamento sensori di linea"
    title: "Collegamento sensori di linea"
  - url: /assets/images/tutorial/beam/Sensore.jpg
    image_path: /assets/images/tutorial/beam/Sensore.jpg
    alt: "Sensori di linea"
    title: "Sensori di linea"
---

Finalmente è il turno di completare l’elettronica del nostro Minisumo montando l’elettronica BEAM.Questa elettronica non ha bisogno di PIC o di Integrati che vengano programmati dal PC ma attraverso neuroni elettronici viene cercato di riprodurre il funzionamento di un neurone e nel nostro caso utile per dare un cervello al nostro Minisumo.

L’elettronica del nostro minisumo è composta da 5 neuroni che lavorando insieme daranno vita al nostro robottino.
Lo schema da cui ci baseremo è lo schema di John Isaac Mumford in modo tale da creare una logica comoda per il nostro minisumo.
Gli elementi di cui avremo bisogno saranno per la sensoristica:

{% include gallery id="sensori" caption="sensori minisumo" layout="half" %}

Per quanto riguarda l’elettronica:

| Quantità | Componente |
|----------|------------|
| 2        | Relé Doppio scambio da 5V |
| 1        | Relé Monoscambio da 5V |
| 2        | 1N4148 |
| 5        | 2N3904 |
| 2        | 2N3906 |
| 3        | 5 K Trimmer Multigiro |
| 4        | 10 K |
| 2        | 100 kpF |
| 2        | 100 uF |
| 2        | 270 |
| 1        | 1000 uF |
| 1        | Switch di Avvio |
| 1        | Pulsante di Reset |
| 2        | LED rossi da 3mm |
| 1        | LED verde da 3mm |
| 3        | Connettori da 2 Poli |
|          | Strip di contatti sia maschio che femmina |
|          | Cavi di vari colori |


Dallo schema è possibile estrapolare il circuito stampato che per chi ha il bromografo o ha seguito le nostre guide potrà sfruttare per stampare il circuito:

{% include gallery id="circuito-stampato" caption="schema elettrico e circuito stampato" layout="half" %}

Il circuito come possiamo notare è costituito da sue sezione, la prima sezione con l’elettronica del robot e l’altra con il Brige del controllo dei ponti realizzato con i Relé.

Possiamo scaricare lo stampato e lo schema in Eagle per poter iniziare a preparare il nostro circuito da montare sul minisumo. **( lo stampato è disponibile nell’area download )**

{% include figure image_path="/assets/images/tutorial/beam/01montaggio.jpg" alt="montaggio Parte 1" caption="montaggio Parte 1" %}

Dopo aver finito di stampare la basetta possiamo finalmente iniziare a saldar, ricordandoci prima di tutto di saldare i componenti più bassi di profilo, quindi primi fra tutti i ponti, dopodiché le resistenze, i diodi, transistor fino ad arrivare ai relè e l’interruttore.

Preparate le due schede potremo finalmente iniziare a montarle sul robot partendo dalla scheda del controllo dei Motori, come possiamo notare è costituita soltanto da 2 relé da 5 volt doppio scambio e 4 connettori per collegare i motori, collegare l’alimentazione.

{% include figure image_path="/assets/images/tutorial/beam/Scheda.jpg" alt="Scheda" caption="Scheda" %}

Prendiamo la nostra scheda per il controllo dei motori e montiamola sotto il telaio del robot

{% include figure image_path="/assets/images/tutorial/beam/MontaggioRELE.jpg" alt="Montaggio RELE" caption="Montaggio RELE" %}

Foriamo la scheda e fissiamola con una vite al telaio.

Da qui prendiamo i cavi provenienti dai motori e colleghiamoli nei connettori alla destra della scheda.

Mentre i Primi due connettori a sinistra partendo dall’alto sono per l’alimentazione e gli altri per polarizzare il relé.

Per il momento fermiamoci e smontiamo la benna precedentemente montata nell’articolo precedente, ed assieme ad una zavorra, nel mio caso una piccolo pezzettino di ferro.

{% include figure image_path="/assets/images/tutorial/beam/PreparazioC.jpg" alt="Preparazione Benna" caption="Preparazione Benna" %}

E dopo aver scartavetrato, diamo una mano di vernice nera in modo tale da rendere il robot il più possibile invisibile alla luce infrarossa. Perché infatti come sappiamo le superfici nere assorbono più luce rispetto a quelle bianche.

{% include figure image_path="/assets/images/tutorial/beam/Colorat.jpg" alt="Benna Colorata" caption="Benna Colorata" %}

Adesso è il turno di avvitare la scheda dell’elettronica alla struttura del robot, e la monteremo logicamente sulla parte alta del telaio.

{% include figure image_path="/assets/images/tutorial/beam/elettrMON.jpg" alt="Elettronica Montata" caption="Elettronica Montata" %}

Recuperiamo i porta batterie precendetemente comprati

{% include figure image_path="/assets/images/tutorial/beam/PortaBatt.jpg" alt="Porta Batterie" caption="Porta Batterie" %}

E montiamoli nel seguente ordine:

Il porta batterie da 3, dopo aver coperto la base con delle strisce adesive, facciamo lo stesso anche per la parte bassa del telaio, in modo tale da poter far adererire la base del porta batterie con il telaio.

{% include figure image_path="/assets/images/tutorial/beam/MontaggioPB.jpg" alt="Montaggio Porta Batterie" caption="Montaggio Porta Batterie" %}

Fermiamoci con il montaggio dei porta battiere e riprendiamo la benna precedentemente colorata, Avvitiamo sulla parte posteriore della Benna i sensori di Linea QRB1134 come si può vedere nella foto. Per capire il funzionamento di questi sensori Infrarossi, basta seguire l’articolo di Antonio presente nelle guide del sito.

{% include figure image_path="/assets/images/tutorial/beam/Benna.jpg" alt="Benna" caption="Benna" %}

Dopodiché avvitiamo la benna e la zavorra come in foto:

{% include figure image_path="/assets/images/tutorial/beam/MontaggioBEN.jpg" alt="Montaggio Benna" caption="Montaggio Benna" %}

E come si può vedere nella fotografia il porta batterie da 2 lo montiamo sulla parte frontale del robot, ed usando le strisce adesive lo collochiamo sulla parte più alta della zavorra.

{% include figure image_path="/assets/images/tutorial/beam/QuasiFin.jpg" alt="Quasi Finito" caption="Quasi Finito" %}

Finalmente siamo arrivati quasi alla fine della realizzazione del minisumo. Dobbiamo collegare i cavi precendetemete montati nella scheda dei relé alla scheda dell’elettronica.

I cavi dell’alimentazione provenienti dai relé andranno collegati sul connettore di uscita del Relé.

Mentre i rimanenti nel connettore di ingresso per la gestione dei motori. Come è possibile vedere nella foto.

Non ci resta che collegare tutti i porta batterie insieme per poter far funzionare il mini-sumo. Questi collegati in serie attraverso un morsetto:

{% include figure image_path="/assets/images/tutorial/beam/Batte.jpg" alt="Batterie" caption="Batterie" %}

Il robot adesso è funzionante, infatti se accendiamo già questo potrà muoversi tranquillamente sul campo. A patto che vengano “ponticellati” i sensori GD2D15 per la ricerca dell’avversario.

Questo ci può risultare molto utile se dobbiamo testare il robot.

Per poter far ciò bisogna cortocircuitare il primo ed il secondo piedino come in foto:

{% include figure image_path="/assets/images/tutorial/beam/ponte.jpg" alt="Collegamenti" caption="Collegamenti" %}

Possiamo provare il nostro robot sul campo e vedere il funzionamento dei sensori.
Come noteremo dalle foto, sono evidenziati anche i trimmer, questi servono per tarare le rotazioni a sinistra ed a Destra del Robot ed il timer dei 5 secondi.

{% include figure image_path="/assets/images/tutorial/beam/Sharp.jpg" alt="Sharp Montati" caption="Sharp Montati" %}

Gli ultimi e più importanti sensori da montare sono i GP2D15, e per poter far ciò prima di tutto dovremo recuperare i cavetti ed i sensori stessi, dopo averli collegati ed averli incollati alla benna come appare in foto dovremo collegarli sulla scheda nel seguente ordine.

Per quanto riguarda i sensori di Linea precedentemente montati, i cavetti andranno collegati nel seguente ordine sulla scheda, tenendo presente che i sensori si devono trovare all’incirca ad 1cm da terra per poter perfettamente rilevare il colore del campo, come possiamo vedere in foto.

{% include gallery id="montaggio" caption="montaggio finale" %}

Finalmente il robot funziona e potremo farlo gareggiare sul campo.

{% include figure image_path="/assets/images/tutorial/beam/finito.jpg" alt="Robot Finito" caption="Robot Finito" %}

Questo robot è arrivato **3° alla robofesta di Pisa** del **21 gennaio 2006**, con il Nome di **Enigma**.

Vi includo la tabella con le misure e le specifiche di questo robot montato:

|     | Dimensioni |
|-----|------------|
| Base | 10cm X 10cm |
| Altezza | 8,5 cm |
| Peso | 477 grammi |
| Peso senza batterie | 328 grammi |
