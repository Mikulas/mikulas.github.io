---
layout: post
title:  "Cronner jako generátor crontab.d"
date:   2014-10-06 00:00:00
categories: nette crontab cronner
---

Štěkyho Cronner mě nadchnul a vidím v něm výhody, nicméně hlavně u hostingů které mají špatně nastavitelný cron. Napadlo mě ale další řešení.

Co v prezentaci na Poslední sobotě nezaznělo je, že je dobré informaci o cronech verzovat – to přesně cronner řeší. Osobně nemám problém crontab nastavit a asi bych nepřekousnul, že bych musel každou minutu volat cron manager v php, který by jenom občas něco zavolal. Takže mě napadlo verzovat nastavení crontabu. Co vím tak úplně každý linux má `/etc/cron.d/`, kam se dají nahrávat soubory ve stejném formátu jako v crontab. Řešení je tedy nasnadě: verzujte v repu aplikace nějakou vlastní cron definici a udělejte si symlink do `/etc/cron.d/` (případně to nechte dělat deploy nástroj).

Další možností je nástroj, který by z cronner annotací vygeneroval crontab (což by mělo jít vždy). To bych asi nevyužil, ale dává to dohromady výmluvnost cronneru a výkon crontabu.

![Diagram](/assets/cronner-venn.svg)

Ještě ale nemáme to ultimátní řešení které by uspokojilo všechny.
