# Aerobicizzazione

Raccolta di dati e studio di un indice di aerobicizzazione per valutare il miglioramento aerobico ottenuto con allenamenti a bassa intensità.

## 0. Obiettivo

Questo progetto vuole individuare un indice che misuri il miglioramento aerobico in soggetti che hanno una buona capacità di sostenere sforzi “fuori giri” ma che necessitano di consolidare la proprio base aerobica.

L'idea è analizzare un periodo di allenamento composto da sessioni a bassa intensità (Z1/Z2) e misurare l'impatto sull'efficienza. Per ridurre la variabilità quotidiana della frequenza cardiaca, l'analisi viene effettuata su base settimanale.

Ogni sessione viene pesata in base alla durata e alla variabilità della potenza erogata.

## 1. Dati e formula di calcolo

### 1.1 Dati grezzi

I dati registrati dai dispositivi di misurazione da considerare sono:

1. Durata attività in minuti **(DUR)**
2. Potenza media dell'attività **(PAVG)**
3. Potenza media normalizzata **(NP)**
4. Frequenza cardiaca media **(BPM)**

### 1.2 Dati derivati

1. **EF** - Efficiency Factor: indica l'efficienza espressa come rapporto tra potenza media e frequenza cardiaca media.
   $$EF = \frac{PAVG}{BPM}$$
2. **VI** - Variability Index: indica la variabilità della sessione, calcolato come rapporto tra potenza normalizzata e potenza media.
   $$VI = \frac{NP}{PAVG}$$
    In un allenamento di base aerobica ideale, questo rapporto tende a 1.

### 1.3 Formula finale

Per ogni attività il valore di efficienza corretto dalla variabilità è:

$$EF_{attività} = \frac{PAVG}{(VI × BPM)}$$

Il valore settimanale è la somma dei valori di ciascuna sessione ponderati per la durata:

$$EF_{sett} = \sum_{n=1}^{N} \left( \frac{\text{Potenza Media}_n}{VI_n \times \text{FC Media}_n} \times \frac{D_n}{D_{tot}} \right)$$

## 2. Valore di confronto

Un valore assoluto di `EF_sett` da solo non basta per capire quanto dell’efficienza potenziale viene utilizzata. Questo perché un atleta più forte può avere un valore maggiore indipendentemente dal suo grado di adattamento aerobico.

Per questo è utile confrontare il valore settimanale con un valore di riferimento teorico, cioè il massimo Efficiency Factor stimato.

### 2.1 Massimo Efficiency Factor

La stima del massimo `EF` si basa sull'intensità della FTP: se si assume che la FTP rappresenti la massima potenza generata principalmente dal motore aerobico e sostenibile a lungo, allora il rapporto tra FTP e frequenza cardiaca alla soglia può fornire una stima teorica di `MAX(EF)`.

### 2.2 Efficienza relativa

L'efficienza relativa è il rapporto tra l'Efficiency Factor settimanale e il massimo teorico:

$$Efficienza_{relativa} = \frac{EF_{sett}}{MAX(EF)}$$

Durante un periodo di allenamento aerobico (Z1/Z2) questo rapporto dovrebbe aumentare. Un valore di riferimento utile può essere 0.8: una volta raggiunto, significa che il motore aerobico è sufficientemente ottimizzato per poter aumentare la “cilindrata” e spostare l'allenamento verso intensità maggiori.

## 3. Raccolta dati

I dati verranno raccolti dalle attività Strava di atleti con un regime di allenamento noto. L'obiettivo è verificare se l'indice è uno strumento valido per misurare l'adattamento aerobico, privilegiando blocchi di allenamento di base aerobica.

### 3.1 Analisi e realizzazione tecnica

L'implementazione iniziale prevede un software Python in grado di generare riepiloghi CSV e grafici dai dati raccolti tramite le API di Strava.

## 4. Sviluppi futuri

Dopo l'analisi, la validazione e la revisione dell'algoritmo, si valuterà la possibilità di integrare lo strumento come plugin in una piattaforma estensibile di analisi dell'allenamento (ad esempio Intervals.icu), scegliendo la tecnologia più adatta.

## 5. Glossario

- **DUR**: durata dell'attività in minuti
- **PAVG**: potenza media
- **NP**: potenza normalizzata
- **BPM**: frequenza cardiaca media
- **EF**: Efficiency Factor
- **VI**: Variability Index


