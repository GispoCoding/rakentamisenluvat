---
layout: "default"
description: ""
id: "dokumentaatio"
status: "Keskeneräinen"
---

# Loogisen tason rakentamiseen liittyvien lupapäätösten tietomalli

{:.no_toc}

{% include common/note.html content="Tietomallin dokumentaatio on toistaiseksi puutteellinen. Täydelliset luokkien, niiden attribuuttien ja assosiaatioden kuvaukset laaditaan mahdollisimman pian" %}

1.  {:toc}

## Yleistä

Loogisen tason Rakentamisen lupapäätösten tietomalli määrittelee yhteiset tietorakenteet, joita käytetään luvanvaraisia rakentamis-, poikkeamis-, maisematyö- ja purkamistoimenpiteitä sisältävien lupa-asioiden, niihin liittyvien lupahakemusten ja -päätösten, myönnettyjen lupien, sekä rakentamishankkeiden ja katselmusten tietojen kuvaamiseen koneluettavassa rakenteisessa paikkatietomuodossa. Tietomallin luokkia tulee käyttää tietomallin [elinkaari](../elinkaarisaannot.html)- ja [laatusääntöjen](../laatusaannot.html) mukaisesti. Looginen tietomalli pyrkii olemaan mahdollisimman riippumaton tietystä toteutusteknologiasta tai tiedon fyysisestä esitystavasta (esim. relaatiotietokanta, tietyn ohjelmointikielen tietorakenteet, XML, JSON).

## Normatiiviset viittaukset

Seuraavat dokumentit ovat välttämättömiä tämän dokumentin täysipainoisessa soveltamisessa: \* {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/" title="Rakennetun ympäristön yhteiset tietokomponentit" %}, versio 1.0 \* {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/" title="Rakennuskohteet ja huoneistot" %}, versio 1.0 \* [ISO 639-2:1998 Codes for the representation of names of languages --- Part 2: Alpha-3 code](https://www.iso.org/standard/4767.html "ISO 639-2:1998 Codes for the representation of names of languages — Part 2: Alpha-3 code") \* [ISO 8601-1:2019 Date and time --- Representations for information interchange --- Part 1: Basic rules](https://www.iso.org/standard/70907.html "ISO 8601-1:2019 Date and time — Representations for information interchange — Part 1: Basic rules") \* [ISO 19103:2015 Geographic information --- Conceptual schema language](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language") \* [ISO 19107:2019 Geographic information --- Spatial schema](https://www.iso.org/standard/66175.html "ISO 19107:2019 Geographic information — Spatial schema") \* [ISO 19108:2002 Geographic information --- Temporal schema](https://www.iso.org/standard/26013.html "ISO 19108:2002 Geographic information — Temporal schema") \* [ISO 19109:2015 Geographic information --- Rules for application schema](https://www.iso.org/standard/59193.html "ISO 19109:2015 Geographic information — Rules for application schema") \* [ISO 19505-2:ISO/IEC 19505-2:2012, Information technology --- Object Management Group Unified Modeling Language (OMG UML) --- Part 2: Superstructure](https://www.iso.org/standard/52854.html "ISO/IEC 19505-2:2012, Information technology — Object Management Group Unified Modeling Language (OMG UML) — Part 2: Superstructure")

## Standardienmukaisuus

Kuvattu tietomalli perustuu [ISO 19109](https://www.iso.org/standard/59193.html "ISO 19109:2015 Geographic information — Rules for application schema")-standardin yleinen kohdetietomalliin (General Feature Model, GFM), joka määrittelee rakennuspalikat paikkatiedon ISO-standardiperheen mukaisten sovellusskeemojen määrittelyyn. GFM kuvaa muun muassa metaluokat `FeatureType`, `AttributeType` ja `FeatureAssociationType`. Kaavatietomallissa kaikki tietokohteet, joilla on tunnus ja jota voivat esiintyä erillään toisista kohteista on määritelty kohdetyypeinä (stereotyyppi `FeatureType`. Sellaiset tietokohteet, joilla ei ole omaa tunnusta ja jotka voivat esiintyä vain kohdetyyppien attribuuttien arvoina on määritelty [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardin `DataType`-stereotyypin avulla. Lisäksi [HallinnollinenAlue](#hallinnollinenalue) ja [Organisaatio](#organisaatio) on mallinnettu vain rajapintojen (`Interface`) avulla, koska on niitä ei ole tarpeen kuvata kaavatietomallissa yksityiskohtaisesti, ja on todennäköistä, että tietovarastoja ylläpitävät tietojärjestelmät tarjovat niille konkreettiset toteuttavat luokat.

[ISO 19109](https://www.iso.org/standard/59193.html "ISO 19109:2015 Geographic information — Rules for application schema") -standardin lisäksi tietomalli perustuu muihin paikkatiedon ISO-standardeihin, joista keskeisimpiä ovat [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language") (UML-kielen käyttö paikkatietojen mallinnuksessa), [ISO 19107](https://www.iso.org/standard/66175.html "ISO 19107:2019 Geographic information — Spatial schema") (sijaintitiedon mallintaminen) ja [ISO 19108](https://www.iso.org/standard/26013.html "ISO 19108:2002 Geographic information — Temporal schema") (aikaan sidotun tiedon mallintaminen).

### Muulla määritellyt luokat ja tietotyypit

#### Rakennetun ympäristön yhteiset tietokomponentit

Malli perustuu {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/" title="Rakennetun ympäristön yhteiset tietokomponentit" %} -kirjaston määrittelyille. Tässä mallissa hyönnetään suoraan seuraavia kirjaston luokkia:

-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#versioituobjekti" title="VersioituObjekti" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#liiteasiakirja" title="Liiteasiakirja" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttöjarakentamisasia" title="AlueidenkäyttöJaRakentamisasia" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttöjarakentamispäätös" title="AlueidenkäyttöJaRakentamispäätös" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#alueidenkäyttöjarakentamismääräys" title="AlueidenkäyttöJaRakentamismääräys" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#rakennetunympäristönlupaasia" title="RakennetunYmpäristönLupaAsia" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#rakennetunympäristönlupahakemus" title="RakennetunYmpäristönLupahakemus" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#rakennetunymäristönlupapäätös" title="RakennetunYmpäristönLupapäätös" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#rakennetunympäristönlupa" title="RakennetunYmpäristönLupa" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#toimija" title="Toimija" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#osoite" title="Osoite" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#kiinteistö" title="Kiinteistö" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#henkilö" title="Henkilö" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktiasiaelinkaaritila" title="AbstraktiAsianElinkaaritila" %}
-   {% include common/moduleLink.html moduleId="yhteisetkomponentit" path="looginenmalli/dokumentaatio/#abstraktilupamääräyksenlaji" title="AbstraktiLupamääräyksenlaji" %}

#### Rakennuskohteet ja huoneistot -tietomallin luokat

Malli hyödyntää laajasti {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/" title="Rakennuskohteet ja huoneistot" %} -tietomallin määrittelyjä. Tässä mallissa hyödynnetään suoraan seuraavia tietomallin luokkia:

-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#rakennussuunnitelma" title="Rakennussuunnitelma" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#erityissuunnitelma" title="Erityissuunnitelma" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#rakennustietomalli" title="Rakennustietomalli" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#rakennuskohteentoimenpide" title="RakennuskohteenToimenpide" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#rakennuskohteenmuutos" title="RakennuskohteenMuutos" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#rakennussuunnitelma" title="Rakennussuunnitelma" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#rakennuskohde" title="Rakennuskohde" %}
-   {% include common/moduleLink.html moduleId="rakennuskohteet" path="looginenmalli/dokumentaatio/#huoneisto" title="Huoneisto" %}

#### CharacterString {#characterstring}

Kuvaa yleisen merkkijonon, joka koostuu 0..\* merkistä, merkkijonon pituudesta, merkistökoodista ja maksimipituudesta. Määritelty rajapinta-tyyppisenä [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa.

#### LanguageString

Kuvaa kielikohtaisen merkkijonon. Laajentaa [CharacterString](#characterstring)-rajapintaa lisäämällä siihen `language`-attribuutin, jonka arvo on `LanguageCode`-koodiston arvo. Kielikoodi voi [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardin määritelmän mukaan olla mikä tahansa ISO 639 -standardin osa.

#### Number {#number}

Kuvaa yleisen numeroarvon, joka voi olla kokonaisluku, desimaaliluku tai liukuluku. Määritelty rajapintana [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa.

#### Integer

Laajentaa [Number](#number)-rajapintaa kuvaamaan numeron, joka on kokonaisluku ilman murto- tai desimaaliosaa. Määritelty rajapintana [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa.

#### Decimal

Laajentaa [Number](#number)-rajapintaa kuvaamaan numeron, joka on desimaaliluku. Decimal-rajapinnan toteuttava numero voidaan ilmaista virheettä yhden kymmenysosan tarkkuudella. Määritelty rajapintana [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa. Decimal-numeroita käytetään, kun desimaalien käsittelyn tulee olla tarkkaa, esim. rahaan liityvissä tehtävissä.

#### Real

Laajentaa [Number](#number)-rajapintaa kuvaamaan numeron, joka on tarkkudeltaan rajoitettu liukuluku. Real-rajapinnan numero voi ilmaista tarkasti vain luvut, jotka ovat 1/2:n (puolen) potensseja. Määritelty rajapintana [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa. Käytännössä esitystarkkuus riippuu numeron tallentamiseen varattujen bittien määrästä, esim. `float (32-bittinen)` (tarkkuus 7 desimaalia) ja `double (64-bittinen)` (tarkkuus 15 desimaalia).

#### Measure

Mittattavan, numeerisen tiedon ja sen antamiseen käytetyn mittayksikön kuvaamiseen käytettävä yleiskäyttöinen tietorakenne. Määritelty [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa.

#### TM_Object

Aikamääreiden yhteinen yläluokka, käytetään, mikäli arvo voi olla joko yksittäinen ajanhetki tai aikaväli. Määritelty luokkana [ISO 19108](https://www.iso.org/standard/26013.html "ISO 19108:2002 Geographic information — Temporal schema")-standardissa.

#### TM_Instant {#tm_instant}

Kuvaa yksittäisen ajanhetken 0-ulotteisena ajan geometriana, joka vastaa pistettä avaruudessa. Määritelty luokkana [ISO 19108](https://www.iso.org/standard/26013.html "ISO 19108:2002 Geographic information — Temporal schema")-standardissa. Aikapisteen arvo on määritelty `TM_Position`-luokalla yhdistelmänä [ISO 8601](https://www.iso.org/standard/70907.html "ISO 8601-1:2019 Date and time — Representations for information interchange — Part 1: Basic rules")-standin mukaisia päivämäärä- tai kellonaika-kenttiä tai näiden yhdistelmää, tai muuta `TM_TemporalPosition`-luokan avulla kuvattua aikapistettä. Viimeksi mainitun luokan attribuutti `indeterminatePosition` mahdollistaa ei-täsmällisen ajanhetken ilmaisemisen liittämällä mahdolliseen arvoon luokittelun tuntematon, nyt, ennen, jälkeen tai nimi.

#### TM_Period

Kuvaa aikavälin [TM_Instant](#tm_instant)-tyyppisten `begin`- ja `end`-attribuuttien avulla. Molemmat attribuutit ovat pakollisia, mutta voivat sisältää tuntemattoman arvon `indeterminatePosition = unknown` -attribuutin arvon avulla annettuna. Määritelty luokkana [ISO 19108](https://www.iso.org/standard/26013.html "ISO 19108:2002 Geographic information — Temporal schema")-standardissa.

#### URI

Määrittää merkkijonomuotoisen Uniform Resource Identifier (URI) -tunnuksen [ISO 19103](https://www.iso.org/standard/56734.html "ISO 19103:2015 Geographic information — Conceptual schema language")-standardissa. URIa voi käyttää joko pelkkänä tunnuksena tai resurssin paikantimena (Uniform Resource Locator, URL).

#### Geometry

Kaikkien geometria-tyyppien yhteinen rajapinta [ISO 19107](https://www.iso.org/standard/66175.html "ISO 19107:2019 Geographic information — Spatial schema")-standardissa. Tyypillisimpiä [ISO 19107](https://www.iso.org/standard/66175.html "ISO 19107:2019 Geographic information — Spatial schema")-standardin Geometry-rajapintaa laajentavia rajapintoja ovat `Point`, `Curve`, `Surface` ja `Solid` sekä `Collection`, jota käyttämällä voidaan kuvata geometriakokoelmia (multipoint, multicurve, multisurface, multisolid).

#### Point

Täsmälleen yhdestä pisteestä koostuva geometriatyyppi. Määritelty rajapintana [ISO 19107](https://www.iso.org/standard/66175.html "ISO 19107:2019 Geographic information — Spatial schema")-standardissa.

## Tietomallin yleispiirteet

## Rakentamisen luvat

### Rakentamislupahakemus

Englanninkielinen nimi: **permit application**

Kuvaa käsitteen Rakentamislupahakemus, erikoistaa luokkaa [RakennetunympäristönLupahakemus](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupahakemus), Stereotyyppi: FeatureType (kohdetyyppi)

Hakemus, joka kohdistuu esim. rakentamislupa-asiaan

**Ominaisuudet**

| Nimi       | Name                                | Tyyppi                | Kardinaliteetti | Kuvaus                                                                                                               |
|---------------|---------------|---------------|---------------|---------------|
| lupatyyppi | type of building permit application | [RakentamisluvanLaji] | 1               | Hakemuksen tyyppi kuvaa, mistä asiassa on kysymys, onko kyseessä rakentamislupa-, purkamislupa-, maisematyöasia jne. |

**Assosiaatiot**

| Roolinimi           | Role name         | Kohde                                                                                                                         | Kardinaliteetti | Kuvaus                                                                                                                    |
|---------------|---------------|---------------|---------------|---------------|
| rakennussuunnitelma | construction plan | [Rakennussuunnitelma](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennussuunnitelma) | 0..\*           | Rakentamista koskeva suunnitelma, joka on perustana rakennettavan kohteen erityissuunnittelulle ja muulle suunnittelulle. |
| suunnitelmamalli    |                   | [Rakennustietomalli](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennustietomalli)   | 0..\*           |                                                                                                                           |

### RakentamislupaAsia

Englanninkielinen nimi:

Kuvaa käsitteen RakentamislupaAsia, erikoistaa luokkaa [RakennetunYmpäristönLupaAsia](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupaasia), Stereotyyppi: FeatureType (kohdetyyppi)

**Assosiaatiot**

| Roolinimi  | Role name           | Kohde                                                                                                                                     | Kardinaliteetti | Kuvaus                                                                              |
|---------------|---------------|---------------|---------------|---------------|
| toimenpide | construction action | [RakennuskohteenToimenpide](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteentoimenpide) | 0..\*           | maankäyttöprosessi jossa määriteltyjen vaiheiden mukaisesti tuotetaan rakennuskohde |

### Rakentamislupa

Englanninkielinen nimi: **building permit**

Kuvaa käsitteen Rakentamislupa, erikoistaa luokkaa [RakennetunYmpäristönLupa](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupa), Stereotyyppi: FeatureType (kohdetyyppi)

**Ominaisuudet**

| Nimi                | Name                                | Tyyppi                | Kardinaliteetti | Kuvaus |
|---------------|---------------|---------------|---------------|---------------|
| lupatyyppi          | type of building permit application | [RakentamisluvanLaji] | 1               |        |
| raukeamispäivämäärä | expiry date                         | date                  | 0..1            |        |

### ToimenpiteenJatkoaikapäätös

Englanninkielinen nimi:

Kuvaa käsitteen ToimenpiteenJatkoaikapäätös, erikoistaa luokkaa [AlueidenkäyttöjaRakentamispäätös](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#alueidenk%C3%A4ytt%C3%B6jarakentamisp%C3%A4%C3%A4t%C3%B6s), Stereotyyppi: FeatureType (kohdetyyppi)

**Ominaisuudet**

| Nimi                         | Name | Tyyppi | Kardinaliteetti | Kuvaus |
|------------------------------|------|--------|-----------------|--------|
| jatkoajanPäättymispäivämäärä |      | date   | 1               |        |

**Assosiaatiot**

| Roolinimi    | Role name           | Kohde                                                                                                                                     | Kardinaliteetti | Kuvaus                                                                              |
|---------------|---------------|---------------|---------------|---------------|
| toimenpide   | construction action | [RakennuskohteenToimenpide](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteentoimenpide) | 1..\*           | maankäyttöprosessi jossa määriteltyjen vaiheiden mukaisesti tuotetaan rakennuskohde |
| jatkettuLupa |                     | [Rakentamislupa]                                                                                                                          | 1               |                                                                                     |

### Purkamislupahakemus

Englanninkielinen nimi:

Kuvaa käsitteen Purkamislupahakemus, erikoistaa luokkaa [RakennetunYmpäristönLupahakemus](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupahakemus), Stereotyyppi: FeatureType (kohdetyyppi)

### PurkamislupaAsia

Englanninkielinen nimi:

Kuvaa käsitteen PurkamislupaAsia, erikoistaa luokkaa [RakennetunYmpäristönLupaAsia](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupaasia), Stereotyyppi: FeatureType (kohdetyyppi)

**Assosiaatiot**

| Roolinimi  | Role name           | Kohde                                                                                                                                     | Kardinaliteetti | Kuvaus                                                                              |
|---------------|---------------|---------------|---------------|---------------|
| toimenpide | construction action | [RakennuskohteenToimenpide](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteentoimenpide) | 0..\*           | maankäyttöprosessi jossa määriteltyjen vaiheiden mukaisesti tuotetaan rakennuskohde |

### Purkamislupa

Englanninkielinen nimi:

Kuvaa käsitteen Purkamislupa, erikoistaa luokkaa [RakennetunYmpäristönLupa](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupa), Stereotyyppi: FeatureType (kohdetyyppi)

### Maisematyölupahakemus

Englanninkielinen nimi:

Kuvaa käsitteen Maisematyölupahakemus, erikoistaa luokkaa [RakennetunYmpäristönLupahakemus](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupahakemus), Stereotyyppi: FeatureType (kohdetyyppi)

### MaisematyölupaAsia

Englanninkielinen nimi:

Kuvaa käsitteen MaisematyölupaAsia, erikoistaa luokkaa [RakennetunYmpäristönLupaAsia](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupaasia), Stereotyyppi: FeatureType (kohdetyyppi)

**Assosiaatiot**

| Roolinimi              | Role name | Kohde                                                                                                        | Kardinaliteetti | Kuvaus |
|---------------|---------------|---------------|---------------|---------------|
| työnSuorituskiinteistö |           | [Kiinteistö](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#kiinteist%C3%B6) | 0..\*           |        |

### Maisematyölupa

Englanninkielinen nimi:

Kuvaa käsitteen Maisematyölupa, erikoistaa luokkaa [RakennetunYmpäristönLupa](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupa), Stereotyyppi: FeatureType (kohdetyyppi)

### Poikkeamislupahakemus

Englanninkielinen nimi:

Kuvaa käsitteen Poikkeamislupahakemus, erikoistaa luokkaa [RakennetunYmpäristönLupahakemus](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupahakemus), Stereotyyppi: FeatureType (kohdetyyppi)

### PoikkeamislupaAsia

Englanninkielinen nimi:

Kuvaa käsitteen PoikkeamislupaAsia, erikoistaa luokkaa [RakennetunYmpäristönLupaAsia](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupaasia), Stereotyyppi: FeatureType (kohdetyyppi)

**Assosiaatiot**

| Roolinimi     | Role name | Kohde             | Kardinaliteetti | Kuvaus |
|---------------|-----------|-------------------|-----------------|--------|
| toteutushanke |           | [Rakentamishanke] | 0..1            |        |

### Poikkeamislupa

Englanninkielinen nimi: **käännös tähän**

Kuvaa käsitteen Poikkeamislupa, erikoistaa luokkaa [RakennetunYmpäristönLupa](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupa), Stereotyyppi: FeatureType (kohdetyyppi)

## Hankkeet ja katselmukset

### Rakentamishanke

Englanninkielinen nimi: **construction project**

Kuvaa käsitteen Rakentamishanke, erikoistaa luokkaa [VersioituObjekti](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#versioituobjekti), Stereotyyppi: FeatureType (kohdetyyppi)

Rakentamislupahakemukseen liittyvän rakentamishankkeen kuvaustiedot

**Ominaisuudet**

| Nimi                 | Name                                | Tyyppi               | Kardinaliteetti | Kuvaus                                                                                                                                  |
|---------------|---------------|---------------|---------------|---------------|
| toimenpide           | Project action                      | [HankkeenToimenpide] | 0..\*           | Liittyvän rakentamistoimenpiteen hankkeenaikainen edistymis- ja valmistumistieto                                                        |
| hankkeenKuvaus       | description of construction project | [LanguageString]     | 0..\*           | Rakentamishankkeen sanallinen kuvaus                                                                                                    |
| aloittamispäivämäärä | start date                          | date                 | 0..1            | Hankkeen aloittamispäivämäärä, päivämäärä, jolloin asiaan liittyvien rakentamistoimenpiteiden on katsottu alkaneeksi/arvioitu alkavaksi |
| päättymispäivämäärä  | end date                            | date                 | 0..1            | Päivämäärä, jolloin hankkeen katsotaan päättyneen, yleensä lopullisen loppukatselmuksen päivämäärä.                                     |

**Assosiaatiot**

| Roolinimi           | Role name | Kohde                                                                                                                                         | Kardinaliteetti | Kuvaus                                                                                                                                                                     |
|---------------|---------------|---------------|---------------|---------------|
| vaadittuLupa        |           | [RakennetunYmpäristönLupa](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#rakennetunymp%C3%A4rist%C3%B6nlupa) | 0..\*           | Lupapäätös, joka mahdollistaa rakentamishankkeen toteuttamisen                                                                                                             |
| vastaavaTyönjohtaja |           | [Henkilö](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#henkil%C3%B6)                                        | 1               | henkilö, jonka tehtävänä on johtaa rakennustyötä                                                                                                                           |
| suunnittelija       |           | [Toimija](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#toimija)                                             | 0..\*           | henkilö, jonka tehtävänä on laatia rakentamista koskevia suunnitelmia ja selvityksiä ja jonka tulee täyttää lainsäädännössä annetut tehtäväkohtaiset kelpoisuusvaatimukset |
| hankkeeseenRyhtyvä  |           | [Toimija](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#toimija)                                             | 1               | Rakentamishankkeeseen ryhtyvä                                                                                                                                              |

### Katselmus

Englanninkielinen nimi: **Inspection**

Kuvaa käsitteen Katselmus, erikoistaa luokkaa [VersioituObjekti](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#versioituobjekti), Stereotyyppi: FeatureType (kohdetyyppi)

Rakennushankkeen viranomaiskatselmukset

**Ominaisuudet**

| Nimi                        | Name                                  | Tyyppi                                                                                                                            | Kardinaliteetti | Kuvaus                                                                                                                 |
|---------------|---------------|---------------|---------------|---------------|
| katselmuksenLaji            | type of inspection                    | [RakentamishankkeenKatselmuksenLaji]                                                                                              | 1               | Kaavoitus- ja rakentamislain mukainen viranomaiskatselmuksen laji.                                                     |
| toimituspäivämäärä          | inspection date                       | date                                                                                                                              | 1               | Katselmuksen pitopäivämäärä                                                                                            |
| vaadittuLupamääräyksissä    | required by permit regulations        | boolean                                                                                                                           | 1               | Katselmuslajin mukainen katselmus on vaadittu lupapäätöksen määräyksissä                                               |
| osittaisuus                 | partial/final                         | [KatsemuksenLopullisuudenLaji]                                                                                                    | 1               | Onko katselmus osittainen vai lopullinen (=kyseisen katselmuslajin viimeinen katselmus kyseisessä rakennushankkeessa). |
| katselmuksenTilanne         | inspection status                     | [KatselmuksenTila]                                                                                                                | 1               | Katselmuksen tilannetieto, arvot koodistosta Katselmuksen tilanne                                                      |
| kohteenMuutos               |                                       | [RakennuskohteenMuutos](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteenmuutos) | 1..\*           |                                                                                                                        |
| käyttäänottohyväksyntä      |                                       | [Käyttöönottohyväksyntä]                                                                                                          | 0..\*           |                                                                                                                        |
| katselmuksenKohteenTarkenne | specification of object of inspection | [LanguageString]                                                                                                                  | 0..\*           | Katselmuksen kohteen tarkempi kuvaus (rakennuksen osa, laite, rappu, huoneisto\...)                                    |
| huomautus                   | inspection remarks                    | [LanguageString]                                                                                                                  | 0..\*           | Katselmuksessa havaitut huomautukset                                                                                   |
| pöytäkirja                  |                                       | [Liiteasiakirja](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#liiteasiakirja)                   |                 |                                                                                                                        |

**Assosiaatiot**

| Roolinimi             | Role name | Kohde                                                                                                                                     | Kardinaliteetti | Kuvaus                                                              |
|---------------|---------------|---------------|---------------|---------------|
| toimittaja            |           | [Henkilö](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#henkil%C3%B6)                                    | 1               |                                                                     |
| katselmoituToimenpide |           | [RakennuskohteenToimenpide](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteentoimenpide) | 0..\*           |                                                                     |
| liittyväHanke         |           | [Rakentamishanke]                                                                                                                         | 1..\*           | Rakentamislupahakemukseen liittyvän rakentamishankkeen kuvaustiedot |
| läsnäolija            |           | [Henkilö](https://tietomallit.ymparisto.fi/ry-yhteiset/v1.0/looginenmalli/dokumentaatio/#henkil%C3%B6)                                    | 0..\*           | Katselmuksessa läsnäollut henkilö                                   |

### HankkeenToimenpide

Englanninkielinen nimi: **Project action**

Kuvaa käsitteen HankkeenToimenpide, Stereotyyppi: DataType (tietotyyppi)

Kuvaa rakentamistoimepiteen edistymisen ja valmistumisen tilaa.

**Ominaisuudet**

| Nimi                              | Name                             | Tyyppi                            | Kardinaliteetti | Kuvaus                                                                                                                     |
|---------------|---------------|---------------|---------------|---------------|
| rakentamistöidenAloituspäivämäärä | start date of construction works | Date                              | 0..1            | Päivämäärä, jolloin rakentamistoimenpiteeseen liittyvät rakennustyöt katsotaan aloitetuiksi.                               |
| valmistumispäivämäärä             | completion date                  | Date                              | 0..1            | Päivämäärä, jolloin rakentamistoimenpide katsotaan kokonaan valmistuneeksi, esim. lopullisen loppukatselmuksen päivämäärä. |
| toimenpiteenTila                  |                                  | [RakennuskohteenToimenpiteenTila] | 1               |                                                                                                                            |

**Assosiaatiot**

| Roolinimi  | Role name           | Kohde                                                                                                                                     | Kardinaliteetti | Kuvaus                                                                              |
|---------------|---------------|---------------|---------------|---------------|
| toimenpide | construction action | [RekennuskohteenToimenpide](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteentoimenpide) | 1               | maankäyttöprosessi jossa määriteltyjen vaiheiden mukaisesti tuotetaan rakennuskohde |

### Käyttöönottohyväksyntä

Englanninkielinen nimi:

Kuvaa käsitteen käyttöönottohyväksyntä, Stereotyyppi: DataType (tietotyyppi)

**Ominaisuudet**

| Nimi                                | Name | Tyyppi  | Kardinaliteetti | Kuvaus                                                                                                                                                                                                                                                                                                                                              |
|---------------|---------------|---------------|---------------|---------------|
| hyväksymispäivämäärä                |      | date    | 1               | Rakentamistoimenpiteen osittaisen valmistumisen, toimenpiteen alaisen rakentamiskohtee käyttöönottamisen päivämäärä. Uudisrakentamisen osalta tämä vastaa rakennuksen käyttöönottopäivämäärää, muutos- ja laajennustoimenpiteiden osalta ajankohtaa, jolloin laajennus- tai muutosalan osittaisesti tai kokonaan on hyväksytty käyttöönotettavaksi. |
| hyväksyttyKäyttöönkokonaisuudessaan |      | boolean | 1               | Rakentamiskohde on hyväksytty käyttöönotettavaksi kokonaisuudessaan.                                                                                                                                                                                                                                                                                |

**Assosiaatiot**

| Roolinimi            | Role name | Kohde                                                                                                                                     | Kardinaliteetti | Kuvaus |
|---------------|---------------|---------------|---------------|---------------|
| hyväksyttyHuoneisto  |           | [Huoneisto](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#huoneisto)                                 | 0..\*           |        |
| hyväksyttyToimenpide |           | [RakennusKohteenToimenpide](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohteentoimenpide) | 0..\*           |        |
| hyväksyttyKohde      |           | [Rakennuskohde](https://tietomallit.ymparisto.fi/rakennuskohteet/v1.0/looginenmalli/dokumentaatio/#rakennuskohde)                         | 1..\*           |        |

## Koodistot

### RakennusvalvontaAsianElinkaaritila

{% include common/codelistref.html registry="rytj" id="rakvalv-asian-elinkaaren-tila" name="Rakennusvalvonta-asian elinkaaren tila" %}

### RakennuslupamääräyksenLaji

{% include common/codelistref.html registry="rytj" id="Lupamaarayshierarkinen" name="Lupamääräys" %}

### RakennuskohteenToimenpiteenTila

{% include common/codelistref.html registry="rytj" id="rakkohteen-toimenpiteen-tila" name="Rakennuskohteen toimenpiteen tila" %}

### RakentamisluvanLaji

{% include common/codelistref.html registry="rytj" id="LuvanSisalto" name="Sijoittamis-/toteuttamislupa" %}

### KatsemuksenLopullisuudenLaji

{% include common/codelistref.html registry="rytj" id="OsittainenLopullinen" name="Katselmuksen lopullisuus (osittainen / lopullinen katselmus)" %}

### RakentamishankkeenKatselmuksenLaji

{% include common/codelistref.html registry="rytj" id="Katselmuslaji" name="Katselmuslaji" %}

### KatselmuksenTila

{% include common/codelistref.html registry="rytj" id="KatselmuksenTilanne" name="Katselmuksen tilanne" %}
