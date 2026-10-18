# Entitäten für Automatisierungen

Stand: 18.10.2026. Auszug aus der Home-Assistant-Entitätenliste, nur was für Automatisierungen gebraucht wird. Netzwerkgeräte, Updates und Router-Sensoren sind bewusst nicht enthalten.

Zigbee: Sonoff Dongle Max, ZHA. Taster und Bewegungsmelder: IKEA TRADFRI.

## Lichter

| Raum | Entität | Name |
|---|---|---|
| Wohnzimmer | `light.wohnzimmer_wohnzimmer` | Wohnzimmer (Gruppe) |
| Wohnzimmer | `light.wohnzimmer_deckenlampe` | Deckenlampe |
| Wohnzimmer | `light.wohnzimmer_esstisch` | Esstisch |
| Wohnzimmer | `light.wohnzimmer_leselampe` | Leselampe |
| Wohnzimmer | `light.wohnzimmer_stehlampe` | Stehlampe |
| Schlafzimmer | `light.schlafzimmer_schlafzimmer` | Schlafzimmer (Gruppe) |
| Schlafzimmer | `light.schlafzimmer_flo_bett` | Flo Bett |
| Schlafzimmer | `light.schlafzimmer_annika_bett` | Annika Bett |
| Arbeitszimmer | `light.arbeitszimmer_arbeitszimmer` | Arbeitszimmer (Gruppe) |
| Arbeitszimmer | `light.arbeitszimmer_schreibtisch` | Schreibtisch |
| Arbeitszimmer | `light.arbeitszimmer_3d_drucker` | 3D Drucker |

## Szenen

| Entität | Name |
|---|---|
| `scene.wohnzimmer_wohnzimmer_entspannen` | Wohnzimmer Entspannen |
| `scene.wohnzimmer_wohnzimmer_nachtlicht` | Wohnzimmer Nachtlicht |
| `scene.wohnzimmer_wohnzimmer_ruhephase` | Wohnzimmer Ruhephase |
| `scene.wohnzimmer_wohnzimmer_goldener_teich` | Wohnzimmer Goldener Teich |
| `scene.wohnzimmer_wohnzimmer_hell` | Wohnzimmer Hell |
| `scene.wohnzimmer_wohnzimmer_lesen` | Wohnzimmer Lesen |
| `scene.wohnzimmer_wohnzimmer_gedimmt` | Wohnzimmer Gedimmt |
| `scene.schlafzimmer_schlafzimmer_nachtlicht` | Schlafzimmer Nachtlicht |

## Sensoren und Taster

| Entität | Beschreibung |
|---|---|
| `binary_sensor.ikea_of_sweden_tradfri_motion_sensor` | TRADFRI Bewegungsmelder |
| `sensor.ikea_of_sweden_tradfri_motion_sensor_batterie` | Batterie Bewegungsmelder |
| `sensor.ikea_of_sweden_tradfri_on_off_switch_batterie` | Batterie TRADFRI Taster 1 |
| `sensor.ikea_of_sweden_tradfri_on_off_switch_batterie_2` | Batterie TRADFRI Taster 2 |
| `event.wohnzimmer_hue_dimmer_switch_1_taste_1` bis `_taste_4` | Hue Dimmer Wohnzimmer, Tasten 1 bis 4 |
| `sensor.wohnzimmer_hue_dimmer_switch_1_batterie` | Batterie Hue Dimmer |

Die Tastendrücke der beiden TRADFRI-Taster gibt es bei ZHA nicht als Entität. Sie werden im Automatisierungs-Editor als Gerätetrigger gewählt (Wenn → Gerät).

## Sonstiges

| Entität | Beschreibung |
|---|---|
| `sun.sun` | Sonnenstand |
| `sensor.sun_next_dawn` / `_dusk` / `_rising` / `_setting` | Dämmerung, Auf- und Untergang |
| `person.florian` | Anwesenheit Florian |
| `camera.turklingel` | Türklingel |
| `media_player.kuche_kuche` | Sonos Küche |
| `media_player.schlafzimmer_schlafzimmer` | Sonos Schlafzimmer |
| `todo.einkaufsliste` | Einkaufsliste |

## Vorhandene Automatisierungen

| Entität | Name |
|---|---|
| `automation.schlafzimmer_licht_bei_bewegung_sonnenuntergang_bis_22_30` | Schlafzimmer Licht bei Bewegung (Sonnenuntergang bis 22:30) |

Hue-Bridge-eigene Automatisierungen (laufen in der Bridge, nicht in HA): `switch.hue_bridge_automation_hue_dimmer_switch_1`, `_naturlich_aufwachen`, `_abends`, `_abend`.

## Geräte-IDs (für Gerätetrigger in ZHA)

| Gerät | Raum | `device_id` |
|---|---|---|
| IKEA TRADFRI on/off switch (E1743) | Schlafzimmer | `c4d43ed7c7218e167b55741ae374bf26` |

## Hinweis Schlafzimmer-Lampen

`light.schlafzimmer_flo_bett` und `light.schlafzimmer_annika_bett` sind Hue-Lampen an der Hue Bridge (Integration `hue`), nicht am Sonoff-Dongle. Native ZHA-Cluster-Befehle (LevelControl Move/Stop) funktionieren fuer sie daher nicht. Dimmen per Taster laeuft ueber eine getaktete Schleife in der Automatisierung.
