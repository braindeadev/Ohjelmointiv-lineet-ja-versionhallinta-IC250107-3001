# Ohjelmointiv-lineet-ja-versionhallinta-IC250107-3001

Kurssin "Ohjelmointivälineet ja versionhallinta IC250107-3001" lopputyö

Clonasin ensin repositorioni komennolla:

```bash
git clone git@github.com:braindeadev/Ohjelmointiv-lineet-ja-versionhallinta-IC250107-3001.git
```

Sitten lisäsin ylläolevan tekstin "README.md" tiedostoon ja puskin sen GitHubiin. Käytin kommentteja:

```bash
git status        # Katsoin committini statuksen
git add *         # Lisäsin kaikki trackaamattomat tiedostot committiin
git commit -m "kommentti"  # Tein commitin ja lisäsin kommentin
git push          # Puskin commitit GitHubiin
```

Toistin tämän 6 kertaa luoden uusia tekstitiedostoja ja muokaten niitä. Tällä kertaa käytin:

```bash
git add "tiedoston_nimi"
```

koska muokkasin vain "teksti.txt" tiedostoa.

Loin kaksi uutta branchia:

```bash
git checkout -b tekstitiedoston_paivittaminen
git checkout -b uusi_tekstitiedosto
```

- "tekstitiedoston_paivittaminen" branchissä lisäsin uutta tekstiä "teksti.txt" tiedostoon
- "uusi_tekstitiedosto" branchissä loin uuden tiedoston "branch_uusi_tiedosto.txt"

Molemmissa brancheissä committasin muutokset:

```bash
git commit -m "kommentti"
```

Mergesin molemmat branchit mainiin:

```bash
git merge feature1 -m "Yhdistetään tekstitiedoston_paivittaminen"
git merge feature2 -m "Yhdistetään uusi_tekstitiedosto"
git checkout main
git push
```

Tein merge errorin seuraavasti: ensin muokkasin "branch_uusi_tiedosto.txt" tiedostoa mainissa ja committasin muutokset. Sitten loin "merge_error" branchin, tein samoihin kohtiin muutoksia ja committasin ne. Kun yritin mergetä branchin mainiin, sain merge-konfliktin:

```text
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Korjasin merge-konfliktin Visual Studiolla käyttämällä "Accept Both Changes". Commitoin muutokset ja puskin ne GitHubiin. Nyt molemmat muutokset näkyvät "branch_uusi_tiedosto.txt" tiedostossa allekkain.

Lopuksi committasin korjatun tiedoston ja puskin sen GitHubiin. Näin merge error korjattiin.

Tein vahingossa muutoksia mainiin, jotka piti tehdä toiseen branchiin. Käytin:

```bash
git stash
git checkout -b stash
git stash pop
```

jolloin tallessa oleva muutos siirtyi uuteen branchiin.

Tein commitin mainiin nimellä "revertattava commit", jonka sitten revertasin:

```bash
git revert HEAD
```

Koska se oli viimeisin commit, tämä peruutti sen helposti.

Hain commitin toisesta branchista mainiin:

```bash
git cherry-pick 75bffbe
```

Lisäsin repoon tagin:

```bash
git tag v1.0.0
git push origin v1.0.0
```

Loin `.gitignore` tiedoston ja lisäsin siihen:

```bash
touch .gitignore
```

```
*.env
```

Tämä poistaa kaikki `.env` loppuiset tiedostot seurannasta.

Siirryin feature-haaroille ja tein rebasen mainiin:

```bash
git rebase main
```

- "uusi_tekstitiedosto" haarassa rebase onnistui ongelmitta  
- "tekstitiedoston_paivittaminen" haarassa tuli aluksi merge error, joka johtui vanhasta stashista. Droppasin shasin, korjasin merge errorin ja rebase onnistui.

Lopuksi puskin molemmat branchit GitHubiin:

```bash
git push origin "branchin_nimi"
```

- "tekstitiedoston_paivittaminen" branch oli identtinen mainin kanssa, joten mergeä ei tarvittu  
- "uusi_tekstitiedosto" branchissa tein pull requestin, tarkistin muutokset ja mergein onnistui GitHubissa painamalla "merge pull request".
