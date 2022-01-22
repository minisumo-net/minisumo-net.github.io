---
title: "La seriale nei PIC"
excerpt: "La seriale nei PIC"
permalink: /tutorial/la-seriale-nei-pic
author: "Raffaello Bonghi"
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/seriale-pic/portaseriale.jpg
  teaser: /assets/images/tutorial/seriale-pic/portaseriale.jpg
---

Molto spesso ci capita di dover permettere al nostro PIC di comunicare con il computer o con strumenti che utilizzano la porta seriale.

I PIC della Microchip integrano al loro interno un set necessario per la comunicazione seriale, ma per poterla utilizzare dovremo utilizzare la porta di comunicazione RS232.

{% include figure image_path="/assets/images/tutorial/seriale-pic/max232.gif" alt="MAX232" caption="MAX232" %}

Molto importante infatti è adattare i livelli di tensione tra il PIC e gli standard RS232.
Questo standard nacque nei primi anni sessanta ad opera della “Elctronic Industries Association”. Permetteva di far comunicare i primi grandi computer tra di loro.

Nel corso degli ultimo decennio questa porta è stata fondamentale per la comunicazione di tutte le periferiche al computer anche se oramai la nuova porta di comunicazione chiamata USB sta soppiantando questo tipo di comunicazione.

# Come funziona

{% include figure image_path="/assets/images/tutorial/seriale-pic/portaseriale.jpg" alt="Porta seriale" caption="Porta seriale" %}

I più importanti PIC della microchip dalla serie 12F alla serie 18F integrano al loro interno tutto il necessario per la comunicazione RS232 tranne il convertitore di stati logici che trasformi i livelli di tensione TTL del PIC (0v , 5v) a quelli dello standard RS232 (-12v , +12v).

L’integrato più utilizzato è il MAX232 che è in grado di alzare la tensione permettendo di poter interfacciarsi con gli standard.

Come si può notare dalla figura si può notare con facilità che grazie all’utilizzo dei condensatori venga raddoppiata la tensione.

{% include figure image_path="/assets/images/tutorial/seriale-pic/pompacondensatori.jpg" alt="Carica scarica condensatori" caption="Carica scarica condensatori" %}

Infatti basta pensare che il condensatore C2 preleva acqua da una fonte e la riversa in un secondo contenitore (C1) posto a maggiore altezza. Più in dettaglio:

Inizialmente il condensatore C2 viene connesso tra massa e Vcc; quindi la corrente (in blu) carica C2 alla tensione di alimentazione (in giallo). Quindi Vc2 = Vcc
C2 viene successivamente connesso tra Vcc ed un secondo condensatore C1; la tensione ai capi di C1 deve essere uguale alla somma di Vcc e Vc2 e quindi C2 si scarica verso C1, che aumenta la propria tensione rispetto a massa
Il processo è ripetuto fino a quando la tensione ai capi di C1 è uguale a 2Vcc: in questo caso infatti C2 non si può più scaricare.
Da notare che, nel funzionamento normale, il processo non può mai interrompersi in quanto il carico collegato a C1, non disegnato, assorbe corrente e quindi tende a scaricare C2 stesso.

Analogamente le figure C e D mostrano l’inversione di tensione:

Inizialmente C2 è caricato alla tensione di alimentazione (magari, come nel disegno da 2Vcc, ricavata con il precedente circuito)
Quindi C2 è connesso tra massa e C1 avendo cura di invertire le polarità. In questo modo C1 si carica a -2Vcc
Il limite dei circuiti a pompa di carica è la limitata quantità di corrente disponibile: infatti se prelevo corrente da C1 questo tende a scaricarsi, facendo scendere la tensione; la corrente generata da un circuito integrato tipo Max232 è generalmente tutta utilizzata per il solo funzionamento del driver e quindi non è disponibile per altri circuiti.

Lo schema di montaggio basilare
Ecco lo schema circuitale che mostra come collegare il MAX232 per farlo funzionare come convertitore di stati logici per il PIC.

{% include figure image_path="/assets/images/tutorial/seriale-pic/max232.jpg" alt="Schema adattatore seriale" caption="Schema adattatore seriale" %}

Su Rx e Tx verranno collegati i piedini del PIC dedicati alla comunicazione seriale.