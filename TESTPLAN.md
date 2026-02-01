# Testing Plan – Börsibaar

## Testing objectives
Testimise eesmärk on tagada, et Börsibaari rakendus töötab vastavalt nõuetele.

Testimiseks kasutatakse:
- automatiseeritud unit- ja integratsiooniteste
- automatiseeritud E2E teste

---

## Backend – Unit tests

### Test scope
Testitakse service-klasside äriloogikat.

### Test approach
Teste kirjutatakse meetodipõhiselt, kus läbi public meetodite kaetakse ka hargnevad private meetodid.  
Hargnevad meetodid, mis kutsuvad teisi service-klasse, mockitakse.

Testimise tulemust mõõdetakse JaCoCo abil, mis annab ülevaate:
- koodikattuvusest
- harukattuvusest

### Test environment
Teste jooksutatakse:
- lokaalses arenduskeskkonnas
- CI protsessis buildide ja merge requestide käigus

### Entry and exit criteria
- Iga unit test defineerib sisendi ja oodatava väljundi
- Järgitakse Arrange, Act, Assert (AAA) mustrit

### Roles and responsibilities
- Unit testide kirjutamine on iga taski teostaja vastutus
- Funktsionaalsuse muutmisel tuleb:
    - uuendada olemasolevaid teste
    - eemaldada üleliigsed testid
    - lisada uued vajalikud testid

### Risks and assumptions
- Unit testid ei taga kogu süsteemi korrektset tööd
- Testid kontrollivad koodi vastavust minimaalsetele nõuetele
- Üleliigne testimine võib aeglustada arendust

### Test deliverables
- JaCoCo raportid koodi- ja harukattuvuse kohta

---

## Back-End integration tests

### Test scope
Testitakse backendi kihtide omavahelist koostööd:
- controller
- service
- repository

Fookuses on äriloogika korrektne toimimine ning andmete töötlemine.

Testitakse eelkõige:
- toodete loomist ja muutmist
- laoseisu lisamist ja korrigeerimist
- sisendandmete valideerimist
- päringute ja vastuste korrektsust

### Test approach
- Testid luuakse äriloogikapõhiselt
- Kaetakse kriitilised kasutajavood
- Kõrvalised teenused mockitakse
- Repository-kiht mockitakse (andmebaasi ei kasutata)

### Test environment
- Repository-klass mockitakse
- Testid on jooksutatavad:
    - lokaalselt
    - CI/CD pipeline’is

### Entry and exit criteria
**Entry criteria:**
- back-end’i põhifunktsionaalsused on implementeeritud
- kood kompileerub
- unit-testid läbivad edukalt
- testkeskkond on seadistatud

**Exit criteria:**
- kõik planeeritud integratsioonitestid on teostatud
- kriitilised ja kõrge prioriteediga vead on parandatud
- testitulemused on dokumenteeritud

### Roles and responsibilities
- Integratsioonitestide eest vastutab testija või QA
- Arendajad:
    - tagavad rakenduse testitavuse
    - parandavad testides leitud vead

### Risks and assumptions
- Vead võivad põhjustada finantskahju ja mainekahju
- Dünaamiline hinnastamine eeldab realistlikke teenindusmahte
- Skaleeritavust eraldi ei testita

Täiendavad riskid:
- Tipptunni koormus (mitu baariterminali korraga)
- Reaalajas hinnakuvamine peab jääma kokkulepitud viiteaja piiresse

### Test deliverables
- Integratsioonitestide tulemused
- Leitud vigade kirjeldused

---

## End-to-End tests

### Test scope
Testitakse kriitilisi kasutajavooge läbi kasutajaliidese.

Testitavad vormid:
- Toote lisamise vorm (`/inventory – New Product`)
- Laoseisu muutmise vorm (`/inventory – Adjust Stock`)

### Test approach
**Automatiseeritud E2E testid:**
- Kasutatakse Cypressi
- Simuleeritakse reaalse kasutaja tegevusi
- Testitakse korrektseid ja vigaseid sisendeid
- Kontrollitakse valideerimist ja veateateid

**Manuaalne testimine:**
- Testitakse piirsituatsioone
- Kontrollitakse kasutajakogemust ja arusaadavust

**Testimise tüübid:**
- Funktsionaalne testimine
- UI testimine
- Negatiivne testimine
- Positiivne testimine

### Testimise sammud (näide)
1. Ava „New Product” vorm
2. Sisesta toote nimi: `Test Õlu`
3. Sisesta hind: `-5.00`
4. Kliki „Create Product”
5. Kontrolli:
    - kuvatakse veateade „Hind ei saa olla negatiivne”
    - vormi ei esitatud
    - toode ei ilmu inventuuri

### Test environment
- Frontend ja backend on käivitatud ja ühendatud
- Kasutatakse testandmeid
- Automatiseeritud testid:
    - lokaalselt (Cypress)
    - vajadusel CI-s
- Manuaalne testimine toimub eraldi testkeskkonnas

### Entry and exit criteria
**Entry criteria:**
- rakendus on ligipääsetav
- frontend ja backend suhtlevad
- testandmed on olemas
- vormid on implementeeritud

**Exit criteria:**
- kõik E2E testid on läbitud
- kasutajavood vastavad ootustele
- kriitilisi defekte ei esine
- defektid on dokumenteeritud

### Roles and responsibilities
- E2E testide ja manuaalse testimise eest vastutab testija või QA
- Arendajad parandavad testides leitud vead

### Risks and assumptions
- E2E testid on ajamahukad
- Eeldatakse, et backend töötab korrektselt

### Test deliverables
- Automatiseeritud E2E testide raportid (nt Cypress)
- Manuaalse testimise märkmed
- Leitud vigade kirjeldused  
