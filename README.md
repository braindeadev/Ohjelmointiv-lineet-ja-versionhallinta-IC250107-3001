# Ohjelmointiv-lineet-ja-versionhallinta-IC250107-3001
Kurssin "Ohjelmointivälineet ja versionhallinta IC250107-3001" lopputyö


clonasin ensin repositorioni komennolla:

$ git clone git@github.com:braindeadev/Ohjelmointiv-lineet-ja-versionhallinta-IC250107-3001.git


sittein lisäsin ylläolevan tekstin "README.md" tiedostoon ja puskin sen kittin
käytin kommentoja 

"git status" jolla katsoin committini statuksen
"git add *" jolla lisäsin kaikki lisäsin trackaamattömät tiedostot committiin
"git commit -m "*kommentti*" jolla committasin tiedostot ja m- jälkeen hakamerkkien sisään kommentin jolla erottaa mitä commit on tehnyt
"git puhs" jolla lpuksi puskinn committini githubiin


toistin tämän 6 kertaa jossa loin uuden tekstitiedoston ja tein siihen muutoksia lisäämällä ja poistamalla tekstiä
tällä kertaa kuitenkin käytin "git add "teidoston nimi" koska muokkasin vain "tekti.txt" tiedostoa

loin kaksi uutta branchia "tekstitiedoston_paivittaminen" ja "uusi_tekstitiedosto" komennoilla
git checkout -b tekstitiedoston_paivittaminen
git checkout -b uusi_tekstitiedosto


"tekstitiedoston_paivittaminen" branchissä lisäsin uutta teksiä "tekti.txt" tiedostoon 
ja "uusi_tekstitiedosto" branchissä loin uuden tiedoston "branch_uusi_tiedosto.txt"

molemmissa brancheissä committasin muutokset git commit -m "kommentti" komennolla jonka jälkeen mergesin molemmat branhit mainiin komennoilla

git merge feature1 -m "Yhdistetään tekstitiedoston_paivittaminen
git merge feature2 -m "Yhdistetään uusi_tekstitiedosto

siten siirryin itse mainiin komennolla
git checkout main

ja puskin branchien muutokset komennolla
git push


