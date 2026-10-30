# Quotient shared average

When you install [Quotient](https://github.com/Korvonordico/quotient-claude-tokens), it doesn't know yet how your estimates compare with what your jobs really cost. It learns that from your own jobs, but at the start you have none. This repository fills that gap. It holds one small file, [`average.json`](average.json), with what jobs cost for other Quotient users compared with what was estimated.

## How it works

1. You finish a job. If sharing is on (it is by default, and you can turn it off), Quotient sends one line of numbers: the model family, the estimate, the real cost, and your Quotient version. Rounded, with no date, no text, no file names, no id.
2. The shared-average service collects these lines and, once a week, writes the new average here.
3. Every copy of Quotient downloads this file once a day.

## Divided by model

Opus, Sonnet, Haiku and the other models don't cost the same, so one single average would mislead. Quotient recognizes the model you use and sends your numbers to its family. When it needs a starting point, it takes the average of the same family. If that family isn't published yet, it takes the average of all jobs together. A family appears here by itself once it has enough jobs.

As soon as you have 5 jobs of your own, Quotient uses your numbers and no longer this average.

## What's in the file

For each model family, and for all jobs together:

- `jobs`: how many jobs the average comes from;
- `factor`: how much jobs really cost compared with the estimate (the median). For example, 1.18 means about 18% more than estimated;
- `p25` and `p75`: the range where half the jobs fall.

## Privacy rules

- A family is published only after at least 30 jobs, and the file changes at most once a week and only after at least 20 new jobs. That way nobody watching it can pick out a single job.
- Anyone can send numbers, so the average could be pushed off on purpose. To limit that, odd values are dropped and Quotient accepts the average only between x0.25 and x4.
- The service's key can write only in this repository, never in Quotient's code.

Full details: [PRIVACY.md](https://github.com/Korvonordico/quotient-claude-tokens/blob/main/PRIVACY.md). Live page: https://quotient-share.korvonordico.workers.dev

## Right now

The average still comes almost entirely from my own jobs, all on Opus. It will become a real shared average as more people use Quotient. If you do, leaving sharing on helps whoever comes next.

---

**In italiano.** Questo progetto contiene un solo file, `average.json`: la media di quanto sono costati davvero i lavori degli utenti di Quotient rispetto alla stima. Serve a chi installa Quotient da zero, finché non ha 5 lavori suoi. La media è divisa per modello (Opus, Sonnet e gli altri). Se il tuo modello non c'è ancora, si usa la media di tutti. Una famiglia compare da sola quando ha almeno 30 lavori. Si mandano solo numeri arrotondati: niente date, testi, nomi o identificativi. Per ora la media viene quasi tutta dai miei lavori su Opus.
