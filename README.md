1. Introduzione
Obiettivo del progetto
Problema affrontato
Motivazione della scelta della CNN
Eventuale confronto tra CNN custom e transfer learning
2. Descrizione del dataset CIFAR-10
Presentazione del dataset
Numero di classi
Numero di immagini
Dimensione delle immagini
Esempi visivi
Osservazioni sul compito di classificazione
3. Importazione delle librerie
Librerie per dati e visualizzazione
Librerie per deep learning
Librerie per eventuali modelli pre-addestrati
4. Caricamento e preparazione dei dati
Download e caricamento del dataset
Split tra train, validation e test
Normalizzazione delle immagini
Codifica delle etichette
5. Data Augmentation
Motivazione dell’uso della data augmentation
Tecniche applicate
Esempi di immagini aumentate
Benefici attesi sulla generalizzazione
6. Definizione dell’architettura del modello
Struttura generale della CNN o del modello con transfer learning
Strati convoluzionali o backbone pre-addestrato
Strati di pooling
Strati fully connected
Dropout e sua funzione regolarizzante
Funzione di attivazione finale
Motivazione delle scelte architetturali
7. Compilazione del modello
Loss function
Optimizer
Metriche di valutazione
8. Addestramento del modello
Numero di epoche
Batch size
Utilizzo di EarlyStopping
Eventuali altri callback
Salvataggio del miglior modello
9. Analisi dei risultati del training
Grafico di accuracy
Grafico di loss
Confronto tra train e validation
Discussione di overfitting o underfitting
10. Valutazione sul test set
Accuracy finale
Altre metriche
Confronto tra addestramento e test
11. Analisi dettagliata delle prestazioni
Confusion matrix
Classi più confuse
Errori più frequenti
Interpretazione dei risultati
12. Limiti del modello
Limiti del dataset
Limiti della generalizzazione
Effetti della bassa risoluzione delle immagini
Limiti dell’architettura scelta
13. Possibili miglioramenti futuri
Ottimizzazione dell’architettura
Maggiore data augmentation
Ulteriore fine-tuning
Test su dataset differenti
Confronto con altre reti
14. Conclusioni
Sintesi dei risultati ottenuti
Considerazioni finali
Valutazione rispetto agli obiettivi iniziali
15. Riferimenti
Fonti consultate
Documentazione
Dataset utilizzati

Data Augmentation va prima dell’addestramento, perché serve a preparare i dati
Dropout va nella definizione dell’architettura, perché è parte del modello
EarlyStopping va nella fase di training, perché è un callback che controlla l’addestramento
Un esempio pratico di organizzazione:

prima definisco le trasformazioni di augmentation
poi costruisco la rete con Dropout
poi addestro il modello con EarlyStopping attivo
