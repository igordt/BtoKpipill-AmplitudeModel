# BtoKpipill-AmplitudeModel

## Descrizione

Questo repository contiene i calcoli sviluppati per lo studio del decadimento **B⁺ → K⁺π⁺π⁻ℓ⁻ℓ⁺** nell'ambito della tesi "Amplitude model for 5-body b → s ℓ⁻ℓ⁺ decays".
L'obiettivo principale è ottenere la rate differenziale di decadiemnto tramite la costruzione dell'ampiezza totale di decadimento utilizzando il formalismo di elicità.
La rate differenziale viene decomposta in termini di funzioni angolari ortogonali e i momenti associati.

## Struttura del Repository

### Calcolo dell'Ampiezza Espansa

**File:** [`ExpandedAmplitude/Ampiezza.ipynb`](ExpandedAmplitude/Ampiezza.ipynb)

Questo notebook calcola l'ampiezza di decadimento sommando i contributi delle diverse risonanze intermedie (canali three-body, one-resonance e two-resonances). L'ampiezza viene espansa trigonometricamente in termini di funzioni seno e coseno, ottenendo un'espressione in cui la dipendenza angolare è esplicita. I risultati intermedi e finali vengono salvati come file `.pkl` nella cartella `ExpandedAmplitude`.

**Contenuto della cartella `ExpandedAmplitude`:**
- `Ampiezza.ipynb` - Notebook principale per il calcolo dell'ampiezza espansa
- File `.pkl` - Risultati salvati (coefficienti trigonometrici, chiralità, momenti semplificati)

### Calcolo dell'Ampiezza con Funzioni di Wigner

**File:** [`WignerAmplitude/AmpiezzaWigner.ipynb`](WignerAmplitude/AmpiezzaWigner.ipynb)

Questo notebook calcola l'ampiezza di decadimento utilizzando le matrici di rotazione di Wigner **D**. L'approccio mantiene la dipendenza angolare in forma compatta attraverso le funzioni di Wigner, che vengono poi combinate utilizzando i coefficienti di Clebsch-Gordan per costruire una base ortogonale di funzioni angolari. I momenti angolari associati a ciascuna funzione di base vengono calcolati e salvati.

**Contenuto della cartella `WignerAmplitude`:**
- `AmpiezzaWigner.ipynb` - Notebook principale per il calcolo con funzioni di Wigner
- File `.pkl` - Risultati salvati (base angolare, momenti, simmetrie, coefficienti semplificati)

### Notebook di Studio e Validazione

- **[`B to Kℓℓ.ipynb`](B%20to%20Kℓℓ.ipynb)** - Studio del decadimento semplificato B → K ℓℓ (senza risonanze intermedie nel settore adronico), utilizzato come caso test per validare il formalismo.

- **[`B to Kπℓℓ.ipynb`](B%20to%20Kπℓℓ.ipynb)** - Studio del decadimento B → K π ℓℓ (con una risonanza intermedia), che rappresenta un caso intermedio tra B → K ℓℓ e il processo completo B → K π π ℓℓ.

- **[`LeptonicHA.ipynb`](LeptonicHA.ipynb)** - Calcolo esplicito delle ampiezze di elicità leptoniche nel limite di massa nulla e massiva dei leptoni. Questo notebook fornisce le espressioni utilizzate negli altri calcoli per la parte leptonica dell'ampiezza.

### Output dei Momenti Angolari

**Cartella:** [`Moments_Output/`](Moments_Output/)

Contiene i file di testo con i momenti angolari calcolati, organizzati per simmetria (ω = +1 o ω = -1).
Ogni file contiene la chiave della funzione angolare e l'espressione simbolica del momento associato in forma leggibile.

## Note

I calcoli sono computazionalmente intensivi e richiedono tempo di esecuzione significativo. Per questo motivo, i risultati intermedi vengono salvati in file `.pkl` che possono essere ricaricati per evitare di ripetere i calcoli.