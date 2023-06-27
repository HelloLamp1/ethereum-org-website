---
title: Attacco e difesa del proof-of-stake di Ethereum
description: Scopri di più sui vettori di attacco noti sul proof-of-stake di Ethereum e come sono difesi.
lang: it
---

Ladri e sabotatori sono costantemente alla ricerca di opportunità per attaccare i software dei client di Ethereum. Questa pagina delinea i vettori di attacco noti sul livello di consenso di Ethereum, definendo come possono essere difesi. Le informazioni su questa pagina sono adattate da una [versione più lunga](https://mirror.xyz/jmcook.eth/YqHargbVWVNRQqQpVpzrqEQ8IqwNUJDIpwRP7SS5FXs).

## Prerequisiti {#prerequisites}

È necessario avere delle conoscenze di base del [proof-of-stake](/developers/docs/consensus-mechanisms/pos/). Inoltre, sarebbe utile avere una comprensione di base del [livello d'incentivazione](/developers/docs/consensus-mechanisms/pos/rewards-and-penalties) di Ethereum e dell'algoritmo di scelta della diramazione, [LMD-GHOST](/developers/docs/consensus-mechanisms/pos/gasper).

## Cosa vogliono gli utenti malevoli? {#what-do-attackers-want}

Spesso si crede erroneamente che un utente malevolo di successo possa generare altro ether, o drenarlo da conti arbitrari. Nessuna delle due cose è possibile, poiché tutte le transazioni sono eseguite da tutti i client di esecuzione sulla rete. Devono soddisfare delle condizioni di validità di base (es. le transazioni sono firmate dalla chiave privata del mittente, il mittente ha un saldo sufficiente, ecc.), altrimenti sono semplicemente annullate. Esistono tre classi di risultati che un utente malevolo potrebbe realisticamente ottenere: riorganizzazioni, doppia finalità o ritardo della finalità.

Una **"riorganizzazione"** è un rimescolamento dei blocchi in un nuovo ordine, magari con l'aggiunta o la sottrazione di blocchi nella catena canonica. Una riorganizzazione malevola potrebbe assicurare l'inclusione o esclusione di blocchi specifici, consentendo la doppia spesa o l'estrazione di valore da transazioni di front-running e back-running (MEV). Le riorganizzazioni, inoltre, potrebbero essere utilizzate per impedire l'inclusione di certe transazioni nella catena canonica: una forma di censura. La forma più estrema di riorganizzazione è detta "inversione di finalità", che rimuove o sostituisce dei blocchi precedentemente finalizzati. Questa è possibile soltanto se più di ⅓ dell'ether in staking totale è distrutto dall'utente malevolo; questa garanzia è nota come "finalità economica" – maggiori informazioni al riguardo sono riportate in seguito.

La **doppia finalità** è l'improbabile ma grave condizione in cui due diramazioni riescono a finalizzarsi simultaneamente, creando uno scisma permanente nella catena. Ciò è teoricamente possibile per un utente malevolo disposto a rischiare il 34% dell'ether in staking totale. La community sarebbe obbligata a coordinarsi all'esterno della catena e accordarsi su quale catena seguire, il che richiederebbe forza al livello sociale.

Un attacco di **ritardo di finalità** impedisce alla rete di raggiungere le condizioni necessarie per finalizzare le sezioni della catena. Senza finalità, è difficile fidarsi delle applicazioni finanziarie basate su Ethereum. L'obiettivo di un attacco di ritardo di finalità è, probabilmente, semplicemente quello di interrompere Ethereum piuttosto che di trarne direttamente profitto, a meno che l'utente malevolo non abbia qualche posizione breve strategica.

Un attacco al livello sociale potrebbe mirare a minare la fiducia pubblica in Ethereum, svalutare l'ether, ridurne l'adozione o indebolire la community di Ethereum per complicare la coordinazione fuori banda.

Avendo stabilito perché un avversario potrebbe attaccare Ethereum, le seguenti sezioni esaminano _come_ potrebbe farlo.

## Metodi di attacco {#methods-of-attack}

### Attacchi al livello 0 {#layer-0}

Prima di tutto, gli individui che non partecipano attivamente a Ethereum (eseguendo un software del client), possono attaccarlo prendendo di mira il livello sociale (Livello 0). Il Livello 0 è la base su cui è costruito Ethereum e, come tale, rappresenta una potenziale superficie per gli attacchi, con conseguenze che si propagano sul resto dello stack. Alcuni esempi potrebbero includere:

- Una campagna di disinformazione potrebbe erodere la fiducia della community nella tabella di marcia di Ethereum, nei team di sviluppatori, nelle app, ecc. Questo potrebbe quindi ridurre il numero di persone desiderose di partecipare alla protezione della rete, penalizzando sia la decentralizzazione che la sicurezza cripto-economica.
- Attacchi mirati e/o intimidazioni dirette alla community degli sviluppatori. Questo potrebbe indurre all'uscita volontaria degli sviluppatori e rallentare il progresso di Ethereum.

- Anche una regolamentazione troppo zelante potrebbe essere considerata un attacco al Livello 0, poiché potrebbe disincentivare rapidamente la partecipazione e l'adozione.
- L'infiltrazione di utenti esperti ma malevoli nella community di sviluppatori il cui obiettivo è rallentare il progresso con discussioni futili, ritardare le decisioni fondamentali, creare spam, ecc.
- Tangenti agli attori principali nell'ecosistema di Ethereum per influenzare il processo decisionale.

Ciò che rende particolarmente pericolosi questi attacchi è che in molti casi è necessario disporre di pochissimo capitale o conoscenze tecniche. Un attacco al Livello 0 potrebbe essere un moltiplicatore di un attacco cripto-economico. Ad esempio, se la censura o l'inversione della finalità fossero ottenute da uno stakeholder attivo di maggioranza, minare il livello sociale potrebbe complicare la coordinazione di una risposta fuori banda della community.

Difendersi dagli attacchi di Livello 0 probabilmente non è semplice, ma possono essere stabiliti dei principi fondamentali. Uno di questi è mantenere un rapporto complessivamente elevato tra segnale e rumore per le informazioni pubbliche su Ethereum, create e diffuse da membri onesti della community tramite blog, server Discord, specifiche annotate, libri, podcast e YouTube. Qui su ethereum.org cerchiamo di mantenere informazioni accurate e di tradurle in quante più lingue possibili. Inondare uno spazio di informazioni di alta qualità e meme è una difesa efficiente contro la disinformazione.

Un'altra fortificazione importante contro gli attacchi al livello sociale è una chiara dichiarazione di missione e un chiaro protocollo di governance. Ethereum si è posizionato come il campione di decentralizzazione e sicurezza tra i livelli 1 dei contratti intelligenti, dando anche un elevato valore a scalabilità e sostenibilità. A prescindere dall'insorgere di divergenze nella community di Ethereum, questi principi essenziali sono minimamente compromessi. Valutare una narrativa basata su tali principi essenziali ed esaminarli tramite tranche successive di revisioni nel processo di EIP (proposta di miglioramento di Ethereum) potrebbe aiutare la community a distinguere gli utenti buoni da quelli "cattivi" e a limitare l'ambito di influenza degli utenti malevoli nella direzione futura di Ethereum.

Infine, è fondamentale che la community di Ethereum resti aperta e accogliente per tutti i partecipanti. Una community con guardiani ed esclusività è una community specialmente vulnerabile agli attacchi sociali, poiché è facile costruire narrative "noi e loro". Il tribalismo e il massimalismo tossico feriscono la community ed erodono la sicurezza del Livello 0. Gli utenti di Ethereum con un interesse acquisito nella sicurezza della rete dovrebbero vedere la propria condotta online e nel mondo reale come un contributo diretto alla sicurezza del Livello 0 di Ethereum.

### Attaccare il protocollo {#attacking-the-protocol}

Chiunque può eseguire un software del client di Ethereum. Per aggiungere un validatore a un client, un utente deve mettere 32 ether in staking nel contratto di deposito. Un validatore consente a un utente di partecipare attivamente alla sicurezza della rete di Ethereum proponendo e attestando nuovi blocchi. Il validatore ora ha una voce che può usare per influenzare i contenuti futuri della blockchain; può farlo onestamente, accrescendo i propri ether tramite le ricompense, o può provare a manipolare il processo a proprio vantaggio, rischiando il proprio stake. Un metodo per generare un attacco è accumulare una quota maggiore dello stake totale e utilizzarla per superare i voti dei validatori onesti. Maggiore è la quota dello stake controllata dall'utente malevolo, maggiore è il suo potere di voto, specialmente in determinati traguardi economici che esploreremo in seguito. Tuttavia, gran parte degli utenti malevoli non riuscirà ad accumulare abbastanza ether per attaccare in questo modo, quindi dovrà invece utilizzare delle tecniche per manipolare la maggioranza onesta perché agisca in un certo modo.

Fondamentalmente, tutti gli attacchi con pochi ether in staking sono lievi variazioni di due tipi di comportamenti scorretti dei validatori: ipoattività (mancata attivazione/proposta o farlo in ritardo) o iperattività (proporre/attestare troppe volte in uno slot). Nelle loro forme più basilari, queste azioni sono gestite facilmente dall'algoritmo di scelta della diramazione e dal livello d'incentivazione, ma esistono metodi più intelligenti per imbrogliare il sistema a vantaggio dell'utente malevolo.

### Attacchi con piccoli importi di ETH {#attacks-by-small-stakeholders}

#### riorganizzazioni {#reorgs}

Svariati documenti hanno spiegato gli attacchi a Ethereum che ottengono riorganizzazioni o ritardi di finalità con soltanto una piccola quota dell'ether in staking totale. Questi, generalmente, si affidano al fatto che l'utente malevolo trattenga alcune informazioni da altri validatori per poi rilasciarle in modo sfumato e/o in un momento opportuno. Solitamente mirano a spostare alcuni blocchi onesti dalla catena canonica. [Neuder et al 2020](https://arxiv.org/pdf/2102.02247.pdf), hanno mostrato come un validatore malevolo possa creare e attestare un blocco (`B`) per uno slot specifico `n+1` ma evitare di propagarlo ad altri nodi sulla rete. Invece, si attiene a quel blocco attestato fino allo slot successivo `n+2`. Un validatore onesto propone un blocco (`C`) per lo slot `n+2`. Quasi simultaneamente, l'utente malevolo può rilasciare il proprio blocco trattenuto (`B`) e le attestazioni trattenute per esso, oltre ad attestare `B` come testa della catena con i propri voti per lo slot `n+2`, negando di fatto l'esistenza del blocco onesto `C`. Quando il blocco onesto `D` viene rilasciato, l'algoritmo di scelta della diramazione vede la costruzione di `D` in cima a `B` come più pesante della costruzione di `D` in cima a `C`. L'utente malevolo, dunque, è riuscito a rimuovere il blocco onesto `C` nello slot `n+2` dalla catena canonica utilizzando una riorganizzazione a priori di 1 blocco. [Un utente malevolo con il 34%](https://www.youtube.com/watch?v=6vzXwwk12ZE) dello stake ha ottime probabilità di riuscire nel suo attacco, come spiegato [in questa nota](https://notes.ethereum.org/plgVdz-ORe-fGjK06BZ_3A#Fork-choice-by-block-slot-pair). In teoria, però, questo attacco potrebbe essere tentato con stake inferiori. [Neuder et al 2020](https://arxiv.org/pdf/2102.02247.pdf) hanno descritto che questo attacco funziona con uno stake del 30%, ma è stato in seguito dimostrato come fattibile con il [2% dello stake totale](https://arxiv.org/pdf/2009.04987.pdf) e poi, ancora, per un [singolo validatore](https://arxiv.org/abs/2110.10086#) che utilizza le tecniche di bilanciamento che esamineremo nella prossima sezione.

![riorganizzazione a priori](reorg-schematic.png)

Un diagramma concettuale dell'attacco di riorganizzazione di un blocco descritto sopra (adattato da https://notes.ethereum.org/plgVdz-ORe-fGjK06BZ_3A#Fork-choice-by-block-slot-pair)

Un attacco più sofisticato può dividere l'insieme di validatori onesti in gruppi discreti aventi visioni diverse della testa della catena. Ciò è noto come **attacco di bilanciamento**. L'utente malevolo attende la propria possibilità di proporre un blocco e, quando arriva, tergiversa e ne propone due. Invia un blocco a metà dell'insieme dei validatori onesti e l'altro blocco all'altra metà. L'equivoco sarebbe rilevato dall'algoritmo di scelta della diramazione e il propositore di blocchi riceverebbe un taglio e sarebbe espulso dalla rete, ma i due blocchi continuerebbero a esistere e avrebbe circa metà dell'insieme dei validatori ad attestarlo per ogni diramazione. Nel mentre, i validatori malevoli rimanenti trattengono le proprie attestazioni. Quindi, rilasciando selettivamente le attestazioni a favore dell'una o dell'altra diramazione al numero sufficiente di validatori, proprio come eseguito dall'algoritmo di scelta della diramazione, portano il peso accumulato delle attestazioni a favore di una o dell'altra diramazione. Questo può continuare per sempre, con i validatori malevoli che mantengono una divisione equa dei validatori tra le due diramazioni. Poiché nessuna delle due diramazioni può attrarre una supermaggioranza dei 2/3, la Beacon Chain non si finalizzerebbe.

Gli **attacchi di rimbalzo** sono simili. Anche in questo caso i voti sono trattenuti dai validatori malevoli. Invece di rilasciarli per mantenere una divisione equa tra le due diramazioni, utilizzano i propri voti nei momenti opportuni per giustificare punti di controllo che si alternano tra la diramazione A e la diramazione B. Questo tira e molla di giustificazioni tra le due diramazioni impedisce la presenza di coppie di punti di controllo di origine e di destinazione giustificati finalizzabili su una delle due catene, interrompendo la finalità.

<YouTube id="xcPxwhrg3Ao"/>

Sia gli attacchi di rimbalzo che quelli di bilanciamento si basano sul fatto che l'utente malevolo abbia un controllo molto preciso sulle tempistiche dei messaggi attraverso la rete, il che è improbabile. Tuttavia, le difese sono integrate nel protocollo sotto forma di ponderazione aggiuntiva data ai messaggi immediati rispetto a quelli lenti. Ciò è noto come [incremento del peso del propositore](https://github.com/ethereum/consensus-specs/pull/2730). Per difendersi dagli attacchi di rimbalzo, l'algoritmo di scelta della diramazione è stato aggiornato così che l'ultimo punto di controllo giustificato possa passare a quello di una catena alternativa soltanto durante il [primo 1/3 degli slot in ogni epoca](https://ethresear.ch/t/prevention-of-bouncing-attack-on-ffg/6114). Questa condizione impedisce all'utente malevolo di risparmiare voti da distribuire in seguito: l'algoritmo di scelta della diramazione, semplicemente, resta leale al punto di controllo che ha scelto nel primo 1/3 dell'epoca in cui avrebbero votato i validatori più onesti.

Combinate, queste misure creano uno scenario in cui un propositore di blocchi onesto emette il proprio blocco molto rapidamente dopo l'inizio dello slot, poi c'è un periodo di circa 1/3 di slot (4 secondi) in cui quel nuovo blocco potrebbe causare il passaggio dell'algoritmo di scelta della diramazione a un'altra catena. Dopo quella stessa scadenza, le attestazioni che arrivano dai validatori lenti sono deponderate rispetto a quelle arrivate prima. Ciò favorisce fortemente i propositori e validatori rapidi nel determinare la testa della catena, riducendo sostanzialmente la probabilità di riuscita di un attacco di bilanciamento o di rimbalzo.

Vale la pena notare che il solo potenziamento del propositore difende solo dalle "riorganizzazioni convenienti", cioè quelle tentate da un utente malevolo con uno stake ridotto. Difatti, lo stesso potenziamento del propositore è raggirabile dai detentori di stake maggiori. Gli autori di [questo post](https://ethresear.ch/t/change-fork-choice-rule-to-mitigate-balancing-and-reorging-attacks/11127) descrivono come un utente malevolo con il 7% dello stake possa distribuire i propri voti strategicamente per indurre i validatori onesti a costruire sulla sua diramazione, riorganizzando un blocco onesto. Questo attacco è stato concepito supponendo condizioni di latenza ideali, che sono molto improbabili. Le probabilità sono ancora fortemente a sfavore dell'utente malevolo, e lo stake maggiore comporta anche un maggiore capitale a rischio e un disincentivo economico persino più forte.

È stato proposto anche un [attacco di bilanciamento specificamente mirato alla regola LMD](https://ethresear.ch/t/balancing-attack-lmd-edition/11853), suggerito come fattibile nonostante il potenziamento del propositore. Un utente malevolo configura due catene in competizione, equivocando la proposta di blocchi e propagando ogni blocco a circa metà della rete, configurando un saldo approssimativo tra le due diramazioni. Quindi, i validatori complici equivocano i propri voti, fissando tempistiche tali che metà della rete riceva prima i loro voti per la diramazione `A` e l'altra metà riceva prima i loro voti per la diramazione `B`. Poiché la regola LMD scarta la seconda attestazione e mantiene soltanto la prima per ogni validatore, metà della rete visualizza i voti per `A` e nessun voto per `B`, l'altra metà vede i voti per `B` e nessun voto per `A`. Gli autori descrivono la regola LMD come dare all'avversario "notevole potere" per effettuare un attacco di bilanciamento.

Questo vettore di attacco LMD è stato chiuso [aggiornando l'algoritmo di scelta della diramazione](https://github.com/ethereum/consensus-specs/pull/2845) in modo che scarti del tutto i validatori equivoci dalla considerazione della scelta della diramazione. L'algoritmo di scelta della diramazione, inoltre, ignorerà l'influenza futura dei validatori equivoci. Ciò impedisce l'attacco di bilanciamento delineato sopra, mantenendo la resilienza contro attacchi valanga.

Un'altra classe di attacchi, detta [**attacchi valanga**](https://ethresear.ch/t/avalanche-attack-on-proof-of-stake-ghost/11854/3), è stata descritta in un [documento di marzo 2022](https://arxiv.org/pdf/2203.01315.pdf). Per causarlo, l'utente malevolo deve controllare diversi propositori di blocchi consecutivi. In ognuno degli slot di proposta del blocco, l'utente malevolo trattiene il proprio blocco, raccogliendoli finché la catena onesta non raggiunge un peso dell'albero secondario equivalente ai blocchi trattenuti. Poi, i blocchi trattenuti vengono rilasciati così che equivochino al massimo. Gli autori suggeriscono che il potenziamento del propositore – la prima difesa contro gli attacchi di bilanciamento e di rimbalzo – non protegge da alcune varianti dell'attacco valanga. Tuttavia, gli autori hanno anche dimostrato l'attacco soltanto su una versione altamente idealizzata dell'algoritmo di scelta della diramazione (hanno utilizzato GHOST senza LMD).

L'attacco valanga è mitigato dalla porzione LMD dell'algoritmo di scelta della diramazione LMD-GHOST. LMD sta per "guidato dall'ultimo messaggio" e si riferisce a una tabella tenuta da ogni validatore, contenente l'ultimo messaggio ricevuto dagli altri validatori. Quel campo viene aggiornato soltanto se il nuovo messaggio proviene da uno slot successivo a quello già nella tabella per uno specifico validatore. In pratica, ciò significa che in ogni slot, il primo messaggio ricevuto è quello che ha accettato e qualsiasi altro messaggio è un equivoco da ignorare. In altre parole, i client di consenso non contano gli equivoci – utilizzano il primo messaggio in arrivo da ogni validatore e gli equivoci sono semplicemente scartati, impedendo gli attacchi valanga.

Esistono diversi altri potenziali aggiornamenti futuri alla regola di scelta della diramazione che potrebbero sommarsi alla sicurezza fornita dal potenziamento del propositore. Uno è [view-merge](https://ethresear.ch/t/view-merge-as-a-replacement-for-proposer-boost/13739), dove gli attestatori congelano la propria vista della scelta della diramazione `n` secondi prima dell'inizio di uno slot e il propositore di blocchi quindi aiuta a sincronizzare la vista della catena nella rete. Un altro aggiornamento potenziale è la [finalità del singolo slot](https://notes.ethereum.org/@vbuterin/single_slot_finality), che protegge dagli attacchi basati sulla tempistica del messaggio finalizzando la catena dopo un solo slot.

#### Ritardo della finalità {#finality-delay}

[Lo stesso documento](https://econcs.pku.edu.cn/wine2020/wine2020/Workshop/GTiB20_paper_8.pdf) che prima descriveva l'attacco di riorganizzazione del blocco singolo a basso costo, descriveva anche un attacco di ritardo di finalità (anche noto come "perdita di vitalità"), che si basa sul fatto che 'utente malevolo proponga il blocco per un blocco di confine dell'epoca. Questo è fondamentale perché questi blocchi di confine dell'epoca diventano i punti di controllo che Casper FFG utilizza per finalizzare porzioni della catena. L'utente malevolo, semplicemente, trattiene il blocco finché abbastanza validatori onesti non utilizzano i propri voti FFC a favore del precedente blocco di confine dell'epoca come destinazione di finalizzazione corrente. Quindi, rilasciano il blocco trattenuto. Attestano al proprio blocco, così come i validatori onesti rimanenti, creando diramazioni con punti di controllo di destinazione differenti. Se hanno tempistiche corrette, impediranno la finalità perché non ci sarà una supermaggioranza dei 2/3 che attesti a entrambe le diramazioni. Minore è lo stake, più precisa deve essere la tempistica, poiché l'utente malevolo controlla meno attestazioni direttamente, e minori sono le probabilità che l'utente malevolo controlli il validatore che propone un dato di confine dell'epoca.

#### Attacchi a lungo raggio {#long-range-attacks}

Esiste inoltre una classe di attacco specifica delle blockchain di proof-of-stake che comporta che un validatore che ha partecipato al blocco di genesi mantenga una diramazione separata della blockchain insieme a quella onesta, convincendo infine l'insieme di validatori onesti a passare ad essa in un dato momento opportuno molto successivo. Questo tipo di attacco non è possibile su Ethereum per via del dispositivo di finalità che assicura che tutti i validatori concordino sullo stato della catena onesta a intervalli regolari ("punti di controllo"). Questo semplice meccanismo neutralizza gli attacchi a lungo raggio, poiché i client di Ethereum semplicemente non riorganizzeranno i blocchi finalizzati. I nuovi nodi che si uniscono alla rete lo fanno trovando un hash di stato recente fidato (un "[punto di controllo a soggettività debole](https://blog.ethereum.org/2014/11/25/proof-stake-learned-love-weak-subjectivity/)") e utilizzandolo come un blocco di pseudo-genesi su cui costruire. Questo crea una 'porta di fiducia' per un nuovo nodo che accede alla rete prima che possa iniziare a verificare le informazioni da solo.

#### Denial of Service {#denial-of-service}

Il meccanismo di PoS di Ethereum seleziona un unico validatore dall'insieme di validatori totali perché sia un propositore di blocchi in ogni slot. Questo è calcolabile utilizzando una funzione pubblicamente nota ed è possibile, per un avversario, identificare il propositore di blocco successivo lievemente in anticipo rispetto alla sua proposta del blocco. Poi, l'utente malevolo può spammare il propositore del blocco per impedirgli di scambiare le informazioni con i suoi pari. Al resto della rete sembrerà che il propositore del blocco sia offline e lo slot resterà semplicemente vuoto. Questo potrebbe essere una forma di censura contro validatori specifici, che impedisce loro di aggiungere informazioni alla blockchain. L'implementazione di elezioni segrete di un singolo capo (SSLE) o di elezioni segrete di un capo non singolo mitigheranno i rischi di DoS, poiché soltanto il propositore del blocco potrà sapere di essere stato selezionato e la selezione non è nota in anticipo. Ciò non è ancora implementato, ma è un'area attiva di [ricerca e sviluppo](https://ethresear.ch/t/secret-non-single-leader-election/11789).

Tutto questo punta al fatto che sia davvero difficile attaccare Ethereum con successo con uno stake ridotto. Gli attacchi fattibili qui descritti richiedono un algoritmo di scelta della diramazione idealizzato, condizioni di rete improbabili, oppure i vettori d'attacco sono già stati chiusi con correzioni relativamente minori al software del client. Questo, ovviamente, non esclude la possibilità che si verifichino zero day, ma dimostra la barra estremamente elevata di capacità tecnica, conoscenza del livello di consenso e fortuna necessaria perché un utente malevolo con uno stake di minoranza sia efficace. Dalla prospettiva di un utente malevolo, la cosa migliore dare sarebbe accumulare quanto più ether possibile e tornare armato di una maggiore quota dello stake totale.

### Utenti malevoli che utilizzano il >= 33% dello stake totale {#attackers-with-33-stake}

Tutti gli attacchi menzionati precedentemente in questo articolo raggiungono una maggiore probabilità di riuscita quando l'utente malevolo ha più ether in staking con cui votare, e più validatori che potrebbero essere scelti per proporre i blocchi in ogni slot. Un validatore malevolo potrebbe dunque mirare a controllare quanto più ether possibile.

Il 33% dell'ether in staking è un punto di riferimento per un utente malevolo poiché, con un qualsiasi importo maggiore, può impedire la finalizzazione della catena senza dover controllare finemente le azioni degli altri validatori. Possono semplicemente scomparire insieme. Se 1/3 o più dell'ether in staking attesta malevolmente o non riesce ad attestare, allora non può esistere una supermaggioranza dei 2/3 e la catena non può finalizzare. La difesa in questo caso è la perdita per inattività. La perdita per inattività identifica quei validatori che non attestano o che attestano il contrario della maggioranza. L'ether in staking posseduto da tali validatori non attestanti è gradualmente disperso finché non rappresenteranno collettivamente meno di 1/3 del totale, così che la catena possa nuovamente finalizzare.

Lo scopo della perdita per inattività è far nuovamente finalizzare la catena. Tuttavia, l'utente malevolo perde anche una porzione del proprio ether in staking. L'inattività persistente tra validatori che rappresentano il 33% dell'ether in staking totale è molto costosa anche se i validatori non ricevono un taglio.

Supponendo che la rete di Ethereum sia asincrona (cioè, ci siano ritardi tra i messaggi inviati e ricevuti), un utente malevolo che controlla il 34% dello stake totale potrebbe causare una doppia finalità. Ciò è dovuto al fatto che l'utente malevolo può equivocare quando è scelto come propositore di blocchi, poi votare due volte con tutti i suoi validatori. Questo crea una situazione in cui esiste una diramazione della blockchain, ciascuna votata dal 34% dell'ether in staking. Ogni diramazione richiede soltanto il 50% dei voti dei validatori rimanenti per entrambe le diramazioni per essere supportata da una supermaggioranza, nel qual caso entrambe le catene possono finalizzarsi (poiché il 34% dei validatori malevoli + metà dei rimanenti 66% = 67% su ogni diramazione). Ogni blocco concorrente dovrebbe essere ricevuto all'incirca dal 50% dei validatori onesti, quindi questo attacco è fattibile soltanto quando l'utente malevolo ha un certo grado di controllo sulla tempistica dei messaggi che si propagano per la rete così da poter ingannare metà dei validatori onesti su ogni catena. L'utente malevolo dovrebbe necessariamente distruggere integralmente il proprio stake (34% di circa 10 milioni di ether con l'insieme odierno di validatori) per ottenere tale doppia finalità, poiché il 34% dei validatori voterebbe due volte simultaneamente – un'infrazione punibile con la sanzione di correlazione massima. La difesa contro questo attacco è il costo molto elevato della distruzione del 34% dell'ether in staking totale. Riprendersi da tale attacco richiederebbe alla community di Ethereum di coordinarsi "fuori banda" e di accordarsi sul seguire una delle due diramazioni ignorando l'altra.

### Utenti malevoli che utilizzano circa il 50% dello stake totale {#attackers-with-50-stake}

Al 50% dell'ether in staking, un gruppo malevolo di validatori potrebbe teoricamente dividere la catena in due diramazioni di pari dimensioni e quindi semplicemente utilizzare tutto il proprio 50% dello stake per votare contrariamente all'insieme di validatori onesti, mantenendo così le due diramazioni e impedendo la finalità. La perdita per inattività su entrambe le diramazioni condurrebbe infine alla finalizzazione di entrambe le catene. A questo punto, l'unica opzione è fare affidamento su un recupero sociale.

È molto improbabile che un gruppo avversario di validatori possa controllare coerentemente e precisamente il 50% dello stake totale, dato il livello di flusso di numeri di validatori onesti, la latenza di rete, ecc.; il costo elevato di effettuare un simile attacco, insieme alla bassa probabilità di successo, sembra essere un forte disincentivo per un utente malevolo razionale, specialmente se un piccolo investimento aggiuntivo per ottenere _oltre il_ 50% sblocca molto più potere.

Al >50% dello stake totale, l'utente malevolo potrebbe dominare l'algoritmo di scelta della diramazione. In questo caso sarebbe in grado di attestare con il voto di maggioranza, ottenendo controllo sufficiente per effettuare brevi riorganizzazioni senza dover ingannare i client onesti. I validatori onesti farebbero lo stesso perché anche il loro algoritmo di scelta della diramazione vederebbe la catena preferita dall'utente malevolo come la più pesante, quindi la catena potrebbe finalizzarsi. Ciò consente all'utente malevolo di censurare certe transazioni, apportare riorganizzazioni a breve raggio ed estrarre il MEV massimo riordinando i blocchi a proprio favore. La difesa contro tale attacco è l'enorme costo di uno stake di maggioranza (attualmente di poco inferiore a 19 miliardi di USD) messo a rischio da un utente malevolo, poiché il livello sociale potrebbe intervenire e adottare una diramazione di minoranza onesta svalutando drasticamente lo stake dell'utente malevolo.

### Utenti malevoli che utilizzano il >=66% dello stake totale {#attackers-with-66-stake}

Un utente malevolo con il 66% o più dell'ether in staking totale può finalizzare la propria catena preferita senza dover forzare alcun validatore onesto. L'utente può semplicemente votare la propria diramazione preferita per poi finalizzarla, semplicemente perché può votare con una supermaggioranza disonesta. Come detentore della supermaggioranza, controllerebbe sempre i contenuti dei blocchi finalizzati, con il potere di spendere, riavvolgere e rispendere, censurare certe transazioni e riorganizzare a piacimento la catena. Acquistando ulteriore ether per controllare il 66% invece del 51%, l'utente malevolo acquisisce di fatto l'abilità di effettuare riorganizzazioni a posteriori e inversioni di finalità (cioè, modificare il passato e controllare il futuro). Le sole vere difese sono il costo enorme del 66% dell'ether in staking totale e l'opzione di fare affidamento sul livello sociale per coordinare l'adozione di una diramazione alternativa. Possiamo affrontarlo in maggiore dettaglio nella sezione seguente.

## Persone: l'ultima linea di difesa {#people-the-last-line-of-defense}

Se i validatori disonesti riescono a finalizzare la propria versione preferita della catena, la community di Ethereum è messa in una situazione difficile. La catena canonica include una sezione disonesta fusa nel suo storico, mentre i validatori onesti possono ritrovarsi puniti per aver attestato una catena (onesta) alternativa. Si noti che una catena finalizzata ma errata potrebbe sorgere anche da un bug in un client di maggioranza. Infine, il ripiego finale è affidarsi al livello sociale, al Livello 0, per risolvere la situazione.

Uno dei punti di forza del consenso di PoS di Ethereum è che esistono [svariate strategie difensive](https://youtu.be/1m12zgJ42dI?t=1712) impiegabili dalla community di fronte a un attacco. Una risposta minima potrebbe essere l'uscita forzata dei validatori malevoli dalla rete senza alcuna sanzione aggiuntiva. Per rientrare nella rete, l'utente malevolo dovrebbe unirsi a una coda di attivazione che assicura all'insieme di validatori di crescere gradualmente. Ad esempio, aggiungere abbastanza validatori da raddoppiare la quantità di ether in staking richiede circa 200 giorni, acquisendo effettivamente i validatori onesti con 200 giorni d'anticipo prima che l'utente malevolo possa tentare un altro attacco del 51%. Tuttavia, la community potrebbe anche decidere di penalizzare l'utente malevolo più duramente, revocando le ricompense passate o bruciando una certa porzione (fino al 100%) del suo capitale in staking.

Qualsiasi sia la sanzione imposta all'utente malevolo, la community deve anche decidere se la catena disonesta, sebbene sia quella preferita dall'algoritmo di scelta della diramazione codificato nei client di Ethereum, sia di fatto non valida e se la community dovrebbe costruire, invece, sulla catena onesta. I validatori onesti potrebbero concordare collettivamente di costruire una diramazione accettata dalla community della blockchain di Ethereum che potrebbe, ad esempio, essersi separata dalla catena canonica prima dell'inizio dell'attacco o far rimuovere forzatamente i validatori malevoli. I validatori onesti sarebbero incentivati a costruire su questa catena, evitando le sanzioni loro applicate per la mancata attestazione (giustamente) della catena dell'utente malevolo. Le borse, on-ramp e applicazioni basate su Ethereum preferirebbero presumibilmente rimanere sulla catena onesta e seguirebbero i validatori onesti nella blockchain onesta.

Tuttavia, questa sarebbe una sostanziale sfida di governance. Alcuni utenti e validatori andrebbero senza dubbio in perdita come conseguenza del ritorno alla catena onesta, le transazioni nei blocchi convalidati dopo l'attacco potrebbero essere potenzialmente ripristinate, disturbando il livello d'applicazione e, semplicemente, minando l'etica di alcuni utenti che tendono a credere che "il codice sia legge". Le borse e le applicazioni avrebbero molto probabilmente azioni esterne alla catena collegate alle transazioni sulla catena che ora potrebbero essere ripristinate, creando una cascata di ritrattazioni e revisioni che sarebbero difficili da disfare correttamente, specialmente se mischiate con guadagni disonesti, depositati nella DeFi o altri derivati con effetti secondari per gli utenti onesti. Indubbiamente alcuni utenti, forse persino istituzionali, avrebbero già beneficiato dalla catena disonesta, per scaltrezza o fortuna, e potrebbero opporsi a una diramazione per proteggere i propri guadagni. Ci sono state richieste di provare la risposta della community agli attacchi >51% così che una ragionevole mitigazione coordinata sia eseguibile rapidamente. Alcune utili osservazioni di Vitalik sono riportate su ethresear.ch [qui](https://ethresear.ch/t/timeliness-detectors-and-51-attack-recovery-in-blockchains/6925) e [qui](https://ethresear.ch/t/responding-to-51-attacks-in-casper-ffg/6363) e su Twitter, [qui](https://twitter.com/skylar_eth/status/1551798684727508992?s=20&t=oHZ1xv8QZdOgAXhxZKtHEw). L'obiettivo di una risposta sociale coordinata dovrebbe essere molto mirato e specifico sulla punizione dell'utente malevolo e sulla minimizzazione degli effetti per gli altri utenti.

La governance è già un argomento complicato. Gestire la risposta all'emergenza del Livello 0 a una catena in finalizzazione disonesta sarebbe senza dubbio impegnativo per la community di Ethereum, ma [è successo](https://ethereum.org/en/history/#dao-fork-summary), [due volte](https://ethereum.org/en/history/#tangerine-whistle) nella storia di Ethereum).

Tuttavia, c'è qualcosa di abbastanza soddisfacente nel ripiego finale nel mondo reale. In definitiva, anche con questo fenomenale stack tecnologico sopra di noi, se il peggio dovesse verificarsi le persone in carne ed ossa dovrebbero coordinarsi per uscirne.

## Riepilogo {#summary}

Questa pagina ha esplorato alcuni dei metodi in cui gli utenti malevoli potrebbero tentare di sfruttare il protocollo di consenso del proof-of-stake di Ethereum. Le riorganizzazioni e i ritardi di finalità sono stati esaminati per gli utenti malevoli con quote crescenti dell'ether in staking totale. In generale, un utente malevolo più ricco ha maggiori possibilità di successo perché il suo stake si traduce in potere di voto che può utilizzare per influenzare i contenuti dei blocchi futuri. A certi importi di soglia di ether in staking, il potere dell'utente malevolo aumenta:

33%: ritardo di finalità

34%: ritardo di finalità, doppia finalità

51%: ritardo di finalità, doppia finalità, censura, controllo sul futuro della blockchain

66%: ritardo di finalità, doppia finalità, censura, controllo sul futuro e il passato della blockchain

Esiste anche una serie di attacchi più sofisticati che richiedono piccoli importi di ether in staking ma si affidano ad attacchi molto sofisticati con il pieno controllo sulla tempistica dei messaggi per influenzare l'insieme di validatori a proprio favore.

In generale, nonostante questi potenziali vettori d'attacco, il rischio di un attacco di successo è basso, certamente inferiore degli equivalenti del proof-of-work. Questo perché l'elevato costo dell'ether in staking è messo a rischio da un utente malevolo che mira a sopraffare i validatori onesti con il loro potere di voto. Il livello di incentivazione integrato del "bastone e carota" protegge contro gran parte dei malfattori, specialmente con stake minori. Anche i più subdoli attacchi di rimbalzo e di bilanciamento hanno poca probabilità di successo poiché le vere condizioni di rete rendono molto difficile ottenere il pieno controllo della consegna del messaggio a sottoinsiemi specifici di validatori, e i team dei client hanno rapidamente chiuso i vettori degli attacchi di rimbalzo, bilanciamento e valanga con semplici correzioni.

Gli attacchi del 34%, 51% o 66% richiederebbero un coordinamento fuori banda per essere risolti. Mentre ciò sarebbe probabilmente doloroso per la community, la sua capacità di rispondere fuori banda è un forte disincentivo per un utente malevolo. Il livello sociale di Ethereum è l'ultima rete di protezione: un attacco tecnicamente riuscito potrebbe ancora essere neutralizzato dalla community che si accorda per accettare una diramazione onesta. Ci sarebbe una gara tra l'utente malevolo e la community di Ethereum: i miliardi di dollari spesi su un attacco del 66% sarebbero probabilmente annientati da un attacco di coordinamento sociale con esito positivo se fosse realizzato abbastanza rapidamente, lasciando l'utente malevolo con pesanti sacchi di ether in staking illiquidi su una catena notoriamente disonesta ignorata dalla community di Ethereum. La probabilità che ciò finisca per essere redditizio per l'utente è sufficientemente bassa da essere un deterrente efficace. Per questo l'investimento nel mantenere un livello sociale coeso con valori strettamente allineati è così importante.

## Letture consigliate {#further-reading}

- [Versione più dettagliata di questa pagina](https://mirror.xyz/jmcook.eth/YqHargbVWVNRQqQpVpzrqEQ8IqwNUJDIpwRP7SS5FXs)
- [Vitalik sulla finalità dell'accordo](https://blog.ethereum.org/2016/05/09/on-settlement-finality/)
- [Documento LMD GHOST](https://arxiv.org/abs/2003.03052)
- [Documento Casper-FFG](https://arxiv.org/abs/1710.09437)
- [Documento Gasper](https://arxiv.org/pdf/2003.03052.pdf)
- [Specifiche del consenso di incremento del peso del propositore](https://github.com/ethereum/consensus-specs/pull/2730)
- [Attacchi di rimbalzo su ethresear.ch](https://ethresear.ch/t/prevention-of-bouncing-attack-on-ffg/6114)
- [Ricerca sul SSLE](https://ethresear.ch/t/secret-non-single-leader-election/11789)