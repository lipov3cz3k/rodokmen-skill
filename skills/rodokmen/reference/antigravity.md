# Antigravity

Skill funguje v Antigravity stejně jako v Claude Code. Tady je jen to, čím se liší instalace, hlídač sítě a prohlížeč.
Zbytek návodu (fáze, matriky, web) platí beze změny. Zatím to nikdo nevyzkoušel na celém rodokmenu.

V příkazové řádce se skill nainstaluje jako plugin: `agy plugin install https://github.com/sarsonj/rodokmen-skill`
(manifest `.antigravity-plugin/plugin.json`). V aplikaci a editoru patří osobní skill do
`~/.gemini/config/skills/rodokmen/` (editor čte i starší `~/.gemini/antigravity/skills/`). Ve složce musí ležet
`SKILL.md`. Nejsnáz je repozitář naklonovat a na složku `skills/rodokmen` udělat odkaz – aktualizace je pak `git pull`.

Skill uživatel vyvolá `/rodokmen` nebo spouštěcí větou z `SKILL.md`. Složka skillu (`SKILL_DIR`) je složka souboru
`SKILL.md`, který jsi otevřel.

`AGENTS.md` v projektu Antigravity načte sám (pravidla workspace).

**Hlídač sítě:** `novy_projekt.py --hlidac` ho zapíše i do `.agents/hooks.json` projektu (hook `PreToolUse`
na `run_command`), `--bez-hlidace` ho odtud zase odebere. Zeptá-li se Antigravity, jestli hookům projektu důvěřovat,
vysvětli uživateli, že jde o tento hlídač. Zákaz `curl`/`wget` z `.claude/settings.json` tu neplatí, zamítá ho až hlídač.

Antigravity umí spouštět příkazy bez ptaní (automatické spouštění v nastavení). Začátečníkovi doporuč schvalování
příkazů; hlídač funguje v obou režimech.

Prohlížeč: vestavěný prohlížečový agent. Pravidla pro prohlížeč v `SKILL.md` (pauzy mezi stránkami, konec při
403/429/503) platí stejně. Postupy v `portaly.md` jsou vyzkoušené s Playwrightem – když snímek neuložíš do souboru,
ať ho uživatel uloží sám (snímek obrazovky).

Náhled webu: `.claude/launch.json` tu nic nespustí. Ve složce `web` spusť `npm run nahled` a pošli odkaz
http://localhost:4321 (bez `--host`).

Model: postupy jsou vyladěné na Claude. S jiným modelem ověřuj čtení přes `tools/overit.py` o to pečlivěji
a nejistá místa řekni uživateli.
