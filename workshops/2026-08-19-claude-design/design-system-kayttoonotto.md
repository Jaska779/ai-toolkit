# DigiOne Design System — käyttöönotto suunnittelijalle

Tällä ohjeella saat DigiOnen design-systeemin käyttöösi Claude Designissa
(claude.ai/design): kaikki 100 komponenttia oikeasta digione-web-koodista,
teematokenit, brändilogot ja näkymäpatternit, joilla Claude generoi
DigiOne-näköisiä käyttöliittymiä.

## Esivaatimukset

- Pääsy GitLabiin (gitlab1.kuntien.fi) ja tähän repoon.
- Oma Claude-tilaus: **Pro, Max, Team tai Enterprise** (Claude Design ei
  sisälly Free-tasoon).
- **Claude Code** asennettuna (työpöytäsovellus tai CLI) ja kirjautuneena
  omalla claude.ai-tunnuksellasi.
- Git asennettuna.

Node- tai Yarn-asennuksia **ei tarvita** — design-systeemi on valmiiksi
buildattuna repossa (`ds-bundle/`). Työkaluja tarvitaan vasta jos bundlea
rakennetaan uudelleen (ks. `.design-sync/NOTES.md`).

## 1. Kloonaa repo

```bash
git clone https://gitlab1.kuntien.fi/digione/ui/digione-web.git
```

```bash
cd digione-web
```

## 2. Vaihda design-haaraan

Design-systeemi elää haarassa `claude-design-system`:

```bash
git switch claude-design-system
```

Tarkista että `ds-bundle/`- ja `.design-sync/`-kansiot näkyvät repon
juuressa — silloin olet oikeassa haarassa.

## 3. Tyhjennä projectId (`.design-sync/config.json`)

Tiedostossa `.design-sync/config.json` on avain `projectId`, joka osoittaa
alkuperäisen tekijän henkilökohtaiseen Claude Design -projektiin. Sinulla ei
ole siihen kirjoitusoikeutta, joten **poista arvo** ennen ensimmäistä
synkkausta:

```json
"projectId": "",
```

Synkkaus luo silloin oman projektin sinun tilillesi ja täyttää kenttään sen
id:n. **Älä committaa omaa projectId:täsi haaraan** — se on henkilökohtainen,
joten jätä muutos paikalliseksi.

## 4. Synkkaa design-systeemi omaan Claude Designiisi

1. Avaa Claude Code repon juurikansiossa.
2. Aja `/design-sync` (tai pyydä: *"Synkkaa tämä design-systeemi Claude
   Designiin"*).
3. Ensimmäisellä kerralla Claude pyytää luvat: design-oikeudet
   claude.ai-kirjautumiseesi, uuden projektin luonti ja tiedostojen lataus.
   Hyväksy ne.
4. Synkkaus lataa valmiin `ds-bundle/`-paketin projektiisi. Mitään ei
   buildata koneellasi.

Kun synkkaus on valmis, avaa **claude.ai/design** — projektissa näkyvät
komponenttikortit ryhmittäin, ja voit pyytää Claudea rakentamaan näkymiä
DigiOnen komponenteilla ja tokeneilla. Käyttöidiomit (tokenit, DsProvider,
patternit) ovat tiedostossa `ds-bundle/README.md` ja
`ds-bundle/guidelines/`-kansiossa — Claude lukee ne projektista itse.

## Päivitysten hakeminen

Kun design-systeemi päivittyy repoon:

```bash
git pull
```

Aja sen jälkeen `/design-sync` uudelleen Claude Codessa — se päivittää vain
muuttuneet tiedostot omaan projektiisi (projectId on tallessa paikallisessa
`config.json`-muutoksessasi).

## Polku Tieran julkaistuksi design-systeemiksi

Nykymallissa jokaisella suunnittelijalla on **oma kopio** omalla
Claude-tilillään, ja totuuslähde on tämä repo. Claude Design -projektin voi
jakaa linkillä (katselu / kommentointi / muokkaus) vain **saman Team- tai
Enterprise-organisaation sisällä** — eri tilausten välillä jakoa ei ole.
Yhteinen, julkaistu design-systeemi syntyy näin:

1. **Tiera hankkii Team- tai Enterprise-tilauksen** ja ottaa Claude Designin
   käyttöön organisaatiossa ([admin-ohje](https://support.claude.com/en/articles/14604406-claude-design-admin-guide-for-team-and-enterprise-plans)).
2. **Suunnittelijat liitetään organisaatioon.** Henkilökohtaisen tilin
   sisällön voi migroida organisaatioon kertaluontoisesti, mutta helpompaa on
   synkata design-systeemi reposta puhtaana organisaation projektiksi.
3. **Nimetty omistaja synkkaa DS:n organisaation projektiksi** tästä reposta
   (sama `/design-sync`-työnkulku, projekti luodaan organisaatiotilille).
4. **Projekti jaetaan linkillä** organisaation suunnittelijoille sopivin
   oikeuksin. Huomio: usean henkilön yhtäaikainen muokkaus on vielä
   beta-vaiheessa, joten muokkaukset kannattaa keskittää omistajalle.
5. **Ylläpito:** totuuslähde pysyy GitLabissa. Komponentti- ja
   teemamuutokset tehdään repoon (tavallisena MR:nä), ja omistaja ajaa
   re-syncin organisaation projektiin. Ohjeet ylläpitäjälle:
   `.design-sync/NOTES.md`.

Lisätietoa: [Get started with Claude Design](https://support.claude.com/en/articles/14604416-get-started-with-claude-design)
