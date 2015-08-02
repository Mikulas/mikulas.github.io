---
layout: post
title:  "Adminer – composer package"
date:   2014-10-11 00:00:00
categories: adminer composer
redirect_from:
  - /adminer-package/index.html
---

[Adminer](http://www.adminer.org/) nemá oficiální composer balíček. Jsou tady různá řešení: většina vývojářů si vystačí s tím, že jednou Adminer [natvrdo do aplikace nakopírují](https://github.com/search?utf8=%E2%9C%93&q=adminer+in%3Apath&type=Code&ref=searchresults) a možná ho jednou za čas updatují novou minor verzí. O něco hezčí přístup je [Pavlův instalační balíček](https://github.com/foglcz/adminer-installer), který sice přes composer nainstalujete, ale nedá se tím Adminer verzovat. O něco šťastnější řešení je [Davidův adminer-custom](https://github.com/dg/adminer-custom), který ale obsahuje navíc nějaké kravinky o které nestojím a jeho verze neodpovídají verzím Admineru.

Před měsícem jsem si připravil daemona, který přes GitHub api kontroluje nové verze Admineru a ze SourceForge stáhuje všechny buildy pro konkrétní verzi (od `myslq-cs` po `editor-pl`): [github.com/Mikulas/adminer-package](https://github.com/Mikulas/adminer-package). Tagy samozřejmě odpovídají konkrétním verzím Admineru. Nový package by se měl objevit max do pár minut od založení nového tagu v Adminer repu.

To že v balíčku jsou všechny buildy mě netrápí – nejsou v autoload a jenom si vyberu (symlinkem) ten který chci použít. Kdyby to pro někoho byl problém, můžete si napsat triviální composer update update script který vám smaže všechny buildy co nechcete.
