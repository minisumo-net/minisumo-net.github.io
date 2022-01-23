---
title: "Costruiamo un carica batterie Litio"
excerpt: "Con questa guida realizzeremo un carica batterie che ci permette di caricare le litio Lipo."
permalink: /guide/strumentazione/costruiamo-un-carica-batterie-litio/
redirect_from:
  - /tutorial/costruiamo-un-carica-batterie-litio
author: "Raffaello Bonghi"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/carica-batterie-litio/caricabatterie.jpg
  teaser: /assets/images/tutorial/carica-batterie-litio/caricabatterie.jpg
---

Infatti come ben sappiamo queste hanno bisogno di un carica batterie particolare che permetta di caricarle correttamente evitando di farle esplodere o rovinarle.

# La carica delle Celle

La corrente di carica deve essere inferiore alla massima corrente di carica indicata nelle specifiche tecniche. Logicamente cariche di corrente superiori danneggiano permanentemente le prestazioni della batteria.

Anche il voltaggio di carica non deve superare quello indicato dalle specifiche tecniche, perché i valori superiori danneggiano anche in questo caso le prestazioni della batteria, e violano le caratteristiche di sicurezza degli elementi, molto spesso possono portare anche all’esplosione.

La stessa cosa vale per la polarità, infatti, non rispettandola si rischia di far esplodere la batteria, soprattutto durante il ciclo di ricarica.


# Come Funziona

Il carica batterie è un elemento fondamentale per utilizzare queste batterie, infatti queste batterie **NON** possono essere caricate con un carica batterie normale, ma con un carica batterie particolare capace di erogare una tensione ed una corrente capace di non far esplodere le batterie.

Dobbiamo sapere che queste batterie fino al 70% della loro carica la carica tensione deve essere al massimo per poterle caricare, poi mano a mano che la batteria si inizia a raggiungere la sua carica completa, la tensione in uscita del carica batterie in uscita deve diminuire fino a raggiungere a diventare nulla.

{% include figure image_path="/assets/images/tutorial/carica-batterie-litio/pict0034.jpg" alt="Batterie Litio" caption="Batterie Litio" %}

# Costruzione

Lo schema che ho utilizzato è il più comune presente su internet, funziona molto bene e carica perfettamente le batterie in un paio d’ore.

Su X2-1 entra la tensione di 15v capace di caricare le batterie… il regolatore di tensione LM317 regola la tensione in uscita che a seconda delle celle presenti sarà con un voltaggio di cut-off di (4.20±0.05)Volt o per 2 celle di (8.40±0.05)Volt e per finire con 3 celle (12.60±0.05)Volt.

Tutte le resistenze presenti, da R9 a R16 invece servono per la corrente in uscita che a seconda della quantità delle celle presenti in serie aumentano o diminuiscono la corrente in uscita.

Vi presento la tabella di regolazione della corrente e del numero di celle del regolatore.

## Il Circuito

Come vediamo, il circuito qui sbrogliato occupa poco spazio, permette di caricare fino a 3 celle in parallelo con amperaggi in uscita di 985mA.

Dalle misure di 6,5 x 4,5 cm utilizza componenti facilmente recuperabili in un qualsiasi negozio di elettronica, con passo standard, il suo costo è sulla 10€.

[Scarica qui il circuto e lo sbroglio](https://github.com/minisumo-net/LithiumBatteryCharger){: .btn .btn--success}

{% include figure image_path="/assets/images/tutorial/carica-batterie-litio/Schema.png" alt="Schema elettrico" caption="Schema elettrico" %}

L’elenco i componenti richiesti per la realizzazione

| Resistenze |        |
|------------|--------|
| R1-R4 | 470Ω 5% ¼Watt |
| R5 | Trimmer Lineare 470Ω |
| R6-R9 | 47Ω 5% ¼Watt |
| R10 | 1KΩ 5% ¼Watt |
| R11 | 10Ω 5% ¼Watt |
| R16 | 1Ω 5% 1Watt |

| Condensatori |        |
|------------|--------|
| C1-C2 | 0,1μF Poliestere |

| Integrati |        |
|------------|--------|
| U1 | LM317T |

| Diodi |        |
|------------|--------|
| D1 | 1N4001 |
| DS1 | LED Rosso |

| Semiconduttori |        |	
|------------|--------|
| Q1-Q2 | 2N2222A |

| Altro |        |
|------------|--------|
| Dissipatore |       |
| Interruttori | DIP16, 8 interruttori |
| X1-X2 | Connettori 2 posti |
| Scatola | Per contenere il carica batterie |

# La tabella di regolazione

Vi presento la tabella di regolazione della corrente e del numero di celle del regolatore.

{% include figure image_path="/assets/images/tutorial/carica-batterie-litio/Circuito.png" alt="Circuito" caption="Circuito" %}

**Tabella regolazione Amperaggio uscita corrente**

| S3 | S4 | S5 | S6 | S7 | S8 |    |
|----|----|----|----|----|----|----|
| OFF | OFF | OFF | OFF | OFF | OFF | 10 mA |
| ON | OFF | OFF | OFF | OFF | OFF | 24 mA |
| OFF | ON | OFF | OFF | OFF | OFF | 62 mA |
| ON | ON | OFF | OFF | OFF | OFF | 75 mA |
| OFF | ON | ON | OFF | OFF | OFF | 127 mA |
| OFF | ON | ON | ON | OFF | OFF | 192 mA |
| OFF | OFF | ON | ON | ON | OFF | 260 mA |
| ON | ON | ON | ON | ON | OFF | 335 mA |
| OFF | OFF | OFF | OFF | OFF | ON | 650 mA |
| OFF | ON | OFF | OFF | OFF | ON | 725 mA |
| OFF | ON | ON | OFF | OFF | ON | 790 mA |
| OFF | OFF | ON | ON | ON | ON | 907 mA |
| OFF | ON | ON | ON | ON | ON | 972 mA |
| ON | ON | ON | ON | ON | ON | 985 mA |

Questa altra tabella serve per quantificare le celle che andranno collegate al carica batterie

**Tabella Celle**

| S1 | S2 |    |
|----|----|----|
| OFF | OFF | 1 Cella = 4.2v |
| ON | OFF | 2 Cella = 8.4v |
| ON | ON | 3 Cella = 12.6v |

Ad esempio la configurazione per un pacco di 2 celle collegate in serie è da 1100mAh è:

| switch | status | 
|--------|--------|
| S1 | ON |
| S2 | OFF |
| S3 | OFF |
| S4 | OFF |
| S5 | OFF |
| S6 | OFF |
| S7 | OFF |
| S8 | ON |

Quindi 8.4v e 650mA in uscita

Grazie a questo carica batterie riusciremo a caricare senza problemi le batterie al Litio polimeri riuscendo così ad evitare problemi durante la carica.

Ricordiamo sempre che è consigliato regolare il carica batterie prima di mettere in carica le batterie ed evitare quindi che si possano creare problemi durante il ciclo di ricarica.

{% include figure image_path="/assets/images/tutorial/carica-batterie-litio/pict0031.jpg" alt="Risultato Finale" caption="Risultato Finale" %}

[Scarica qui il circuto e lo sbroglio](https://github.com/minisumo-net/LithiumBatteryCharger){: .btn .btn--success}