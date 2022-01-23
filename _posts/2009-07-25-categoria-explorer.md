---
title: "Explorer"
excerpt: "Lo spirito delle competizioni dei robot Explorer rispecchia la ricerca del Minotauro da parte di Teseo. Nelle gare il Minotauro è rappresentato da un serie di fonti di luce, suono e gas che vengono disposte lungo un labirinto insidioso e pieno di ostacoli."
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/explorer/CampoSenior.jpg
  teaser: /assets/images/posts/explorer/CampoSenior.jpg
categories:
  - Gare di robotica
tags:
  - explorer
---

Di che si tratta? Torniamo indietro nel tempo e trasferiamoci in Grecia, quasi 2000 anni prima della nascita di Cristo. In quel tempo, all’epoca del Minotauro, i cretesi combattevano contro i greci. Fu allora che Minosse, re dell’isola di Creta, diede incarico a Dedalo di costruire un labirinto per rinchiudervi il Minotauro; il labirinto avrebbe dovuto essere talmente intricato da impedire a chiunque di uscirne. Dedalo, nella speranza di guadagnarsi la fiducia del sovrano, costruì quindi l’edificio noto alla storia come il Labirinto di Cnosso.

Vuole poi la leggenda che il Minotauro venisse rinchiuso nel labirinto e che, ogni anno, sette giovani e sette fanciulle di Atene, sconfitta dal re di Creta, gli venissero sacrificati per saziare la sua fame di carne umana.

Il sacrificio fu ripetuto due volte, ma la terza volta giunse a Creta Teseo, figlio di Etra e del sovrano di Atene Egeo, con l’intento di porre fine ai sacrifici. L’impresa era molto difficile non solo perchè avrebbe dovuto uccidere il Minotauro, ma  anche perchè, una volta entrati nel Labirinto, era quasi impossibile uscirne.

Teseo, per poter raggiungere Creta, finse di essere uno dei fanciulli da sacrificare. A Creta il giovane si innamorò di Arianna, figlia di Minosse, che lo aiutò nell’impresa. Quando venne il suo turno egli entrò nel labirinto dipanando lungo la strada un rocchetto di filo, fornitogli da Arianna. Teseo giunse al cospetto del mostro, lo uccise e, riavvolgendo il filo, riuscì ad uscire dal labirinto. Finì così l’orrendo sacrificio che era stato imposto da Minosse agli ateniesi e Teseo ed Arianna fuggirono da Creta e si recarono a Nasso.

Non appena sbarcati, Teseo dichiarò ad Arianna che aveva finto di amarla per salvarsi dalla prova del labirinto e abbandonò la fanciulla sulla spiaggia.

Lo spirito delle competizioni dei robot Explorer rispecchia la ricerca del Minotauro da parte di Teseo. Nelle gare il Minotauro è rappresentato da un serie di fonti di luce, suono e gas che vengono disposte lungo un labirinto insidioso e pieno di ostacoli. Il principale avversario dei robottini è il tempo a loro disposizione: solo tre minuti. Entro questo tempo gli Explorer devono individuare tutte le sorgenti e contemporaneamente devono saper evitare, possibilmente ricordandoli, gli ostacoli.

Scenderemo adesso nel dettaglio e vedremo come si costruisce, in linea generale, un robot Explorer. Vedremo inoltre come è organizzata una gara e quali ne sono le regole.

# Le Categorie

Esistono tre categorie di Explorer:

1. Explorer Junior Programmabili
2. Explorer Junior Analogici
3. Explorer Senior

## Explorer Junior

{% include download.html name="regolamentoexplorerjuniorv2.pdf" url="https://drive.google.com/file/d/1291_nZsUCJzSM-2j9rsqcqtHCUDOF1X9/view?usp=sharing" %}

{% include figure image_path="/assets/images/posts/explorer/CampoJunior.jpg" alt="Campo explorer junior" caption="Campo explorer junior" %}

Le due categorie Explorer Junior sono nate per spingere i ragazzi del 2° anno delle scuole superiori a cimentarsi nella costruzione di piccoli robottini esploratori. Il campo e le regole sono molto più semplici di quelli della categoria Senior, ciò non toglie che la difficoltà di costruzione e l’impegno richiesto siano quasi equivalenti.

Il campo di gara è di 2 metri per 2. Le misure dei robot non possono superare i 20 x 20 x 25 cm (sensori di contatto esclusi) ed i limiti vengono fatti rispettare in modo rigoroso.

I nostri robottini devono cercare sei fonti di luce disposte casualmente all’interno del labirinto. Non appena un robot trova una fonte di luce, il direttore di gara la spegne, per consentire al robot di riprendere la ricerca delle fonti di luci rimanenti.

Ma cosa hanno di differente le categorie degli Explorer Junior Programmabili e degli Explorer Junior Analogici? L’elettronica di controllo!
Nella prima categoria, vale a dire quella degli “Explorer Junior Programmabili”, i movimenti del robot e la gestione dei sensori viene effettuata da un microcontrollore; tra i più comunemente utilizzati ci sono i controller integrati della Microchip, grazie alla semplicità dello schema elettrico.

Mentre, per quanto riguarda gli “Explorer Junior Analogici”, i sensori ed i motori vengono controllati in modo puramente analogico, quindi con relè, transistor e diodi e senza il supporto di un programma.

## Explorer Senior

{% include download.html name="regolamentoexplorerseniorv1.pdf" url="https://drive.google.com/file/d/1ZMFnU1YKtMnGodgD42rEafVUOn6CTZ8D/view?usp=sharing" %}

{% include figure image_path="/assets/images/posts/explorer/CampoSenior.jpg" alt="Campo explorer senior" caption="Campo explorer senior" %}

La categoria degli Explorer Senior è quella più complessa ed impegnativa, ma più interessante.

Questi robot devono percorrere un labirinto chiuso, quindi senza vie di uscita, di 3 metri per 2. All’interno del labirinto essi devono cercare e trovare tre fonti di luce, tre fonti di suono e tre fonti di gas (il gas in questione non è altro che alcool etilico). Ogni volta che trovano una di queste sorgenti, i robot devono illuminare i propri LED e fermarsi per tre secondi, in modo tale da permettere agli arbitri ed ai giudici di convalidare il punto.

I colori utilizzati sono standard e sono indicati dal regolamento:

| Colore | Sorgente | Punteggio |
|--------|----------|-----------|
| Rosso | Gas | 1 |
| Verde | Luce | 2 |
| Giallo | Suono | 3 |

Le misure di questi robot devono rientrare entro un cubo di 30 cm di lato. La principale difficoltà che i costruttori devono affrontare è la scrittura di un programma di controllo che sia in grado, gestendo un opportuno numero di sensori, di individuare le sorgenti, accorgersi delle pareti e degli ostacoli e non perdersi nei meandri del labirinto.

Ma non è tutto! Le cose sono ancora più complicate. Infatti i robot devono percorrere il labirinto mentre tutte le fonti di luce, di suono e di gas sono sempre attive. Il robot deve quindi sapersi allontanare da una sorgente per ricercare una nuova fonte e deve evitare di individuare la stessa fonte più di una volta. Chi scrive il software deve quindi realizzare un buon sistema di mappatura del labirinto e delle sorgenti.

Nella figura 3 c’è un esempio di campo Explorer, che, come si può vedere, è ricco di vicoli ciechi, di ostacoli e di sorgenti molto vicine tra loro. I semicerchi o i cerchi delimitano lo spazio in cui il robot si deve fermare per guadagnare il punto relativo alla sorgente.

Inoltre, per ogni errore, i robot subiscono una penalità consistente:

| Ostacolo | Punteggio |
|----------|-----------|
| Ostacolo Generico | -1 |
| Sorgente o Ostacolo contenente la sorgente | -2 |

# Cosa c’è bisogno per poter costruire un Robot Explorer?

{% include figure image_path="/assets/images/posts/explorer/Sensori.jpg" alt="Sensori di contatto e infrarossi" caption="Sensori di contatto e infrarossi" %}

Innanzitutto sono necessari sensori per la rilevazione della presenza di pareti od ostacoli: i più utilizzati sono i sensori infrarossi per le lunghe distanze ed i sensori di contatto, chiamati “baffi”, che permettono di accorgersi dell’imminente urto con un ostacolo e di cambiare percorso.

{% include figure image_path="/assets/images/posts/explorer/Sensori2.jpg" alt="Fotoresistori e fotodiodi a confronto" caption="Fotoresistori e fotodiodi a confronto" %}

I sensori più utilizzati per trovare le fonti di luce sono i fotoresistori, particolari componenti che cambiano la loro resistenza quando sono irradiati da una luce, oppure i fotodiodi, che conducono quando vengono colpiti dalla luce.

![Microfono]({{ '/assets/images/posts/explorer/microfono.jpg' | relative_url }})

Per l’individuazione dei suoni vengono utilizzati microfoni tarati per ricevere soltanto onde di 4 KHz, per non confondere il robot con il suono delle voci del pubblico durante le competizioni.

![Rilevatore di Gas]({{ '/assets/images/posts/explorer/gas.jpg' | relative_url }})

Infine, per poter trovare all’interno del labirinto le fonti di alcool etilico, vengono utilizzati molto spesso sensori del tipo di quelli utilizzati in cucina per gli allarmi contro le fughe di gas.

Nessuna delle categorie Explorer è soggetta a limiti di peso: questo permette di montare motori più potenti e batterie più pesanti.
Le batterie più usate sono quelle al piombo: grazie alla loro lunga durata ed al loro notevole amperaggio, infatti, riescono a mantenere attivi tutti i sensori per tutto il periodo di gara.

# Un robot explorer

La categoria dei robot Explorer è la più istruttiva ed interessante, ed infatti è la più adottata negli Istituti Tecnici; consente infatti di mettere in pratica ciò che è stato insegnato durante l’anno scolastico.

Chi vuole avere maggiori informazioni sulle diverse categorie Explorer può chiedere nel nuovo forum di minisumo.net. All’interno del forum professori e partecipanti alle competizioni vi potranno dare consigli per costruire il miglior robot possibile e magari per partecipare e vincere nelle gare di categoria.

{% include figure image_path="/assets/images/posts/explorer/AndChipIII.jpg" alt="AndChipIII" caption="AndChipIII" %}

| Nome | AndChip III |
|------|-------------|
| Costruttore | Andrea Massimi |
| Microcontrollore | PIC Micro 16F877 |
| Motori | 2 motori ridotti controllati da un ponte H (L293D) |
| Sensori di Luce | 5 Fotodiodi |
| Sensori di Suono | 2 Mic. Amplificati e controllati da un ToneDecoder (NE567) |
| Sensori di Gas | ST-11 Amplificato (LM358) |
| Altezza | 195 mm |
| Larghezza | 190 mm |
| Profondità | 175 mm |
| Sensori Urto | Sharp GP2D120, baffi |
| Metodo gestione Sensori |   |
|   | Luce: Analogico (0V=buio, 5V=max luce) |
|   | Suono: Digitale (0= suono a 4 khz, 1= altri suoni) |
|   | Gas: Analogico (Val. crescente quando vi è GAS) |
|   | Urto: Analogici (0V= nessun ostacolo, 3.5V= ostacolo vicino) |