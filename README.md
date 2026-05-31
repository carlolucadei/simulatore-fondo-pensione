# 🏦 Simulatore Fondo Pensione – Risparmio Fiscale IRPEF 2026

Uno strumento web **gratuito, open source e completamente offline** per stimare il risparmio fiscale IRPEF derivante dal versamento volontario a un fondo pensione complementare, secondo le aliquote italiane 2026.

---

## ✨ Funzionalità

- Calcolo IRPEF per scaglioni (23% / 33% / 43%) applicato a due scenari: con e senza fondo pensione
- Deduzione automatica del contributo volontario con applicazione del limite massimo annuo
- Supporto al contributo datoriale (in percentuale sulla RAL o importo fisso)
- Tabella comparativa con dettaglio per scaglione
- Riepilogo qualitativo in linguaggio semplice, generato dinamicamente
- Validazione degli input con messaggi chiari
- Tutto in un **singolo file HTML** — zero dipendenze esterne, funziona aprendo il file nel browser

---

## 🚀 Come usarlo

### Opzione 1 – Direttamente nel browser

1. Scarica il file `simulatore-fondo-pensione.html`
2. Aprilo con qualsiasi browser moderno (Chrome, Firefox, Safari, Edge)
3. Compila i campi e leggi i risultati in tempo reale

### Opzione 2 – GitHub Pages

Se vuoi pubblicarlo come sito, basta attivare **GitHub Pages** sulla root del repository e puntare a `simulatore-fondo-pensione.html` come pagina principale (oppure rinominarlo in `index.html`).

---

## 📋 Input richiesti

| Campo | Descrizione |
|---|---|
| RAL annuale | Reddito Annuo Lordo in euro |
| Contributo volontario % | Percentuale della RAL da versare al fondo |
| Contributo datoriale | Opzionale: importo fisso o percentuale versata dal datore di lavoro |

---

## 📊 Output calcolati

- IRPEF stimata nei due scenari (senza / con fondo pensione)
- Dettaglio dell'imposta per ciascuno scaglione IRPEF
- Risparmio fiscale annuo
- Costo netto effettivo del contributo (versato meno risparmio)
- Totale annuo versato nel fondo (lavoratore + datore)
- Beneficio economico complessivo stimato

---

## ⚙️ Struttura del codice

Il file è organizzato in funzioni pure e ben separate, facilmente modificabili:

```
calcolaIRPEF()              → calcolo imposta per scaglioni
calcolaContributoLavoratore() → contributo annuo dalla percentuale
calcolaQuotaDeducibile()    → applicazione del limite di deducibilità
calcolaDatoriale()          → contributo del datore di lavoro
scenarioSenzaFondo()        → scenario base
scenarioConFondo()          → scenario con deduzione
renderTabella()             → tabella comparativa
renderScaglioni()           → dettaglio scaglioni IRPEF
renderSummary()             → riepilogo qualitativo testuale
renderKPI()                 → aggiornamento valori in evidenza
valida()                    → validazione input
```

Le costanti fiscali (aliquote, soglie, limite di deducibilità) sono tutte definite in cima al file JavaScript in una struttura facilmente aggiornabile:

```javascript
const IRPEF_SCAGLIONI = [
  { min: 0,     max: 28000,    aliquota: 0.23, label: '23%  (fino a 28.000 €)' },
  { min: 28000, max: 50000,    aliquota: 0.33, label: '33%  (28.001 – 50.000 €)' },
  { min: 50000, max: Infinity, aliquota: 0.43, label: '43%  (oltre 50.000 €)' },
];

const LIMITE_DEDUCIBILITA = 5300.00; // euro
```

---

## ⚠️ Disclaimer

> **Questo strumento è fornito esclusivamente a scopo informativo e didattico.**

Il simulatore fornisce una **stima semplificata** basata sulle aliquote IRPEF 2026 e **non sostituisce in alcun modo una consulenza fiscale o previdenziale professionale**.

Il calcolo **non considera**:
- addizionali regionali e comunali IRPEF
- detrazioni da lavoro dipendente o per carichi familiari
- contributi previdenziali INPS
- TFR (Trattamento di Fine Rapporto)
- altre deduzioni (es. contributi sanitari, previdenza obbligatoria)
- situazioni reddituali complesse o redditi diversi dalla RAL dipendente

Per una valutazione accurata della tua situazione fiscale e previdenziale, **rivolgiti a un commercialista, un consulente del lavoro o un consulente finanziario abilitato.**

---

## 🏛️ Riferimenti ufficiali

Per informazioni ufficiali sulla previdenza complementare in Italia:

- **COVIP** – Commissione di Vigilanza sui Fondi Pensione  
  🔗 [https://www.covip.it](https://www.covip.it)  
  La COVIP è l'autorità di riferimento per dubbi, chiarimenti e normativa sui fondi pensione complementari.

- **Normativa fiscale di riferimento**: D.Lgs. 252/2005 (disciplina delle forme pensionistiche complementari) e TUIR art. 10 (deduzioni dal reddito complessivo)

---

## 📄 Licenza

```
MIT License

MIT License

Copyright (c) 2026 carlolucadei

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

Licenza MIT: puoi usare, copiare, modificare, distribuire e pubblicare questo codice liberamente, anche per scopi commerciali, senza chiedere permesso. L'unica condizione è mantenere il testo della licenza nelle copie distribuite.

**Contributi benvenuti** — apri una pull request, segnala un bug o proponi nuove funzionalità. Questo strumento esiste per essere migliorato dalla comunità.

---

## 🤝 Come contribuire

1. Fai un fork del repository
2. Crea un branch (`git checkout -b feature/nome-funzionalita`)
3. Effettua le modifiche al file HTML
4. Apri una Pull Request con una descrizione delle modifiche

Idee di miglioramento benvenute: addizionali regionali/comunali, simulazione pluriennale, export PDF, supporto ai PIP (Piani Individuali Pensionistici), confronto tra diversi fondi.

---

*Simulatore non ufficiale — aggiornato alle aliquote IRPEF 2026 — dati a solo scopo indicativo*
