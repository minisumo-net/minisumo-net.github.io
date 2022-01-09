---
title: "Regolamento"
excerpt: "Regolamento"
permalink: /regolamento/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/regolamento/posizioni.jpg
  teaser: /assets/images/regolamento/posizioni.jpg
  actions:
    - label: ":sparkling_heart: Sponsor"
      url: "https://github.com/sponsors/rbonghi"
toc: true
toc_label: "Tavola dei contenuti"
toc_sticky: true
configurazioni:
  - url: /assets/images/regolamento/sumo-fold_up.gif
    image_path: /assets/images/regolamento/sumo-fold_up.gif
    alt: "minisumo alla partenza"
    title: "minisumo alla partenza"
  - url: /assets/images/regolamento/sumo-fold_down.gif
    image_path: /assets/images/regolamento/sumo-fold_down.gif
    alt: "minisumo trasformato"
    title: "minisumo trasformato"
posizioni-robot:
  - url: /assets/images/regolamento/ro01.gif
    image_path: /assets/images/regolamento/ro01.gif
    alt: "posizione 1"
    title: "Il robot è al Limite del bordo campo, ma non è ancora caduto. Il robot può continuare a gareggiare"
  - url: /assets/images/regolamento/ro02.gif
    image_path: /assets/images/regolamento/ro02.gif
    alt: "Posizione 2"
    title: "Il robot si è piegato su di un lato sul ring. Il robot è ancora in gara."
  - url: /assets/images/regolamento/ro03.gif
    image_path: /assets/images/regolamento/ro03.gif
    alt: "Posizione 3"
    title: "Il robot è capovolto sul ring. Il robot è ancora in gara."
  - url: /assets/images/regolamento/ro05.gif
    image_path: /assets/images/regolamento/ro05.gif
    alt: "Posizione 4"
    title: "Il robot ha toccato con una delle sue estremità il terreno. Il robot ha perso l’incontro."
---

Molto spesso quando andiamo a costruire il nostro robot da minisumo non sappiamo come dobbiamo costruirlo per colpa delle severe norme imposte dal regolamento. Ma in questa guida vedremo come poter interpretare al meglio il significato di certi punti che potrebbero risultare difficili per chi sta iniziando la prima volta.

La prima operazione che dobbiamo fare, quando iniziamo a progettare il robot, è vedere se il robot rispetta i parametri imposti dal regolamento, partendo dal peso, le misure ecc…  (Regolamento visionabile nell’area download)

Queste informazioni sono descritte nel capitolo 3, articolo 5 del regolamento:

**Capitolo 3: Specifiche dei robot (Articolo 5 Specifiche)**

Il robot deve poter essere contenuto in un quadrato di 10x10cm per lato. Non ci
sono restrizioni in altezza.

* Il peso non deve essere superiore a 500gr.
* Non ci sono restrizioni sul metodo di controllo usato con robot autonomi.
* Un robot autonomo deve essere progettato per attivarsi dopo circa 5 secondi che il contendente ha premuto il pulsante di start del robot.

Da qui si può capire che il robot deve rispettare i 500g di peso e la base di 10x10cm.

Da ciò si deduce che le batterie al piombo o motori particolarmente pesanti possono creare qualche problema al nostro progetto, quindi se progettiamo il nostro primo minisumo tralasciamo questo tipo di materiali.

L’alimentazione del nostro robot che ci conviene utilizzare sono senza dubbio le batterie AA, le AAA o meglio ancora le batterie al Litio che ci comportano un notevole risparmio di peso.

I motori che potremo usare durante le nostre creazioni potranno essere servocomandi o motori con motoriduzione, ad esempio Gear Motor, che rispettano le specifiche della categoria e sono adatti per un progetto di un robot da minisumo.
Altro punto fondamentale di un nostro progetto è senza dubbio la struttura che il robot da minisumo avrà, che come da regolamento dovrà rispettare i 10cm per lato.
Queste rigorose misure comportano delle dimensioni che non saranno possibili superare per il robot, come le dimensioni massime delle ruote che non dovranno superare i 10cm di diametro.

Una curiosità che ci può ritornare molto utile, le dimensioni massime 10cm x 10cm valgono soltanto durante l’avvio del mach, durante la gara il robot può mutare la propria forma permettendosi di diventare più grande o più piccolo, come possiamo vedere nella foto di questo robot da minisumo dell’est Europa.
I robot con questo tipo di struttura, non sono molto frequenti durante le robofesta italiane e può essere un buon punto di partenza per futuri robot da competizione.

{% include gallery id="configurazioni" caption="minisumo configurazoni" layout="half" %}

# 5 Secondi e Restrizioni

Altro punto importante evidenziato sempre nell’articolo 5 riguarda il ritardo di 5 secondi.

Questo ritardo risulta molto importante perché permette di allontanare i costruttori del robot e tutti i partecipanti dal ring ad una distanza di 100 cm evitando di compromettere il corretto funzionamento dei robot durante lo scontro.
Le specifiche del robot però come abbiamo notato nel regolamento, contenuto nell’area download del portale, non sono finite qui, infatti, proseguendo nella lettura possiamo notare altre restrizioni relative agli “armamenti” del minisumo. 

Ma analizziamo l’articolo 6:

**Articolo 6 Restrizioni sul progetto del robot**

* Il robot non deve includere un dispositivo che impedisce le operazioni dell’avversario, come un disturbatore (jammer) o una luce stroboscopica.
* Il robot non deve includere qualsiasi parte che potrebbe danneggiare la superficie del Ring.
* Il robot non deve includere un dispositivo che spruzza liquidi, polvere o gas.
* Il robot non deve includere dispositivi sparanti.
* Il robot non deve includere dispositivi di espulsione.
* Il robot non deve includere nessuna parte che fissa il robot alla superficie del Ring e impedisce di essere mosso (ad esempio ventose, colla e così via).

Queste restrizioni sono molto chiare e non c’è bisogno di aggiungere spiegazioni in più, infatti, il robot non potrà supportare dispositivi che possano disturbare l’avversario, dispositivi che possano danneggiarlo, o distruggano il ring e ancora peggio gli spettatori presenti alla competizione.

Altre informazioni che possono risultare utili durante la costruzione del robot, riguardano la “sensoristica” per la rilevazione dell’avversario e del bordo ring.
Per riconoscere il bordo ring si possono usare i sensori infrarossi, che riconoscono a seconda della quantità di luce riflessa se il colore di fondo è bianco o nero, ma per questo vi rimando all’articolo di Antonio sul funzionamento e sulla costruzione di un sensore infrarosso.

Altra alternativa che può essere utilizzata è quella di un microswitch che, quando il robot da mini-sumo giunge alla fine del ring, questo riconoscendo lo scalino che divide il ring dal terreno può decodificare la fine del campo.

# Organizzazione di una competizione

Molto spesso ci troviamo a partecipare ad un evento e questo può essere strutturato in modo differente a seconda del giudice o della quantità di robot presenti.

Questo molto spesso è dovuto all’organizzazione dei giudici dei robot che secondo la quantità di robot presenti in gara optano per due possibili strutture, la prima ad eliminazione diretta degli avversari, la seconda a gironi. Queste come è possibile notare dai seguenti schemi differiscono per più di un motivo, per i seguenti motivi:

{% include figure image_path="/assets/images/regolamento/eliminazioneD.jpg" alt="Eliminazioni dirette" caption="Eliminazioni dirette" %}

Nelle eliminazioni dirette ogni robot si scontrerà con un solo avversario comportando l’eliminazione istantanea dalla gara. I vantaggi che comportano questo tipo di gara, sono principalmente di tempo, infatti, in un evento organizzato in questo modo si ha molto più tempo per poter fare gareggiare tutti i robot iscritti.

{% include figure image_path="/assets/images/regolamento/eliminazioneG.jpg" alt="Gironi" caption="Gironi" %}

Nella seconda possibilità di strutturare un evento, si utilizzano i gironi. In questo caso i robot si sfideranno ognuno contro tutti gli altri sfidanti. Chi otterrà più vittorie passerà il turno o vincerà l’evento. Strutture del genere portano via molto tempo per poter far gareggiare tutti i robot.

# La manche

I robot dovranno sfidarsi in un ring rotondo, prima dell’avvio della gara i robot si dovranno posizionare nel seguente modo:

Il primo robot dovrà collocarsi nel primo semicerchio che è segnato nella foto in rosso nella posizione che il partecipante ritiene più comoda, dopodiché farà la stessa cosa l’avversario posizionandosi nella sezione opposta blu. Il Mach successivo il robot che avrà collocato per secondo potrà collocarlo per primo.

{% include figure image_path="/assets/images/regolamento/posizioni.jpg" alt="Posizioni" caption="Posizioni" %}

L’incontro è costituito sempre da 3 manche, la prima, la seconda e la terza di spareggio.

Dalla quantità di vittorie concluse dal robot si dichiarerà il vincitore del mach.
Se i robot dovessero fermarsi o non si riuscisse ad avere una vittoria netta di un robot sull’altro nel corso dei 3 minuti. Il giudice deciderà quale robot far vincere o se fare un nuovo mach.

L’articolo 10 elenca tutte le possibilità in cui non ci sono disparità tra i robot:

**Articolo 10 Cancellazione della partita e ripetizione**
Un incontro verrà cancellato o rigiocato come conseguenza delle seguenti condizioni:

* I robot sono bloccati insieme in modo tale che nessun’altra azione è possibile, oppure ruotano in circolo svariate volte.
* Entrambi i robot toccano la zona esterna del Ring allo stesso tempo.
* Qualsiasi altra condizione per cui il giudice decide che non può essere designato un vincitore.
* In caso di una ripetizione, sono proibite manutenzioni ai robot fino a che non venga osserato un punto Yuko, ed i robot devono essere immediatamente rimessi nella posizione specificata nel Capitolo 8 Articolo 6.
* Se nessuno dei robot in competizione vince o perde anche dopo aver ripetuto l’incontro, il giudice può riposizionare entrambi i robot in una specifica locazione e ricominciare. Se dopo questo non c’è ancora un vincitore, l’incontro può continuare dalla posizione decisa dal giudice, fino a che non viene raggiunto un limite di tempo.

Nel capitolo 7 del regolamento sono presenti tutte le possibilità in cui il robot o la squadra commetta delle violazioni.

Le violazioni, infatti, comportano l’ammonimento della squadra e se la stessa ne ha commette troppi può essere anche espulsa dal gioco.

Durante l’incontro il robot può trovarsi in uno dei seguenti stati e molto spesso non si sa come ci si deve comportare. Vi elenco i casi estremi:

{% include gallery id="posizioni-robot" caption="posizioni robot" layout="half" %}