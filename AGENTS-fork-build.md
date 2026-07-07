Toto je fork projektu, ktery oproti main branch rozsiruje puvodni funkcionalitu o featury v nasledujich branchich:

- feat/creation_relative
- feat/target_date_offset
- feat/progress_offset
- feat/progress_colors
- feat/stroke0

Cilem je vytvorit finalni build do branche "fork-build", ktery bude obsahovat vsechny vyse uvedene featury a bude pripravena k nasazeni.

Upstream repozitar (puvodni projekt, ze ktereho je toto fork): https://github.com/Rishi8078/TimeFlow-Card.git
Origin repozitar (tento fork): git@github.com:ma-zal/TimeFlow-Card.git

Postup buildu:
1. Aktualizovat 'main' branch z upstream repozitare (git fetch upstream + merge do main), push na origin/main.
2. Pro kazdou feature branch (creation_relative, target_date_offset, progress_offset, progress_colors, stroke0):
    - Pokud branch neexistuje lokalne, vytvorit ji z origin/feat/<nazev>.
    - Provest merge z 'main' do feature branch.
    - Resit pripadne konflikty.
    - Poznamka: Pouze merges, zadne rebase.
    - Push aktualizovane feature branch zpet na origin.
3. Vytvor branch 'fork-build-<date YYMMDD>' z aktualniho stavu 'main'. Pokud uz existuje (lokalne nebo na originu), smaz ji a zacni znovu.
4. Pro kazdou feature branch (v poradi jako v seznamu vyse):
    - Provest merge z feature branch do 'fork-build'.
    - Resit pripadne konflikty - ale nemeli by nastat
5. Spust "npm run build" pro vytvoreni finalniho buildu, vysledny build (dist) commitnout do 'fork-build'.
6. Push 'fork-build' na origin (pripadne force push, pokud byla branch znovu vytvorena).

Poznamka: branch "next" je samostatna, drivejsi/manualni integracni branch a tímto postupem se nijak nepouziva ani nemeni.

