---
title: "Costruiamo un bromografo"
excerpt: "Costruiamo un bromografo"
permalink: /tutorial/costruiamo-un-bromografo
author: "Raffaello Bonghi"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/tutorial/bromografo/Foto053.jpg
  teaser: /assets/images/tutorial/bromografo/Foto053.jpg
componenti:
  - image_path: /assets/images/tutorial/bromografo/Foto003.jpg
  - image_path: /assets/images/tutorial/bromografo/Foto004.jpg
  - image_path: /assets/images/tutorial/bromografo/Foto005.jpg
  - image_path: /assets/images/tutorial/bromografo/Foto006.jpg
costruzione:
  - image_path: /assets/images/tutorial/bromografo/Foto007.jpg
  - image_path: /assets/images/tutorial/bromografo/Foto008.jpg
---

Dopo lunghi studi persi durante i primi di agosto dell’anno scorso, tra vacanze e negozi chiusi, iniziai a realizzare un bromografo utile per creare le schede del mio robot  e tutte le schede elettroniche che potessero servirmi.

Durante i miei studi in materia cercai di capire anche cosa significava usare un bromografo e come dovessi usare le lampade infatti le lampade UVA possono essere pericolose:

Su http://www.roboteck.org/faq/faq.htm#D_8_5 La faq della lista roboteck vi sono contenute le informazioni sulle lampade. Cito quello che viene spiegato che a parer mio è molto utile:

Ed il bromografo che cosa è, dove lo posso trovare e, soprattutto, quanto costa? E poi, sarò capace di usarlo?

> [R8.5] Il bromografo è un attrezzo che permette di arrivare ad avere dei PCB di qualità anche a livello amatoriale (si riescono ad avere, con l’esperienza, anche piste di 5 mil).
> Come già scritto precedentemente, con la bromografia si fanno delle “foto a contatto” su di una basetta ramata presensibilizzata. Per fare ciò si possono utilizzare diverse sorgenti luminose.
>
> Qui di seguito riporto un elenco di sorgenti luminose, peraltro non esaustivo, che è risultato essere stato usato dai componenti della mailing-list:
>
> * Lampade alogene da tavolo
> * Lampade UV-A/B/C da 4W/8W/12W/15W
> * Lampade abbronzanti da tavolo
> * Lampade a vapori di mercurio
> * Lampade per le zanzariere
> * Lampade comuni ma di varie potenze
> * Sole
> 
> Uno studio approfondito (Eseguitodaunodeinostricompari:-) ha fatto rilevare che il Photoresist e’ sensibile alle radiazioni ultraviolette (UV) comprese tra i 300nm (nanometri) e i 440nm.
> 
> Pare anche evidente che tutti sono soddisfatti del proprio metodo e non hanno grandi intenzioni di cambiare, quindi si può supporre che qualunque sia il tempo di esposizione necessario, qualunque sia la spesa sopportata, qualunque sia il grado tecnico raggiunto, a tutti fa fatica farsi un altro bromografo.:-)))
> 
> Anche fisicamente i procedimenti utilizzati per impressionare la basetta sono vari (si arriva al folkloristico, ma pur sempre efficace, portafoto esposto al sole).
> 
> Generalmente un bromografo dovrebbe avere una o piu lampade UV, illuminanti uno o tutti e due i lati (se si ha intenzione di fare dei PCB doppia faccia), e quindi si suppone debba essere incluso in una scatola-recipiente chiudibile (per evitare di trovarsi involontariamente tintarellati). All’interno della scatola si dovrebbero trovare (il condizionale è d’obbligo) le lampade UV con gli starter (questi ultimi con la sigla S2, se si usano due neon in serie) e i/il reattore, un piano di vetro od altro materiale trasparente (che NON filtri gli UV!) sul quale appoggiare l’elemento mascherante e la basetta col lato sensibile verso le lampade:-). Inoltre, si può aggiungere (e, nonostante il tono scherzoso, il seguente materiale può essere un valido aiuto per una migliore qualità del risultato) a scelta: un timer, una pompa a vuoto, un altro vetro, del polistirolo, dei pesi o quant’altro possa venire in mente per pressare la basetta e renderla tutt’uno con la pellicola trasparente.
> In questo caso il timer NON serve per pressare la basetta ma per avere dei tempi esatti di esposizione (che possono variare per molti motivi ed a volte 10-20 secondi in piu o in meno fanno la differenza). Per poter fare dei test su quali siano i tempi di esposizione adatti è consigliabile scaricare e stampare il foglio test dal tutorial di Vincenzo Villa sui PCB (che tra l’altro è moooolto piu esaustivo di queste FAQ).
> L’indirizzo è: http://www.vincenzov.net/tutorial/stampati/stampati.htm
> La pompa a vuoto serve per far aderire perfettamente la basetta con il master ed il vetro evitando che rimangano delle bolle di aria tra di esse, che non permetterebbero la corretta impressione dell’immagine sulla basetta.
> Probabilmente nei bromografi professionali di ultima generazione vengono usati i policarbonati al posto del vetro, come per i fanali delle autovetture e delle moto moderne, che sono molto piu’ trasparenti del vetro ed ormai hanno simili caratteristiche meccaniche.
> 
> Dato che l’elemento mascherante è la stampa del circuito stampato (possibilmente su acetato), i raggi UV impressionano lo strato sensibile che rimane esposto alla luce.

Da qui elaborai uno schema che riprendeva lo schema principale di Fiser apportando qualche piccola modifica sulla quantità dei reattori presenti:

{% include figure image_path="/assets/images/tutorial/bromografo/Foto001.jpg" alt="Schema elettrico" caption="Schema elettrico" %}

Da questo iniziai a pensare quali erano gli elementi fondamentali per realizzare il mio nuovo bromografo.

Si capiva subito che la spesa più importante erano le lampade e da ciò ne conseguiva rapidamente che servivano:

* UV tipo A 352nm da 8 Watt, di queste 4
* 4 Reattori da 8W
* 4 Starter
* 8 supporti per i neon

Questi erano gli elementi fondamentali per poter realizzare la prima parte del bromografo.

Già iniziai a pensare una struttura basilare del macchinario questo era composto da due parti:

* Camera di Impressione
* Zona di controllo

Nella camera di impressione vi erano contenute le lampade la zona che pensavo utilizzare per questa sezione era circa **20×30 cm**.

La zona di controllo doveva contenere tutta l’elelettronica di gestione delle lampade più i reattori e gli starter.

Da questo momento in poi iniziai a pensare che materiali utilizzare per realizzare la scatola del bromografo, la scelta cadde rapidamente sul legno.

Realizzare la struttura del bromografo comportò un po’ di tempo, ma la struttura divenne chiara dopo una rapida discussione con il falegname.

# Elementi

{% include figure image_path="/assets/images/tutorial/bromografo/Foto002.jpg" alt="Telaio" caption="Telaio" %}

* 2 pannelli legno multistrato spesso 1,5cm, da 11,5cm x 38cm PER LATERALI
* 2 pannelli legno multistrato spesso 1,5cm, da 11,5cm x 33cm PER LATERALI
* 1 pannello legno multistrato spesso 1,5cm, da 10cm x 33cm PER LATERALE BASSO
* 1 pannello legno multistrato spesso 1cm, da 33cm x 38cm PER BASE
* 1 pannello legno multistrato spesso 1,5cm, da 23cm x 33cm PER COPERCHIO LAMPADE
* 1 pannello legno multistrato spesso 1,5cm, da 15cm x 30cm PER COPERCHIO ELETTRONICA
* 2 Listelli per vetro da 30cm
* 2 Listelli per vetro da 17,5cm
* 1 Listello per coperchio elettronica da 5cm

Misura della struttura complessiva: 14,5cm altezza X 38cm lunghezza x 33cm Profondità. Da questo momento in poi iniziai a prendere tutto ciò che serviva per completare la prima parte del bromografo:

* 1 interruttore con LED
* 1 spina
* 1 rivelatore
* 1 Percloruro Ferrico, Trovato in cantina
* 1 basetta presensibilizzata
* 1 lastra di vetro 5mm
* 1 Piedini per la base del bromografo,
* 1 Maniglia per aprire lo sportello
* 20 viti da 2cm per legno
* Gli elementi fondamentali per costruire il bromografo erano presenti. Adesso si poteva iniziare a realizzare la struttura fondamentale.

{% include gallery id="componenti" caption="Componenti" layout="half" %}

# Costruzione

Durante il montaggio scoprì di aver ragionato male sulle dimensioni della sezione dedicata all’impressione della scheda, mi ero infatti dimenticato di calcolare oltre la presenza delle lampade anche la presenza dei porta lampade che occupavano 1 cm in più del previsto. Questo nuovo problema portò a pensare come dovessi risolvere questo errore senza dover rifare il telaio del bromografo dal falegname.

L’idea si risolse facendo un piccolo scasso all’interno del legno permettendo di recuperare quel centimetro perso.

{% include gallery id="costruzione" caption="Costruzione" %}

Con questo si chiude la prima parte della guida su come realizzare un bromografo utile per realizzare schede elettroniche, sia per il minisumo che per l’elettronica amatoriale.
Nella prossima guida sarà dedicata al montaggio della struttura ed alla prima prova di stampa.

Ecco il costo della prima spesa per realizzare il bromografo

| Qt | Componenti | costo |
|----|------------|-------|
| 4 | lampade NEON UVA 352 nm 8W, 4€ cada 1 | TOT 16€ |
| 4 | reattori 8W, 5,50€ cada 1 | TOT 22€ |
| 8 | Porta lampade NEON, 1€ cada 1 | TOT 8€ |
| 4 | Starter, 50cent cada 1 | TOT 2€ |
| 4 | porta Starter | 1€ cada 1 (me li hanno regalati) |
| 1 | Interruttore con luce | 3€ |
| 1 | Spinotto | 1,8€ |
| 1 | rivelatore | 2€ |
| 1 | Percloruro Ferrico | Trovato in cantina |
| 1 | basetta presensibilizzata | 5,50€ |
| 1 | Scatola del Bromo | 11€ già tagliata |
| 3 | cinghie per aprire lo sportello riflettente | 1,50€ |
| 1 | lamina in alluminio riflettente per i neon | 3€ |
| 1 | set di punte per CS (servono per fare i buchi di piccola misura per far passare i reofori nel PCB) del Dremel | 6,80€ |
| 1 | Piedini per la base del bromografo | 2€ |
| 1 | Maniglia per aprire lo sportello | 3€ |
| 20 | viti da 2cm per legno | 1,50€ |

Per il momento Spesa complessiva è di 89,10€