# Prompt: Luo projektin agenttiohjeet

Luo nykyisen projektikansion juureen tiedostot `AGENTS.md` ja `CLAUDE.md`, jotka ohjaavat tekoälyagenttien toimintaa tässä projektissa.

## Tavoite

Muodosta selkeä ja käytännöllinen toimintamalli projektin materiaalien käsittelyyn, UX-dokumentaation ylläpitämiseen ja prototyyppien hyödyntämiseen.

Ohjeiden perusteella agentin pitää ymmärtää:

- mitä kukin projektikansio sisältää
- mitä tiedostoja saa muokata
- milloin dokumentaatiota pitää päivittää
- miten materiaalista johdetut havainnot dokumentoidaan
- miten lähteet, epävarmuudet ja avoimet kysymykset merkitään
- milloin työ katsotaan valmiiksi

## Ennen tiedostojen luomista

1. Tutki nykyinen kansiorakenne ja olemassa olevat tiedostot.
2. Tarkista, onko projektissa jo agenttiohjeita, dokumentointikäytäntöjä tai YAML-frontmatter-rakennetta.
3. Hyödynnä olemassa olevia käytäntöjä ja vältä ristiriitaisten ohjeiden luomista.
4. Älä muuta muita projektin tiedostoja tämän tehtävän yhteydessä.
5. Jos `AGENTS.md` tai `CLAUDE.md` on jo olemassa, säilytä niiden hyödyllinen projektikohtainen sisältö ja täydennä sitä. Älä korvaa sisältöä sokkona.

## Ohjetiedostojen suhde

- Tee `AGENTS.md`-tiedostosta työkaluriippumaton pääohje ja projektin ensisijainen agenttiohjeistus.
- Tee `CLAUDE.md`-tiedostosta Claude Codea koskeva ohje, joka viittaa ensisijaiseen `AGENTS.md`-tiedostoon ja sisältää vain mahdolliset Claude-kohtaiset lisäohjeet.
- Vältä saman ohjeistuksen tarpeetonta ylläpitämistä kahdessa paikassa.
- Käytä `CLAUDE.md`-tiedostossa viittausta `@AGENTS.md`, jotta yhteiset ohjeet ovat Claude Coden käytettävissä.
- Jos luotettava tiedostojen välinen viittaus ei ole käytettävissä, sisällytä molempiin tiedostoihin tärkeimmät säännöt ja kerro, että ohjeet on pidettävä keskenään yhdenmukaisina.

## Projektin kansiorakenne

### `Materiaalit/`

Kansioon tallennetaan projektissa ja työpajoissa syntyvät materiaalit sekä asiakkaan toimittamat lähdeaineistot, kuten:

- PDF- ja Word-dokumentit
- Excel- ja CSV-tiedostot
- esitykset
- haastattelu- ja työpajatranskriptit
- muistiinpanot
- kuvat ja muut projektin lähdeaineistot

Määritä ohjeisiin seuraavat toimintaperiaatteet:

- Materiaalit ovat lähdeaineistoa. Alkuperäisiä tiedostoja ei saa poistaa, siirtää, nimetä uudelleen tai muokata ilman käyttäjän lupaa.
- Relevantin työskentelysession alussa agentti tarkistaa, onko kansioon lisätty uusia tai muuttuneita materiaaleja.
- Agentin ei tarvitse analysoida kaikkea aineistoa uudelleen jokaisella kerralla. Sen tulee ensisijaisesti käsitellä uudet, muuttuneet tai tehtävän kannalta olennaiset tiedostot.
- Materiaaleista tunnistetut havainnot, tarpeet ja päätelmät viedään `UX-dokumentaatio/`-kansion dokumentteihin.
- Havainnoista pitää käydä ilmi niiden lähde. Agentti ei saa esittää oletuksia tai omia tulkintojaan vahvistettuina käyttäjätietoina.
- Ristiriitaiset, epävarmat tai vanhentuneilta vaikuttavat tiedot merkitään selkeästi tarkistettaviksi.

### `UX-dokumentaatio/`

Kansio toimii projektin ensisijaisena UX- ja palvelumuotoilutiedon lähteenä sekä agenttien käyttämänä projektiwikinä.

Dokumentaatio tallennetaan Markdown-tiedostoina. Dokumentit indeksoidaan, linkitetään toisiinsa ja varustetaan YAML-frontmatter-tiedoilla.

Kansioon voidaan dokumentoida esimerkiksi:

- käyttäjäryhmät, tarpeet ja tavoitteet
- tutkimushavainnot
- prosessit ja palvelupolut
- käyttötapaukset ja käyttäjätarinat
- kipukohdat ja pullonkaulat
- vaatimukset ja rajoitteet
- ratkaisuideat ja konseptit
- hypoteesit ja oletukset
- päätökset ja niiden perustelut
- avoimet kysymykset
- prototyypeistä, testeistä ja asiakaspalautteesta saadut havainnot

Määritä ohjeisiin seuraavat käytännöt:

- Dokumentaatiota päivitetään projektisessioiden, uuden materiaalin, päätösten ja palautteen perusteella.
- Ennen uuden dokumentin luomista tarkistetaan, onko tiedolle jo olemassa sopiva dokumentti.
- Päivityksissä säilytetään dokumenttien väliset linkit, lähdeviitteet ja yhteinen rakenne.
- Jos projektissa on jo YAML-frontmatter-käytäntö, käytä sitä. Muussa tapauksessa määritä kevyt yhteinen rakenne, joka sisältää vähintään otsikon, dokumenttityypin, tilan, päivityspäivän, tunnisteet ja lähteet.
- Fakta, käyttäjähavainto, oletus, hypoteesi ja ratkaisuidea erotetaan toisistaan.
- Vanhaa tietoa ei poisteta ilman perusteltua syytä. Vanhentunut tieto merkitään vanhentuneeksi tai korvatuksi.
- Merkittävät ristiriidat ja avoimet kysymykset nostetaan käyttäjän päätettäväksi.

### `Prototyypit/`

Kansio sisältää projektin toiminnalliset prototyypit. Prototyypit luodaan Claude Designilla.

Prototyyppien tarkoituksena on:

- konkretisoida ja arvioida konsepteja
- validoida oletuksia
- kerätä käyttäjä- ja asiakaspalautetta
- testata käyttötapauksia ja palvelupolkuja
- toimia lähtökohtana varsinaiselle kehitystyölle

Määritä ohjeisiin seuraavat periaatteet:

- Prototyyppi ei ole automaattisesti tuotantovalmis toteutus.
- Prototyypin tulee perustua UX-dokumentaatiossa kuvattuihin tarpeisiin, käyttötapauksiin ja oletuksiin.
- Prototyyppiin liittyvät keskeiset oletukset, testattavat kysymykset ja rajaukset dokumentoidaan.
- Prototyypeistä saatu palaute ja validointitulokset päivitetään takaisin UX-dokumentaatioon.
- Prototyyppien ja niitä koskevien UX-dokumenttien välille luodaan jäljitettävä yhteys.

## Agentin työnkulku

Kuvaa ohjeissa vähintään seuraava perusprosessi:

1. Tarkista tehtävä, olemassa oleva dokumentaatio ja relevantit materiaalit.
2. Tunnista uudet havainnot, muutokset, ristiriidat ja avoimet kysymykset.
3. Päivitä ensisijaisesti olemassa olevia UX-dokumentteja.
4. Luo uusi dokumentti vain, jos tiedolle ei ole sopivaa paikkaa.
5. Lisää tai päivitä YAML-frontmatter, sisäiset linkit ja lähdeviitteet.
6. Tarkista, ettei sama tieto ole ristiriitaisesti useassa dokumentissa.
7. Raportoi tehdyt muutokset, käytetyt lähteet, epävarmuudet ja käyttäjän päätöstä vaativat asiat.

## Yleiset toimintaperiaatteet

Sisällytä molempiin ohjeisiin soveltuvin osin seuraavat säännöt:

- Käytä oletusarvoisesti suomea, ellei projektin nykyinen dokumentaatio tai käyttäjä ohjeista muuta.
- Säilytä olemassa oleva tiedostojen nimeämis- ja dokumentointitapa.
- Älä keksi käyttäjätutkimuksen tuloksia, päätöksiä tai asiakasvaatimuksia.
- Merkitse lähde ja epävarmuuden taso aina, kun tieto perustuu tulkintaan.
- Pyydä käyttäjän päätös, jos muutos vaikuttaa projektin keskeisiin linjauksiin tai tietojen poistamiseen.
- Vältä tarpeetonta dokumentaatiota ja päällekkäisiä tiedostoja.
- Pidä ohjeet konkreettisina, tiiviinä ja toteutettavina.

## Valmiin työn kriteerit

Tehtävä on valmis, kun:

- projektin juuressa ovat `AGENTS.md` ja `CLAUDE.md`
- tiedostojen roolit ja keskinäinen suhde ovat selkeitä
- jokaisen projektikansion tarkoitus ja käsittelysäännöt on dokumentoitu
- materiaalien, UX-dokumentaation ja prototyyppien välinen työnkulku on kuvattu
- lähteiden, epävarmuuksien ja ristiriitojen käsittelylle on selkeät säännöt
- ohjeissa ei ole tarpeetonta päällekkäisyyttä tai keskinäisiä ristiriitoja
- muita projektin tiedostoja ei ole muutettu

## Lopputervehdys käyttäjälle

Kerro lopuksi lyhyesti, mitä tiedostoja loit tai päivitit ja mitkä olivat tärkeimmät määrittelemäsi toimintaperiaatteet.
