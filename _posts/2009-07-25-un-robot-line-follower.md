---
title: "Un robot line-follower"
excerpt: "Il robot sarà dotato di 2 ruote e due punti di appoggio omnidirezionali, di un microprocessore PIC 16F876"
author: "Matteo Camporeale"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/posts/line-follower/23 robot2.jpg
  teaser: /assets/images/posts/line-follower/23 robot2.jpg
categories:
  - Robots
tags:
  - Line Follower
---

Con questo progetto ho voluto realizzare un robot in grado di seguire autonomamente una linea bianca tracciata su di una pavimentazione nera e che sia in grado di fermasi in caso vi siano ostacoli sul percorso.
Il robot sarà dotato di 2 ruote e due punti di appoggio omnidirezionali, di un microprocessore PIC 16F876 che si occuperà della gestione di tutta la parte di controllo automatico ed è inoltre è necessario l’uso di 4 sensori, 3 per il rilevamento della linea e 1 per il rilevamento degli ostacoli lungo il percorso.


# Studio del problema

Per facilitare lo studio e la realizzazione del progetto ho deciso di seguire un approccio modulare al problema iniziale, in pratica ho cercato di sezionare il problema in diversi blocchi dove ognuno rispondeva ad una parte del problema.
Questo metodo mi a portato ha suddividere il progetto in questo schema a blocchi:

{% include figure image_path="/assets/images/posts/line-follower/01 schema.jpg" alt="Schema principale" caption="Schema principale" %}

Dallo schema si evince che sarà necessario realizzare tre schede elettroniche ognuna dedita a una specifica funzione. L’elettronica dovrà essere in grado di controllare 2 motori separati che a loro volta azioneranno una delle 2 ruote, cosi che variando la velocità di rotazione di un motore sia possibile generare un cambio di direzione del robot.
Sarà poi necessario studiare il sistema di collegamento fra i vari componenti dello schema, ed inoltre sarà necessario studiare un telaio sul quale assemblare il tutto.
Di seguito andrò ad analizzare ogni singolo blocco e a spiegarne le principali funzioni.

# Ricerca e sviluppo delle singole parti che compongono il progetto

## Meccanica

Per lo sviluppo della parte di meccanica che compone il Robot ho deciso di servirmi di un motoriduttore già presente sul mercato, l’uso del motoriduttore è stato necessario in quanto i motori non possono essere collegati direttamente alle ruote in quanto non avrebbero la coppia necessaria per spostare tutta la struttura.

La scelta è caduta su questo motoriduttore in kit di montaggio della Tamiya Twin Motor Gearbox

{% include figure image_path="/assets/images/posts/line-follower/02 TamiyaTwinMotor.jpg" alt="Tamiya TwinMotor" caption="Tamiya TwinMotor" %}

Questo doppio motoriduttore è molto compatto(7.5cm di lunghezza), contiene due piccoli motori DC che trasmettono il moto a due assi esagonali da 3mm separati. Si può assemblare in due diversi rapporti di riduzione: veloce 58:1 o lento 203:1.

In entrambi i casi i motori producono una elevata potenza.

Per quanto riguarda le ruote invece ho scelto delle comuni ruote in plastica ricoperte in gomma, con un diametro di 58mm.
Come punti di appoggio omnidirezionali mi sono affidato ad un altro prodotto presente sul mercato sempre della Tamiya le Ball Caster.

{% include figure image_path="/assets/images/posts/line-follower/03 ballcaster.jpg" alt="Ballcaster" caption="Ballcaster" %}

In pratica sono formate da una piccola sfera di acciaio Inox che scorre su tre rullini anch’essi in acciaio.
Il Ball Caster può essere assemblato in due modi diversi per ottenere un’altezza totale di 25 mm o 35 mm.
Il telaio è stato realizzato con un materiale plastico di facile lavorazione e si basa tutto su di un piano al di sotto del quale è stato fissato il motoriduttore e i sensori, mentre al di sopra sono state disposte schede elettroniche, batterie e pulsanti.

{% include figure image_path="/assets/images/posts/line-follower/04 telaio.jpg" alt="Telaio" caption="Telaio" %}

## I sensori

I sensori scelti sono tutti sensori ad infrarossi considerato l’elevato rapporto qualità prezzo. I tre sensori che si occupano del rilevamento della linea sono della Fairchild, più precisamente il modello è QRB1134. (In allegato il datasheet completo)

![QRD1114]({{ '/assets/images/posts/line-follower/05 QRD1114.jpg' | relative_url }})

Il sensore QRB1134 è un sensore ad infrarossi che contiene due elementi, uno che emette un fascio di luce infrarosso e l’altro che legge la luce riflessa. E’ dotato di filtro ottico per ridurre le interferenze della luce ambientale. Distanza ottimale di lettura 5 mm.

Invece il sensore scelto per rilevare la presenza di ostacoli lungo il percorso è lo Sharp GP2D120. (In allegato il datasheet completo)

![GP2D15]({{ '/assets/images/posts/line-follower/06 GP2D15.jpeg' | relative_url }})

Sensore Infrarosso che restituisce una lettura analogica, il valore di tensione che possiamo prelevare in uscita varia in maniera lineare con il diminuire della distanza dell’oggetto rilevato. Questo modello è in grado di rilevare oggetti posti da 4 a 50 cm di distanza.

# Scheda di interfaccia tra sensori e PIC

Lo sviluppo di questa scheda si è reso necessario per poter inserire l’elettronica di contorno necessaria per il funzionamento dei 4 sensori e per permettere di avere tutti i morsetti utilizzati per collegare i cavi dei sensori all’elettronica.

Tutti i sensori verranno usati in analogico cosi da avere una migliore e più precisa lettura, la conversione analogico-digitale ci penserà il PIC con il suo A/D integrato.

Per lo scopo è stato realizzato questo circuito: (In allegato schematico, master e layout).

{% include figure image_path="/assets/images/posts/line-follower/07 sensori.jpg" alt="Sensori" caption="Sensori" %}

I sensori QRB1134 per funzionare hanno bisogno che il led infrarossi interno venga alimentato e ciò è stato fatto collegando in serie i tre led, cosi da risparmiare corrente, e mettendo un trimmer R5 che grazie alla sua resistenza variabile permette di tarare i sensori una volta montati cosi da trovare il valore che consente un miglior riconoscimento della linea. Il trimmer usato è da 100 ohm e in serie è stata inserita una resistenza di limitazione da 33 ohm per impedire che portando il trimmer a 0 i led possano bruciarsi.

R2, R3, R4 sono resistenze di pull-up che tengono a Vcc il segnale di uscita che poi il transistor interno dei sensori si occuperà di mandare gradualmente a massa a seconda di quanta luce viene riflessa dalla superficie illuminata dal led infrarosso, seguendo circa questi valori:

* Massima riflessione 3,8v
* Minima riflessione 0,6v

Il valore di R2, R3, R4 è di 10 Kohm come tutte le resistenze di pull-up/down utilizzate in questo progetto.

C1,C2,C3 sono condensatori da 100nF utilizzati per filtrare il segnale in uscita.

Sulla scheda poi al posto dei sensori SENS_SX, SENS_DX, SENS_C sono stati inseriti morsetti a 4 pin cosi da semplificare i collegamenti con i cavi dei sensori che poi verranno montati a distanza dalla scheda.

Per quando riguarda invece il quarto sensore lo Sharp, verrà collegato al morsetto X7, il sensore ha bisogno della Vcc e della massa per funzionare ed in uscita ci fornirà un valore di tensione che varia linearmente con il diminuire della distanza dell’oggetto rilevato.
Inoltre tra l’uscita di questo sensore e massa è stato inserito un piccolo condensatore da 33uF per stabilizzare il segnale.

Tutti i segnali vengono mandati al connettore “SEGNALI” che tramite una piattina a 10 pin li porterà all’A/D del PIC.
L’alimentazione viene prelevata tramite il connettore “PWR1” dalla scheda di potenza e poi riportata tramite “PWR2” alla scheda del microcontrollore.

{% include figure image_path="/assets/images/posts/line-follower/08 sensori.jpg" alt="Scheda sensori" caption="Scheda sensori" %}

Ecco la scheda finita e già montata sul telaio del robot.

## Scheda di potenza

Questa scheda ha il compito principale di fornire la corrente necessaria al funzionamento dei due motori (circa 1A a testa) e di interfacciarsi al pacco batterie.

Le batterie utilizzate per fornire l’alimentazione ai motori sono 3 pile AA da 1,5 volt in serie capaci di erogare circa 2,7Ah, mentre tutta la sezione di elettronica verrà alimentata da una batteria da 9v.

Per lo scopo è stato realizzato questo circuito: (In allegato schematico, master e layout).

{% include figure image_path="/assets/images/posts/line-follower/09 potenza.jpg" alt="Schema per scheda potenza" caption="Schema per scheda potenza" %}

I due integrati fondamentali di questa scheda sono l’LM7805 e L298 (datasheet allegati). L’LM7805 è un regolatore di tensione che si occuperà di stabilizzare a 5v la tensione in ingresso dalla batteria da 9v. C3 è un condensatore da 100nF utilizzato per stabilizzare ulteriormente la tensione in uscita dal regolatore. La batteria da 9v avrà il + collegato al morsetto CON-3 e il – al morsetto CON-2.
L’L298 è un ponte ad H integrato, utilizzato per pilotare i 2 motori. Sopporta una corrente di picco di 6A e un carico continuo di 2.5A per canale. Sul pin VS (n° 4) viene data la tensione che verrà poi fornita ai motori, nel nostro caso è collegato al morsetto CON-1.

A questo morsetto verrà poi collegato il + del pacco batterie da 4,5v mentre il – sarà collegato in comune sul morsetto CON-2.

L’L298 è equipaggiato internamente con una protezione contro il surriscaldamento, per carichi superiori ai 0,6A è necessario equipaggiare l’integrato con un dissipatore di calore cosi da non far intervenire la protezione.

I due pin Sens dell’L298 permettono di controllare quanta corrente viene utilizzata dai motori, visto che nel nostro caso non era necessario questo tipo di controllo abbiamo collegato a massa questi 2 pin come spiegato nel datasheet.

Gli 8 diodi sono di tipo Schottky BS160 utilizzati come diodi di ricircolo necessari per evitare che le sovratensioni, generate dalle bobine dei motori, si scarichino sui transistor del ponte H distruggendolo.

C1 è un semplice condensatore da 100nF utilizzato per filtrare l’alimentazione del L298 mentre C2 è un condensatore elettrolitico da 470uF da almeno 63V, viene preso di una tensione cosi alta perché sarà sottoposto a notevoli sovratensioni generate dai motori.

Il suo scopo è quello di aiutare le batterie a mantenere la tensione fornita ai motori il più costante possibile indipendentemente dalla corrente richiesta.

Al connettore da 16pin “Segnali” vengono riportati tutti i pin necessari per il controllo del ponte H. i 2 Enable uno per canale e i 4 pin di Input, 2 per canale.

I 2 motori verranno collegati ai 4 morsetti M, il primo motore su M1-1,M1-2 ed il secondo su M2-1,M2-2.

Al connettore “PWR” vengono portate Vcc (5v stabilizzati) e massa che serviranno per alimentare tutte le altre schede del progetto.

# Teoria sul PONTE H

## Controllo motori On-Off

I motori DC possono essere controllati in vari modi: il pilotaggio più semplice è quello ON/OFF, che permette di comandare il motore solo alla massima velocità di rotazione in un verso (interruttore ON) oppure fermarlo (interruttore OFF)

Questo controllo può essere implementato con un interruttore (es. un mos o un transistor) e con un diodo di ricircolo necessario per evitare danni al resto del circuito (il motore è un carico con una componente induttiva).

{% include figure image_path="/assets/images/posts/line-follower/10 m2.jpg" alt="Singolo Motore" caption="Singolo Motore" %}

*Schema del pilotaggio ON-OFF: quando l’interruttore è aperto il motore è fermo, quando è chiuso gira alla massima velocità. A destra un esempio di implementazione*

## Il ponte ad H

Il tipo di controllo appena presentato non permette né la regolazione della velocità del motore né la possibilità di far girare il motore in entrambi i versi di rotazione.
Per far girare il motore nel verso opposto è necessario infatti invertire il segno della corrente che passa all’interno del motore stesso, per far ciò si usa un circuito chiamato ponte H costituito da 4 interruttori comandati e da 4 diodi di ricircolo.

{% include figure image_path="/assets/images/posts/line-follower/11 m1.jpg" alt="Schema semplificato" caption="Schema semplificato" %}

*Schema semplificato di un ponte H*

Attivando i transistor A1 e B2 la corrente scorre nel motore in un verso mentre attivando i transistor B1 e A2 la corrente scorre nel verso opposto. E’ da evitare la configurazione in cui sono accesi entrambi i transistor A o entrambi i transistor B infatti la corrente di corto circuito su un lato del ponte potrebbe creare seri danni al ponte stesso o al circuito di alimentazione.

## Ponti H discreti e Ponti H integrati

Esistono due tipi di ponti H: i ponti H discreti, costituiti da componenti sparsi come transistor e diodi e i ponti H integrati, in questo caso tutto il circuito è racchiuso in un package plastico di tipo DIP (dual in-line package) o simile. I ponti H integrati sono molto versatili e, oltre a garantire una bassa occupazione di area nel circuito (in alcuni casi, come il SN754410 e l’ L293D, contengono anche i diodi di ricircolo), hanno buone prestazioni (l’ L298 può fornire fino a 2,5A per ponte), possono essere montati in parallelo per ottenere alte correnti e riescono a lavorare in un intervallo di tensioni di alimentazione molto ampio (da 6V a 48V circa a seconda del modello).

{% include figure image_path="/assets/images/posts/line-follower/12 m3.jpg" alt="Struttura Ponte H" caption="Struttura Ponte H" %}

*Schema di funzionamento interno di un ponte H integrato*

Tale integrato è costituito da quattro mezzi ponti H ognuno dei quali è costituito da due transistor e da una logica che li comanda in modo da accenderne solo uno alla volta: quando il transistor superiore di un mezzo ponte è in conduzione quello inferiore sarà necessariamente spento e viceversa. E’ inoltre presente un comando di Enable che permette di inibire il funzionamento di una coppia di mezzi ponti.

Si può inoltre notare la presenza di due pin dedicati alla connessione di una resistenza di
Sens per monitorare la corrente assorbita dal motore (utile per controllare l’assorbimento di corrente cosi da evitare rischiosi stalli del motore).

Ricapitolando, per ognuno dei due ponti presenti nell’integrato abbiamo a disposizione
due ingressi di controllo per permettere il passaggio di corrente in un verso e un ingresso
di Enable per accendere e spegnere il ponte.

{% include figure image_path="/assets/images/posts/line-follower/13 fotopotenza.jpg" alt="Scheda di potenza" caption="Scheda di potenza" %}

*Ecco la scheda assemblata e già montata sul telaio del robot.*

# Scheda a microcontrollore

Questa scheda è il vero cuore del robot, in questa scheda verrà inserito il microcontrollore PIC 16F876.
Per spiegare il funzionamento di questa scheda è necessario suddividerla in ulteriori blocchi.

Ecco lo schema che ne evidenzia le varie parti:

{% include figure image_path="/assets/images/posts/line-follower/14 pic.jpg" alt="Microcontrollore" caption="Microcontrollore" %}

Per poter controllare il ponte H presente nella scheda di potenza è stato necessario inserire un buffer invertente cosi da poter realizzare un controllo Locked Anti-Phase PWM (LAP).

Il “Gruppo interfaccia per comunicazione seriale” si è rivelato necessario per poter programmare il PIC senza doverlo rimuovere dalla scheda, questa possibilità ci viene fornita dal “BootLoader”.

## Teoria sul controllo LAP:

**PWM**

Un segnale PWM (Pulse Width Modulation ovvero modulazione a variazione della larghezza d’impulso) è un’ onda quadra di dutycycle variabile che permette di controllare l’assorbimento (la potenza assorbita) di un carico elettrico(nel nostro caso il motore DC), variando (modulando) il dutycycle.

{% include figure image_path="/assets/images/posts/line-follower/15 duty.jpg" alt="Duty Cycle" caption="Duty Cycle" %}

Un segnale PWM è caratterizzato dalla frequenza (fissa) e dal dutycycle (variabile); il dutycycle è il rapporto tra il tempo in cui l’onda assume valore alto e il periodo T (l’inverso della frequenza: T=1/f) ne segue che un dutycycle del 50% corrisponde ad un’onda quadra che assume valore alto per il 50% del tempo, un dutycycle dell’80% corrisponde ad un’onda quadra che assume valore alto per l’80% del tempo e basso per il restante 20%, un dutycycle del 100% corrisponde ad un segnale sempre alto e un dutycycle dello 0% ad un segnale sempre basso (come vedremo anche questi ultimi due casi non sono del tutto inutili). Ora è necessario capire come applicare il segnale PWM al ponte H per controllare il motore, esamineremo la modalità: PWM locked anti-phase.

## Locked Anti-Phase PWM

Il controllo LAP (locked anti-phase) si basa su questo schema circuitale:

{% include figure image_path="/assets/images/posts/line-follower/16 l298.jpg" alt="L298" caption="L298" %}

Il segnale PWM viene messo in ingresso all’invertitore in modo da avere ai due lati opposti del ponte due segnali invertiti tra loro; agendo sull’enable è possibile spegnere il rispettivo ponte.

Per il controllo LAP può bastare anche solo un segnale di comando (l’enable può essere fissato alto se non necessario) infatti l’onda quadra (PWM) stabilisce sia la velocità che il verso di rotazione nel seguente modo:

* Dutycycle a 0% : rotazione alla massima velocità in un verso
* Dutycycle al 50%: motore fermo
* Dutycycle al 100%: rotazione alla massima velocità nell’altro verso

# Teoria sul Bootloader

Il bootloader è un software sviluppato dalla microchip. La stessa casa che produce i PIC, per permettere la programmazione del microcontrollore senza rimuoverlo dal circuito ed inserirlo nel programmatore.

In pratica il bootloader è un software che va caricato nel PIC tramite programmatore solo una volta  e che poi permette la riprogrammazione dell’integrato tramite porta seriale.

Il software necessario è scaricabile direttamente dal sito microchip a questo indirizzo:
http://www.microchipc.com/PIC16bootload/PIC16F87xA_bootloader_v9-50.zip

è composto da 2 parti, una da caricare nel PIC e l’altra invece è l’applicativo da utilizzare sul pc per spedire al PIC il file .hex generato per il nostro software.

Il PIC integra già al suo interno tutto il necessario per la comunicazione RS232 tranne il convertitore di stati logici che trasformi i livelli di tensione TTL del PIC (0v , 5v) a quelli dello standard RS232 (-12v , +12v).

L’integrato scelto per questa funzione è il MAX 232 che è in grado partendo da una Vcc di 5v di fornirci in uscita i richiesti +12v e -12v.
Ciò è possibile grazie al un circuito a pompa di carica

{% include figure image_path="/assets/images/posts/line-follower/17 pompac.jpg" alt="Pompa condensatori" caption="Pompa condensatori" %}

Le figure A e B mostrano come viene ottenuto il raddoppio della tensione. Una immagine che rende l’idea è quella di un contenitore (C2) che preleva acqua da una fonte e la riversa in un secondo contenitore (C1) posto a maggiore altezza. Più in dettaglio:

* Inizialmente il condensatore C2 viene connesso tra massa e Vcc; quindi la corrente (in blu) carica C2 alla tensione di alimentazione (in giallo). Quindi Vc2 = Vcc
* C2 viene successivamente connesso tra Vcc ed un secondo condensatore C1; la tensione ai capi di C1 deve essere uguale alla somma di Vcc e Vc2 e quindi C2 si scarica verso C1, che aumenta la propria tensione rispetto a massa
* Il processo è ripetuto fino a quando la tensione ai capi di C1 è uguale a 2Vcc: in questo caso infatti C2 non si può più scaricare.

Da notare che, nel funzionamento normale, il processo non può mai interrompersi in quanto il carico collegato a C1, non disegnato, assorbe corrente e quindi tende a scaricare C2 stesso.

Analogamente le figure C e D mostrano l’inversione di tensione:

* Inizialmente C2 è caricato alla tensione di alimentazione (magari, come nel disegno da 2Vcc, ricavata con il precedente circuito)
* Quindi C2 è connesso tra massa e C1 avendo cura di invertire le polarità. In questo modo C1 si carica a -2Vcc

Il limite dei circuiti a pompa di carica è la limitata quantità di corrente disponibile: infatti se prelevo corrente da C1 questo tende a scaricarsi, facendo scendere la tensione; la corrente generata da un circuito integrato tipo Max232 è generalmente tutta utilizzata per il solo funzionamento del driver e quindi non è disponibile per altri circuiti

Ecco lo schema circuitale che mostra come collegare il MAX232 per farlo funzionare come convertitore di stati logici per il PIC.

{% include figure image_path="/assets/images/posts/line-follower/18 max232.jpg" alt="MAX232" caption="MAX232" %}

Su Rx e Tx verranno collegati i piedini del PIC dedicati alla comunicazione seriale.

# Schema circuitale scheda a microcontrollore

Per far svolgere alla scheda tutte le funzioni evidenziate dallo schema a blocchi è stato sviluppato questo circuito: (In allegato schematico, master e layout).

{% include figure image_path="/assets/images/posts/line-follower/19 main.jpg" alt="Scheda principale" caption="Scheda principale" %}

Il PIC 16F876 è il centro della scheda, C3 è un condensatore di filtraggio per l’alimentazione da 100nF, R2 è una resistenza da 10K che insieme ai 2 pin “Reset” crea il circuito necessario a resettare il PIC.

C1,C2,Q1 formano il circuito di clock, C1 e C2 sono due condensatori ceramici da 27pF e Q1 e un quarzo da 4 MHz.

Il connettore “PWR” è quello che porterà l’alimentazione, 5v stabilizzati, a tutta la scheda. LED-PWR è il led che mostra la presenza dell’alimentazione e R1 è la sua resistenza di limitazione da 1K ohm.

Il connettore “SENS” sarà collegato al connettore “SEGNALI” della scheda dei sensori e si occuperà di portare al PIC i segnali provenienti dai sensori.

Il connettore “LED” ci fornirà la possibilità di inserire dei led di controllo del robot, comandati dalla Porta B del PIC. I led al massimo potranno essere 7 io ne ho utilizzati solo tre per segnalare alcuni stati del robot. Per comodità è stato inserito il connettore “GND” che in pratica non fa altro che fornirci dei pin di massa dove poter collegare il catodo dei led.

Il 74HC14 è il buffer invertente utilizzato per il controllo LAP dei 2 motori, il connettore “MOTORI” porterà i segnali generati dal PIC e dall’inverter alla scheda di potenza.

C4 è un condensatore da 100nF che filtrerà l’alimentazione del 74HC14.

“SV1” sono 2 pin ai quali verrà collegato un interruttore che avvierà il robot, R3 è la resistenza di pull-up da 10K per mantenere a Vcc il segnale quando l’interruttore è aperto.

C5,C6,C7,C8 sono i 4 condensatori necessari per il funzionamento del max232, sono 4 condensatori da 10uF da almeno 16v.
X1-2, X1-3, X1-5 sono i 3 pin del connettore seriale utilizzati per comunicare con il pc.

{% include figure image_path="/assets/images/posts/line-follower/20 PIC.jpg" alt="PIC" caption="PIC" %}

Ecco la scheda assemblata, manca solo da inserire gli integrati negli appositi zoccolini.

## Studio e sviluppo del software per il controllo del robot

Per realizzare il software del robot è indispensabile avere ben chiare in mente tutte le funzioni e tutti i vari controlli che il software dovrà effettuare.

Per chiarirsi le idee di solito è molto utile stendere un diagramma di flusso che ci servirà poi per scrivere il software vero e proprio.

Ecco il diagramma su cui mi sono basato per realizzare il software che controlla il robot:

{% include figure image_path="/assets/images/posts/line-follower/21 diagramma3.jpg" alt="Diagramma" caption="Diagramma" %}

Dal diagramma, studiando tutte le varie parti ho realizzato il software. Il software è stato scritto in linguaggio C e compilato con il compilatore C14. (In allegato il software)

Qui riporto solo alcune parti fondamentali del software per poterle spiegare.

### Configurazione dei moduli per il PWM:

Il PIC 16F876 è gia predisposto per poter generare i segnali di controllo PWM.
Per far ciò è necessario però configurare alcuni registri interni del PIC per attivare questa funzione, per deciderne la frequenza, ecc.

Ecco le istruzioni che ci consentono di fare ciò:

```c
void PWMSetup(void)
{
CCP1CON= 0;  //Resetto il modulo CCP1
CCP2CON= 0;   //Resetto il modulo CCP2
PR2= 0xFF;    //Inserire qui il valore di PR2 desiderato

PWMDutySX(512);   //DC 50% con LAP
PWMDutyDX(512);   //DC 50% con LAP
T2CON= 0b00000100;  //Senza prescaler e post scaler e attivo Timer2

ccp1m3= 1;    //Configuro CCP1 per la modalità PWM
ccp1m2= 1;
ccp1m1= 0;
ccp1m0= 0;
ccp2m3= 1;    //Configuro CCP2 per la modalità PWM
ccp2m2= 1;
ccp2m1= 0;
ccp2m0= 0;
}
```

Questa parte di codice permette di configurare e abilitare i registri necessari per il PWM

Il PIC 16F876 ci permette di avere un valore per il dutycycle formato da 10bit (1024 combinazioni) cosi da aver una buona sensibilità per il controllo della velocità.

Per sistemare il valore dei 10bit da suddividere in 2 registri sono necessarie queste poche istruzioni:

```c
void PWMDutySX (unsigned int duty1)
{
ccp1y=0b00000001&duty1;
ccp1x=0b00000001&(duty1>>1);
CCPR1L= duty1>>2;
}

void PWMDutyDX (unsigned int duty2)
{
ccp2y=0b00000001&duty2;
ccp2x=0b00000001&(duty2>>1);
CCPR2L= duty2>>2;
}
```

### Configurazione del convertitore A/D:

I sensori utilizzati forniscono tutti un uscita analogica, una tensione che varia. Per poter leggere questa variazione è necessario abilitare il convertitore A/D integrato nel PIC.

Il convertitore dovrà campionare i segnali ogni volta che il software richiede la lettura di un sensore, per evitare di ripetere all’interno del programma più volte lo stesso codice ho utilizzato delle procedure.

Ecco la procedura necessaria ad avviare la campionatura di un segnale collegato su RA2:

```c
int read_dx()   //Procedura di campionatura segnali su AN2
{
int d;
ADCON1= 0b10000000;  //Setto il registro ADCON1 varie funzioni,
//leggere DATASHEET
ADCON0= 0b10010001;  //Setto l’AD per leggere su AN2 e l’abilito
delay_ms(1);
go= 1;     //Avvio la campionatura
delay_ms(10);
d= ADRESH;    //Assegno a d i 2 bit di ADRESH
return ((d << 8)| ADRESL);  //Shifto di 8 i bit di d e poi gli assegno gli 8 bit
//di ADRESL per avere i 10bit totali
}
```

ADCON0 e ADCON1 sono 2 registri fondamentali per l’A/D il primo serve ad abilitare il convertitore, a deciderne il clock, e a decidere quale delle 5 porte campionare.

Il secondo invece permette di configurare i 6 pin della PORTA come ingressi digitali o analogici.

Il convertitore analogico digitale del PIC è a 10bit, in pratica la tensione in ingresso massima fornirà un valore di 1024, ad ingresso 0 fornirà 0

## Teoria sui convertitore A/D

Analog to Digital Converter (ADC), in italiano convertitore analogico-digitale, è un componente elettronico in grado di convertire una grandezza continua (ad es. una tensione) in una serie di valori discreti.

La risoluzione di un convertitore indica il numero di valori discreti che può produrre. È usualmente espressa in bit. Per esempio, un ADC che codifica un ingresso analogico in 256 livelli discreti ha una risoluzione di 8 bit, essendo 28 = 256. La risoluzione può anche essere definita elettricamente, ed espressa in volt. La risoluzione in volt di un ADC è uguale alla minima differenza di potenziale tra due segnali che vengono codificati con due livelli distinti adiacenti. Alcuni esempi possono aiutare:

Esempio 1:

* Range compreso tra 0 e 10 volt
* Risoluzione dell’ADC di 12 bit: 212 = 4096 livelli di quantizzazione
* La differenza di potenziale tra due livelli adiacenti è 10 V / 4096 = 0.00244              V = 2.44 mV

Esempio 2:

* Range compreso tra -10 e 10 volt
* Risoluzione dell’ADC di 14 bit: 214 = 16384 livelli di quantizzazione
* La differenza di potenziale tra due livelli adiacenti è 20 V / 16384 = 0.00122            V = 1.22 mV

Nella pratica, la risoluzione di un convertitore è limitata dal rapporto segnale/rumore (S/N ratio) del segnale in questione. Se è presente troppo rumore all’ingresso analogico, sarà impossibile convertire con accuratezza oltre un certo numero di bit di risoluzione. Anche se l’ADC produrrà un valore, questo non sarà accurato essendo i bit meno significativi funzione del rumore e non del segnale.

## Modifica direzione del robot:

Per modificare la direzione del robot è necessario far variare la velocità quindi il dutycycle che controlla un motore.
Più è la differenza di velocità tra i due motori più è rapida la curva.

Per modificare la velocità dei motori all’interno del software sono state create delle procedure, ne riporto una per poterla spiegare.

```c
void gira_dx()
{
PWMDutyDX(870);  //Motore Sx più veloce del motore Dx
PWMDutySX(930);
ledSX= 0;   //Accendo ledDX
ledDX= 1;
ledC= 0;
}
```

In questo caso assegnando al motore Dx un dutycycle minore rispetto al motore Sx otterrò una leggera curva a destra, per segnalare che il robot sta curvando accendo il led corrispondente alla direzione delle curva.

Per poter far percorrere al robot curve più nette è stato necessario inserire un’altra procedura chiamata curva veloce a destra che in pratica non fa altro che aumentare la differenza tra i due dutycycle.

Per segnalare questa situazione accendo anche il led centrale oltre a quello della direzione di curvatura.

# Costruzione telaio e assemblaggio

Nel costruire la struttura del robot è necessario tener conto della distribuzione dei pesi, il peso maggiore dev’essere sulle ruote anteriori quelle collegate ai motori cosi da aver un buon attrito e una precisa variazione di direzione.
Inoltre è necessario disporre le batterie in una posizione facilmente accessibile cosi da facilitarne il cambio e la rimozione.
Sul telaio del robot devono essere disposti 2 pulsanti, uno utilizzato per avviare il robot e uno collegato al reset (necessario per il bootloader).
Dovranno essere poi disposti in maniera visibile i 3 led di segnalazione.
Nella realizzazione delle schede è necessario disporre dello spazio per ricavare i 4 fori di fissaggio delle stesse al telaio.
La scheda di potenza è bene che sia in alto cosi che il dissipatore del L298 abbia il necessario ricambio d’aria.

Ecco come sono riuscito a conciliare tutte queste caratteristiche:

{% include figure image_path="/assets/images/posts/line-follower/22 robot1.jpg" alt="Robot 1" caption="Robot 1" %}

Questa foto mostra il robot completo visto da dietro, si vede la batteria da 9v il Tamiya le Ball Caster. La scheda del micontrollore quella con in connettore per la seriale, ed in alto la scheda di potenza con il dissipatore e L298

{% include figure image_path="/assets/images/posts/line-follower/23 robot2.jpg" alt="Robot 2" caption="Robot 2" %}

Qui invece si vedono le Ruote, i tre led di segnalazione (ledDX, ledSX, ledC) il sensore di prossimità della SHARP ed il pacco batterie da 4,5v.

# Conclusioni e osservazioni

Costruire il robot è stato tanto difficile quanto interessante, mi ha permesso di scontrarmi con argomenti non conosciuti e di dover cercare informazioni per una sorta di autoapprendimento.

Inoltre la progettazione e la ricerca guasti mi ha fornito un metodo di approccio ai problemi modulare e funzionale.

Il risultato è ottimo, il robot segue con una discreta precisione la linea tracciata sul fondo e rileva gli ostacoli senza difficoltà
Purtroppo il raggio di curvatura del robot non è molto ampio ciò è dovuto soprattutto alla scarsa precisione e linearità dei motori utilizzati.

Il software scritto è stabile e non presenta bug.

L’elettronica è stata testata e non ha rivelato problemi di sorta anche dopo ore di utilizzo.