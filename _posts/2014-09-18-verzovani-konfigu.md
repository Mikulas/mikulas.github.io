---
layout: post
title:  "Verzování konfigu"
date:   2014-09-18 00:00:00
categories: nette config
---
Při spolupráci s více lidmi často narážím na to, že někdo si upraví lokální konfiguraci a aplikace bez těch správných klíčů ostatním nefunguje. V lepším případě na to upozorní dobrá commit message, v tom horším se to programátor dozví z laděnky někdy v polovině rozběhnuté aplikace a špatně se to debuguje.

Na většině projektů co se podílím jsem nasadil verzované lokální konfigurace. Nemyslím tím že tenhle config přidávám do VCS (chraň bůh, jsou tam hesla atp.) ale v `config.local.sample.neon` i v `config.local.neon` máme klíč `version: [1]`. Pokud se do sample konfigurace udělá bc break, zvýší se version o jedna. Hned při dalším kompilaci konfigurace proběhne kontrola, že verze obou konfigurací jsou stejné – pokud nejsou, zobrazí se tahle krásná výjimka:

![Ukázka výjimky při různých verzích](/assets/bluecreen-e1410986720585-1024x854.png)

Tohle celé je implementováno v rozšíření, které jsem pod Clevisem publikoval zde: https://github.com/Clevis/config-version-extension

Přidání do projektu je na tři řádky. Performance hit je prakticky nulový.

```yml
# config.neon
extensions:
    version: Clevis\Version\DI\VersionExtension
```

```yml
# config.local.neon
# config.local.sample.neon
version: [1]
```

Mimochodem, protože se jako neon parsuje i `config.local.sample.neon` tak je rovnou kontrolováno, že je v tom souboru opravu validní neon. Říkám že je to feature tohohle rozšíření, protože se tomu nejde vyhnout – šlo by parsovat tu version regexem, ale to není to pravé ořechové.

Další řešení je mít git hook, který upozorní pokud se změní `config.local.sample.neon`. Tuším, že na tohle by šel použít post-checkout.
