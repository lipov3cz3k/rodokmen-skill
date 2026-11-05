# Správa repozitáře rodokmen-skill

Vydání nové verze: zvedni číslo ve čtyřech místech najednou – `.claude-plugin/plugin.json` a
`.antigravity-plugin/plugin.json` (`version`), `skills/rodokmen/VERZE` (podle něj agent u uživatele pozná, že má aktualizovat projekt) a README na dvou místech – nahoře „Aktuální verze: X.Y.Z (vydána D. M. RRRR)“ a v požadavcích
„Stav k D. M. RRRR (verze X.Y.Z)“, vždy s číslem verze i datem vydání.
Do `CHANGELOG.md` přidej nahoru sekci `## X.Y.Z – D. M. RRRR` (Nové / Opravy / Návody, krátké odrážky pro uživatele,
čísla issues jako `#11`). Po commitu a pushi vytvoř tag a vydání na GitHubu s textem té sekce:
`awk '/^## X.Y.Z /{f=1;next} /^## /{f=0} f' CHANGELOG.md > /tmp/notes.md && gh release create vX.Y.Z --target main --title "X.Y.Z" --notes-file /tmp/notes.md`.
Mění-li se formát mezi `tools/` a `template/web/`, otestuj i aktualizaci projektu založeného předchozí verzí
(`novy_projekt.py` na stejnou složku, `npm install`, `npm run data`, `npm run build`).

Skill se vyvíjí a zkouší v Claude Code. Jde použít i v Codexu a OMP (Oh My Pi), které ho instalují ze stejného
`.claude-plugin/marketplace.json` – ten proto nepřesouvej. Když měníš pokyny vázané na aplikaci (nástroje, příkazy,
restart), uprav i stávající zmínky o Codexu a OMP, ať si neodporují. V Codexu ani OMP je ověřovat nemusíš.
Totéž platí pro Cursor (`reference/cursor.md`) a Antigravity (`reference/antigravity.md`, `.antigravity-plugin/plugin.json`).
Pokyny projektu jsou v `template/AGENTS.md`, `CLAUDE.md` (v repozitáři i v šabloně) je jen odkaz `@AGENTS.md`.
Hlídač sítě (`tools/hlidac_site.py`) umí vstup Claude Code i Antigravity – `tests/brzda/test_hlidac.py` zkouší obojí.
