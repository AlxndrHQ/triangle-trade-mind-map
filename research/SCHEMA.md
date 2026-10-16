# Triangle Trade Mind Map — research data schema

Output ONE JSON file: `{"records":[...], "events":[...]}`. Valid JSON, no comments, UTF-8.

## PROFILE record (people, families, dynasties, ruling houses, and major COMPANIES/BANKS that deserve a full dossier)
```json
{
  "id": "kebab-case-unique-id",
  "name": "Display name (e.g. 'DeWolf family' or 'John Hawkins')",
  "category": "European Families" | "African States & Families" | "American Families" | "Companies & Banks" | "Crowns & Explorers",
  "role": "Explorer & Crown" | "Trader & Shipper" | "Planter & Enslaver" | "Financier & Insurer" | "Ruler & Supplier" | "Broker & Agent",
  "nation": "Portugal" | "Spain" | "Britain" | "Netherlands" | "France" | "Denmark-Norway" | "Brandenburg-Prussia" | "Sweden" | "Genoa/Florence (Italian states)" | "Holy Roman Empire (German)" | "United States" | "Brazil" | "Cuba" | "Caribbean" | "Dahomey" | "Asante" | "Oyo" | "Kongo" | "Ndongo/Angola" | "Niger Delta & Biafra" | "Gold Coast" | "Senegambia" | "Sierra Leone & Upper Guinea" | "Bight of Benin (Lagos/Ouidah)" | other short label if truly needed,
  "scale": "Minor" | "Significant" | "Major" | "Dominant",       // relative weight in the Atlantic trade
  "scaleBasis": "documented" | "estimated",
  "scaleNote": "One sentence justifying scale, with numbers where documented (voyages, captives, enslaved people held, compensation £).",
  "start": 1497,           // first year of involvement in the slave trade/slavery economy (integer)
  "end": 1512,             // last year of direct involvement (integer), or null if the entity/its successor still exists
  "lifespan": "1454–1512"  // for people; for families/companies the active span e.g. "1769–1820" or "1690–present"
  "base": "Seville, Spain",           // main base city
  "geo": [37.389, -5.984],            // [lat, lng] of base, 3 decimals
  "aliases": ["optional alt names"],
  "origins": "2–3 sentences: who they were before / how they got in.",
  "role_summary": "2–3 sentences: what exactly they did in the trade (the callout).",
  "roleDetail": [ {"t":"Short bold claim.", "d":"1–2 sentence detail with specifics.", "basis":"documented"|"interpretive"} ],   // 2–4 items
  "legacy": "2–3 sentences: where the wealth/power went and what exists TODAY (successor companies, descendants, apologies, reparations, statues removed, institutions).",
  "legacyDetail": [ {"t":"...", "d":"...", "basis":"documented"|"interpretive"} ],   // 1–3 items
  "sources": [ {"label":"Publisher — Title", "url":"https://..."} ],   // 2–4 REAL URLs you actually found via search
  "connections": [ {"id":"other-id", "type":"<edge type>", "label":"short label, e.g. 'financed 1497 voyage'"} ]
}
```

## ENTITY record (ports, forts, castles, ships, colonies, institutions, laws/charters, smaller firms, legacy institutions)
```json
{ "id":"elmina-castle", "name":"Elmina Castle (São Jorge da Mina)", "type":"entity",
  "kind":"Fort / trading castle" | "Port" | "Ship / voyage" | "Colony / plantation" | "Chartered company" | "Bank / insurer" | "Charter / law / treaty" | "University / church" | "Legacy / apology" | other short label,
  "description":"2–3 factual sentences.", "start":1482, "geo":[5.083,-1.348] (optional, for places), "connections":[...] }
```

## Edge types (use exactly these)
- `ownership` — founded / owned / shareholder / governor of
- `trade` — sold or bought captives, supplied, traded with
- `finance` — loan, credit, insurance, bills of exchange, invested
- `charter` — royal charter, licence, asiento, monopoly grant, appointed by
- `voyage` — sailed for / ship / expedition / commanded
- `plantation` — held plantations / enslaved people at
- `family` — family / marriage / descendant
- `legacy` — successor institution, merged into, apology, reparations, endowment, money flowed to
- `political` — ally, war, treaty, diplomacy, lobbying
- `parallel` — thematic parallel only (no real tie; use sparingly)

## Rules
1. Accuracy over volume. Mainstream academic scholarship only (SlaveVoyages.org, UCL Legacies of British Slavery, national archives, university reports, museum sites, Britannica, peer-reviewed or reputable press). Never use propaganda sources (e.g. Nation of Islam's "The Secret Relationship", white-supremacist or Afrocentric-myth sites). Where claims are contested, say so and mark basis "interpretive".
2. Every profile needs ≥2 sources with real, working URLs you found while searching. Don't invent URLs.
3. Numbers: cite where they come from in the text ("per SlaveVoyages", "per LBS"). Give approximate figures with "c." / "~".
4. Connections: link richly (3–8 per profile) to people, companies, ports, and the SHARED IDs below. Only link to IDs that exist in your own file or in the SHARED REGISTRY. Never create a record whose id is in the registry unless your group OWNS it.
5. Neutral, sober tone. These are records of atrocity; describe roles plainly. Use "enslaved people" / "captives", not "slaves" as a noun where avoidable.
6. "events": 8–15 key dated events for your group: `{"year":1498, "title":"Short title", "text":"1–2 sentences.", "ids":["record-ids","involved"], "source":{"label":"...","url":"..."}}`.
7. Write the file with the Write tool to the exact path given. Validate it parses: `python3 -c "import json;json.load(open('PATH'))"`.

## SHARED REGISTRY (id — name — owning group). Link freely; only the owner creates it.
G1 Iberia & explorers:
- amerigo-vespucci — Amerigo Vespucci
- christopher-columbus — Christopher Columbus
- lorenzo-di-pierfrancesco-medici — Lorenzo di Pierfrancesco de' Medici
- gianotto-berardi — Gianotto Berardi
- bartolomeo-marchionni — Bartolomeo Marchionni
- crown-of-castile — Crown of Castile / Spain (Ferdinand & Isabella, Charles V…)
- crown-of-portugal — Crown of Portugal (House of Aviz/Braganza)
- henry-the-navigator — Prince Henry "the Navigator"
- casa-de-contratacion — Casa de Contratación (Seville)
- spanish-asiento — The Spanish Asiento (licence system)
- welser-family — Welser family (Augsburg)
- fugger-family — Fugger family (Augsburg)
- port-lisbon, port-seville, port-luanda — ports
- elmina-castle — Elmina Castle (G1 owns; Portuguese-built 1482, Dutch from 1637)
- antonio-lopez-comillas — Antonio López y López, Marquis of Comillas
G2 Britain:
- royal-african-company, south-sea-company, john-hawkins, james-duke-of-york, edward-colston, lascelles-family, beckford-family, gladstone-family, codrington-family, barclays, lloyds-of-london, bank-of-england, nm-rothschild, slavery-abolition-act-1833 (entity, compensation), port-liverpool, port-bristol, port-london, bunce-island, cape-coast-castle, church-of-england, trevelyan-family
G3 Continental Europe:
- dutch-west-india-company, middelburgsche-commercie-compagnie, house-of-orange, de-nederlandsche-bank, compagnie-des-indes, port-nantes, port-bordeaux, port-amsterdam, gradis-family, danish-west-india-guinea-company, schimmelmann-family, brandenburg-african-company, saint-domingue (entity), code-noir (entity), goree-island
G4 Africa:
- kingdom-of-dahomey, francisco-felix-de-souza, port-ouidah, asante-empire, oyo-empire, kingdom-of-kongo, afonso-i-of-kongo, queen-nzinga, aro-confederacy, kingdom-of-bonny, old-calabar-efik, jaja-of-opobo, kosoko-of-lagos, madam-tinubu, caulker-family, akwamu-kingdom
G5 Americas:
- dewolf-family, brown-family-providence, brown-university, aaron-lopez, peter-faneuil, royall-family, henry-laurens, georgetown-university, franklin-and-armfield, lehman-brothers, jpmorgan-chase, wells-fargo-wachovia, aetna, new-york-life, brown-brothers-harriman, julian-de-zulueta, joaquim-pereira-marinho, clotilda-meaher, port-newport, port-charleston, port-rio-valongo, port-salvador, port-havana, pedro-blanco
