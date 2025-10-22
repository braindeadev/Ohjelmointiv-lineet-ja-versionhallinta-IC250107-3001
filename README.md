# Ohjelmointivälineet-ja-versionhallinta-IC250107-3001
Kurssin "Ohjelmointivälineet ja versionhallinta IC250107-3001" lopputyö

2.
Clonasin ensin repositorioni käyttäen SSH-yhteyttä komennolla:

```bash
git clone git@github.com:braindeadev/Ohjelmointiv-lineet-ja-versionhallinta-IC250107-3001.git
```

3.
Sitten lisäsin ylläolevan tekstin "README.md" tiedostoon ja puskin sen GitHubiin. Käytin kommentteja:

```bash
git status        # Katsoin committini statuksen
git add *         # Lisäsin kaikki trackaamattomat tiedostot committiin
git commit -m "kommentti"  # Tein commitin ja lisäsin kommentin
git push          # Puskin commitit GitHubiin
```

4.
Toistin tämän 6 kertaa luoden uusia tekstitiedostoja ja muokaten niitä. Tällä kertaa käytin:

```bash
git add *         # Lisäsin kaikki trackaamattomat tiedostot committiin
```
sijaan komentoa
```bash
git add tekti.txt	#Lisäämällä komennon perään tiedoston nimen committaan vain tietyn tiedoston onkä kaikkia jos lisäisin "*" loppuun
```

5.
Loin kaksi uutta branchia komennoilla:

```bash
git checkout -b tekstitiedoston_paivittaminen
git checkout -b uusi_tekstitiedosto
```

- "tekstitiedoston_paivittaminen" branchissä lisäsin uutta tekstiä "teksti.txt" tiedostoon
- "uusi_tekstitiedosto" branchissä loin uuden tiedoston "branch_uusi_tiedosto.txt"

Molemmissa brancheissä committasin muutokset:

```bash
git commit -m komentti(riippuan mitä commitissa lisätään/poistetaan)
```

Mergesin molemmat branchit mainiin:

```bash
git checkout main
git merge tekstitiedoston_paivittaminen -m "Yhdistetään tekstitiedoston_paivittaminen"
git merge uusi_tekstitiedosto -m "Yhdistetään uusi_tekstitiedosto"
git push
```

6.
Tein merge konfliktin seuraavasti: ensin muokkasin "branch_uusi_tiedosto.txt" tiedostoa mainissa ja committasin muutokset. Sitten loin "merge_error" branchin, tein "branch_uusi_tiedosto.txt" tiedostoon muutoksia ja committasin ne. Kun yritin mergetä branchin mainiin, sain merge-konfliktin:

```text
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Korjasin merge-konfliktin Visual Studiolla käyttämällä "Accept Both Changes" valintaa. Nyt molemmat muutokset näkyvät "branch_uusi_tiedosto.txt" tiedostossa allekkain.

Lopuksi committasin korjatun tiedoston ja puskin sen GitHubiin. Näin merge error korjattiin.

7.
Tein "vahingossa" muutoksia mainiin, jotka piti tehdä toiseen branchiin. Käytin git stash ominaisuutta ominaisuuden "siirtämiseksi" uuteen branchiin:

```bash
git stash	#varastoi uuden ominaisuuden talteen
git checkout -b stash	# tei ominaisuudelle uuden branchin "stash" joka näin jälkikäteen todeten ei ole kauhean hyvä nimi branchille.
git stash pop	#varastoitu ominaisuus palautetaan säilöstä sen hetkiselle branchille.
```


8.
Tein commitin mainiin nimellä "revertattava commit", jonka sitten revertasin komennolla:

```bash
git revert HEAD	#tekee uuden kommitin jossa "poistuu" viimeisin commit
```

Koska revertattava commit oli viimeisin, tämä peruutti sen helposti.

9.
Hain commitin toisesta branchista mainiin komennolla:

```bash
git cherry-pick 75bffbe #tämä commit(75bffbe) on sama commit missä "siirsin" ominausuuden mainista uuteen branchiin ja nyt sama teksi on uudestaan manissa
```

10.
Lisäsin repoon tagin komennoilla:

```bash
git tag v1.0.0	#loin uuden tagin
git push origin v1.0.0	#puskin sen gittiin
```

11.
Loin komennolla `.gitignore` tiedoston ja lisäsin siihen .env tiedostot:
Aluksi olin unohtanut lisätä "*" .env eteen jonka takia .gitignore ei toiminut!:

```bash
touch .gitignore	#luo ".gitignore" tiedoston nykyiseen hakemistoon
```

.gitignore sisältö:
```
*.env
```
Tämä poistaa kaikki `.env` loppuiset tiedostot seurannasta.:

12.
Siirryin yksitellen brancheiileni ja suoritin komennon:

```bash
git rebase main #mergeää branchin "mainin eteen" ja tekee commit historiasta lineaarisen
```

- "uusi_tekstitiedosto" haarassa rebase onnistui ongelmitta  
- "tekstitiedoston_paivittaminen" haarassa tuli aluksi merge error, joka johtui vanhasta stashista. Droppasin stashin joka korjasi merge errorin jonka jälkeen rebase onnistui.


13.

Lopuksi puskin molemmat branchit GitHubiin:

```bash
git push origin tekstitiedoston_paivittaminen
git push origin uusi_tekstitiedosto
```

- "tekstitiedoston_paivittaminen" branch oli jo identtinen mainin kanssa, joten mergeä ei tarvittu  
- "uusi_tekstitiedosto" branchissa tein pull requestin, tarkistin muutokset ja merge onnistui GitHubissa painamalla "merge pull request".
