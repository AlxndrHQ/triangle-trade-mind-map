# The Triangle Trade — Mind Map of the Players, 1492–Today

An interactive mind map and set of dossiers on the people, families, states and companies that built, financed and profited from the transatlantic slave trade, and on the people it enslaved, the people who survived and resisted it, and the parallel Arab, trans-Saharan and Indian Ocean trades. It starts in 1492 with Amerigo Vespucci and the Seville merchant houses, and runs to the apologies, reparations debates and successor institutions of today.

**Live site:** https://alxndrhq.github.io/triangle-trade-mind-map/

## Views

| Tab | What it shows |
|---|---|
| **Web** (`#/web`) | A force-directed network of players (circles) and places/institutions (boxes). The **Timeline** layout (`#/web/timeline`) lays everything out left to right from 1492 to today. |
| **Directory** (`#/directory`) | Dossier cards in seven groups: European families; African states & families; American families; companies & banks; crowns & explorers; enslaved & free Black lives; and Arab, Saharan & Indian Ocean traders. |
| **Chronology** (`#/chronology`) | Dated events from 1492 to today, each linked to its players and a source, plus SlaveVoyages estimates "by the numbers". |
| **Overlaps** (`#/overlaps`) | Companies, ports, forts and institutions shared by two or more players, and the direct ties that cross the triangle. |
| **Map** (`#/map`) | Players pinned to their bases. The **Triangle Routes** layer (`#/map/routes`) draws the three legs and the direct Brazil–Africa trade. |

Filters for period, group, role and nation apply across every view. Click any name to open its dossier (`#/p/<id>`).

## Data

`data.json` holds `{records, events}`; `index.html` also embeds a copy so the page works when opened from disk. Each profile carries:

- `category`, `role`, `nation`, `scale` (Minor → Dominant, relative weight in the trade), `start`/`end` years, `base` and `geo`
- `origins`, `role_summary` + `roleDetail[]`, `legacy` + `legacyDetail[]`. Every detail is tagged `documented` or `interpretive`.
- `sources[]` and `connections[]` (edge types: ownership, trade, finance, charter, voyage, plantation, family, legacy, political, parallel)

Entities (ports, forts, ships, charters, institutions) use `{id, name, type:"entity", kind, description, start, geo, connections}`.

## Sources & method

The records draw on mainstream scholarship and archives: the [SlaveVoyages](https://www.slavevoyages.org) databases, UCL's [Legacies of British Slavery](https://www.ucl.ac.uk/lbs/), national and corporate archives, university reports (Brown, Georgetown, Harvard) and museum sites. Each dossier lists its own sources. Scale ratings are relative judgements, marked "est." where estimated. Including a modern institution reflects its documented historical ties or its own acknowledgement, not present-day wrongdoing.

## Rebuilding

`research/g1.json … g12.json` are the source files, one per research group: Iberia & explorers, Britain, continental Europe, African states, the Americas, African trading families, US planter families, Dutch/Portuguese/German/Swiss families, financiers & legacy today, the Middle Passage (survivors, captains, crews, ships), enslaved and free Black lives, and the Arab, trans-Saharan and Indian Ocean trades. `research/SCHEMA.md` is the record format. To merge them, check links, and regenerate `data.json` plus the embedded copy in `index.html`, run:

```sh
python3 tools/build.py research .
```

Corrections and additions are welcome. Open an issue with a source.
