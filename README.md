# Quotient shared average

This repository holds one file, [`average.json`](average.json): the shared average that every copy of [Quotient](https://github.com/Korvonordico/quotient-claude-tokens) downloads once a day, so that new users start from real numbers instead of from zero.

- **Who writes it:** the shared-average service ([code](https://github.com/Korvonordico/quotient-claude-tokens/tree/main/server)), at most once a week, only after at least 20 new jobs and never below 30 jobs, so that someone watching this file cannot tell a single job apart.
- **What is in it:** for each model family and for all jobs together, how many jobs, and the median of real cost / raw estimate with its middle half, rounded to 2 decimals. It is a best-effort average: anyone can send numbers, and Quotient uses it only between x0.25 and x4. Numbers only: no dates of jobs, no names, no ids.
- **Why a separate repository:** the service's key can write only here, never in Quotient's code.

What is collected and how: [PRIVACY.md](https://github.com/Korvonordico/quotient-claude-tokens/blob/main/PRIVACY.md). Live page: https://quotient-share.korvonordico.workers.dev

---

*In italiano:* questo progetto contiene solo `average.json`, la media condivisa che ogni copia di Quotient scarica una volta al giorno. La scrive il servizio della media, al massimo una volta a settimana, solo dopo almeno 20 lavori nuovi e mai sotto i 30. Solo numeri. È separato dal progetto di Quotient perché la chiave del servizio possa scrivere solo qui, mai nel programma.
