# Applied Reinforcement Learning for Pac-Man Agents

Questo repository presenta un'analisi comparativa di agenti intelligenti addestrati con tecniche di **Reinforcement Learning (RL)** per giocare autonomamente a Pac-Man. Il progetto, basato sull'ambiente fornito dal corso **CS188 di Berkeley AI**, esplora e confronta due approcci fondamentali del RL: uno **Model-Based (Value Iteration)** e uno **Model-Free (Q-Learning)**.

![Grafico di Analisi delle Performance](./media/pacman_analysis_overview.png)
*(Esempio di analisi parametrica per ottimizzare il win rate dell'agente)*

---

### 📄 **Documentazione Completa**
*   [**Leggi la Relazione di Progetto Completa](./docs/relazione_rl_pacman.pdf)**
*   [**Visualizza le Slide di Presentazione](./docs/presentazione_rl_pacman.pdf)**

---

## 🎯 Obiettivo del Progetto

L'obiettivo è duplice:
1.  **Implementare e addestrare** agenti autonomi in grado di completare con successo i livelli di Pac-Man, massimizzando il punteggio.
2.  **Condurre un'analisi comparativa** tra l'algoritmo **Value Iteration** e **Q-Learning**, valutandone performance, adattabilità e complessità in diversi scenari di gioco.

## 🤖 Agenti Implementati

Sono stati sviluppati due tipi di agenti, che rappresentano due paradigmi differenti del Reinforcement Learning:

### 1. Agente Model-Based: Value Iteration
Questo agente utilizza l'algoritmo **Value Iteration** per calcolare una policy ottimale. Richiede una conoscenza a priori del modello dell'ambiente (un **Processo Decisionale di Markov - MDP**), ovvero le probabilità di transizione e le ricompense.
*   **Punti di Forza:** Converge rapidamente alla policy ottimale se il modello è accurato.
*   **Adattamenti Implementati:** Per gestire la natura non stazionaria dei fantasmi, sono state implementate tecniche di **aggiornamento dinamico delle ricompense** (es. "danger zones" e "ghostbuster mode").

### 2. Agente Model-Free: Q-Learning
Questo agente apprende direttamente dall'interazione con l'ambiente (per "trial and error") utilizzando l'algoritmo **Q-Learning**. Non necessita di un modello preesistente del gioco.
*   **Punti di Forza:** Estremamente adattabile ad ambienti le cui regole non sono note o cambiano dinamicamente.
*   **Varianti Implementate:** Include sia il Q-Learning tabellare che una versione con **Approximate Q-Learning** per gestire spazi degli stati più grandi.

## 📊 Analisi Sperimentale e Risultati

È stata condotta una rigorosa fase di testing per valutare l'impatto di iperparametri chiave sulle performance (misurate come **win rate** su 1000 episodi):
*   **Discount Factor (γ):** Analisi di come la visione a lungo termine dell'agente influenzi le strategie in mappe semplici (`smallGrid`) e complesse (`mediumClassic`).
*   **Safety Distance:** Valutazione dell'efficacia di mantenere una "distanza di sicurezza" dai fantasmi.
*   **Ghostbuster Mode:** Analisi dell'impatto strategico della caccia ai fantasmi quando le capsule energetiche sono attive.

I risultati, dettagliati nella relazione, mostrano i trade-off tra i due algoritmi e forniscono insight quantitativi per la configurazione ottimale degli agenti in diversi contesti.

## 🛠️ Stack Tecnologico

*   **Linguaggio:** Python
*   **Framework:** L'ambiente di test è basato sul framework del corso **Berkeley AI CS188**.
*   **Librerie Principali:**
    *   `numpy` per calcoli efficienti.
    *   `pandas` e `matplotlib` per l'analisi e la visualizzazione dei dati raccolti durante i test.

## 🚀 Esecuzione

Il codice è basato sul framework di Berkeley. Per eseguire un test, è possibile utilizzare i comandi forniti dal progetto originale. Ad esempio, per addestrare un agente Q-Learning:

```bash
python pacman.py -p PacmanQAgent -x 2000 -n 2010 -l smallGrid
