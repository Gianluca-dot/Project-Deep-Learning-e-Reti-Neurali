1. Introduzione:
- Scopi del progetto
- Problema affrontato
- Motivazione della scelta della CNN
- Eventuale confronto tra CNN custom e transfer learning

2. Descrizione del dataset CIFAR-10
- Presentazione del dataset
- Numero di classi
- Numero di immagini
- Dimensione delle immagini
- Esempi visivi
- Osservazioni sul compito di classificazione
  
3. Importazione delle librerie
- Librerie per dati e visualizzazione
- Librerie per deep learning
- Librerie per eventuali modelli pre-addestrati
  
4. Caricamento e preparazione dei dati
- Download e caricamento del dataset
- Split tra train, validation e test
- Normalizzazione delle immagini
- Codifica delle etichette
  
5. Data Augmentation
- Motivazione dell’uso della data augmentation
- Tecniche applicate
- Esempi di immagini aumentate
- Benefici attesi sulla generalizzazione
  
6. Definizione dell’architettura del modello
- Struttura generale della CNN o del modello con transfer learning
- Strati convoluzionali o backbone pre-addestrato
- Strati di pooling
- Strati fully connected
- Dropout e sua funzione regolarizzante
- Funzione di attivazione finale
- Motivazione delle scelte architetturali
  
7. Compilazione del modello
- Loss function
- Optimizer
- Metriche di valutazione
  
8. Addestramento del modello
- Numero di epoche
- Batch size
- Utilizzo di EarlyStopping
- Eventuali altri callback
- Salvataggio del miglior modello
  
9. Analisi dei risultati del training
- Grafico di accuracy
- Grafico di loss
- Confronto tra train e validation
- Discussione di overfitting o underfitting
  
10. Valutazione sul test set
- Accuracy finale
- Altre metriche
- Confronto tra addestramento e test
  
11. Analisi dettagliata delle prestazioni
- Confusion matrix
- Classi più confuse
- Errori più frequenti
- Interpretazione dei risultati
  
12. Limiti del modello
- Limiti del dataset
- Limiti della generalizzazione
- Effetti della bassa risoluzione delle immagini
- Limiti dell’architettura scelta
  
13. Possibili miglioramenti futuri
- Ottimizzazione dell’architettura
- Maggiore data augmentation
- Ulteriore fine-tuning
- Test su dataset differenti
- Confronto con altre reti
  
14. Conclusioni
- Sintesi dei risultati ottenuti
- Considerazioni finali
- Valutazione rispetto agli obiettivi iniziali
  
15. Riferimenti
- Fonti consultate
- Documentazione
- Dataset utilizzati

Data Augmentation va prima dell’addestramento, perché serve a preparare i dati
Dropout va nella definizione dell’architettura, perché è parte del modello
EarlyStopping va nella fase di training, perché è un callback che controlla l’addestramento
Un esempio pratico di organizzazione:

prima definisco le trasformazioni di augmentation
poi costruisco la rete con Dropout
poi addestro il modello con EarlyStopping attivo


* CONFRONTO TRA CNN CUSTOM E TRASNSFER LEARNING CON UN MODELLO PRE ADDESTRATO ResNet

In generale, per un progetto su CIFAR-10 ci sono due approcci sensati:

CNN costruita da zero
Transfer learning con un modello pre-addestrato, come ResNet
La soluzione migliore, dal punto di vista didattico, spesso è confrontare i due approcci. Questo permette di mostrare:

come funziona una CNN progettata da zero
come cambia il comportamento usando un modello pre-addestrato
quali vantaggi e svantaggi ha il transfer learning rispetto a una rete costruita manualmente
In questo caso, il transfer learning ha senso perché:

ResNet ha già imparato filtri generici molto utili
spesso converge più velocemente
può dare prestazioni migliori, soprattutto se il training set non è enorme
permette di discutere in modo interessante il tema della riusabilità dei modelli
Però ci sono anche alcune problematiche:
CIFAR-10 ha immagini piccole, quindi spesso bisogna adattare l’input al formato richiesto da ResNet
se si usa un modello pre-addestrato, devi spiegare bene cosa hai congelato e cosa hai riaddestrato
il docente potrebbe aspettarsi che tu motivi chiaramente perché hai scelto il transfer learning
Quindi:

se il progetto deve essere semplice e lineare, si esegue solo una CNN
se si vuole fare un progetto più completo e forte, fai un confronto tra CNN da zero e transfer learning con ResNet
In questo secondo caso, il notebook potrebbe avere una struttura del tipo:

modello 1: CNN custom
modello 2: ResNet con transfer learning
confronto finale su accuracy, loss, confusion matrix e tempi di addestramento
Così l'analisi finale diventa molto più ricca, perché si può dire non solo “il modello funziona”, ma anche “questo approccio è migliore di quest’altro e per quali motivi”.

Un esempio di confronto utile potrebbe essere:

CNN custom: più semplice, più interpretabile, ma prestazioni inferiori
ResNet: più complessa, più potente, spesso più accurata, ma meno trasparente e più costosa computazionalmente
Quindi, in sintesi: sì, il transfer learning conviene, ma ancora meglio è usarlo come confronto con una rete creata da zero, se si ha tempo e si vuole un progetto più convincente.

inserire solo le due classi: animali e veicoli, escludendo dal dataset aerei e navi, sia la soluzione più logica e preferibile anche a quella di inserire una soglia di confidenza, perchè il problrema chiede di classificare le immagini il più correttamente possibile tra veicoli ed animali e quindi non includere la classe aerei e navi si può considerare come una operazione di pulizia del dataset, operazione che si compie sempre prima di far eseguire le operazioni di addestramento e validazione.

La scelta di tenere solo le due macro-classi:

animali
veicoli stradali
ed escludere:

aerei
navi
è la più logica  e più coerente rispetto all’uso di una soglia di confidenza, perché:

il problema richiesto è binario
l’obiettivo è classificare il più correttamente possibile tra due sole categorie
le classi non pertinenti introdurrebbero rumore concettuale nel dataset
la pulizia del dataset è una fase normale e necessaria prima del training e della validation
Dal punto di vista metodologico, stai facendo una selezione del dataset in base al problema da risolvere. Questo non è un “trucco”, ma una buona pratica di preprocessing e di data curation.

La soglia di confidenza, invece, sarebbe utile se si volesse costruire un sistema che debba anche gestire immagini fuori distribuzione o categorie sconosciute. Ma in questo caso non è il focus del problema, quindi è meno adatta.

Quindi la formulazione più corretta da usare nel progetto è qualcosa del tipo: “Per rendere il problema coerente con l’obiettivo di classificare immagini tra veicoli e animali, sono state mantenute soltanto le classi pertinenti del dataset CIFAR-10, escludendo aerei e navi in quanto non appartenenti alla categoria dei veicoli stradali.”

Questo permette di:

avere un dataset più pulito
rendere il compito più chiaro
evitare ambiguità nella valutazione
lavorare su un problema ben definito
Un piccolo accorgimento: quando si scriverà il notebook, si specificherà sempre che non si stà usando CIFAR-10 completo, ma un sottoinsieme selezionato del dataset.
Questo rende la metodologia trasparente e professionale.
