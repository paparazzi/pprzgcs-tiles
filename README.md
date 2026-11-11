# PprzGCS tiles

Map tiles for [PprzGCS](https://github.com/paparazzi/PprzGCS) of places no online map shows in detail
(indoor flight arenas), served with GitHub Pages:

    https://paparazzi.github.io/pprzgcs-tiles/<DIR>/{z}/{x}/{y}.png

Web mercator tiles (the layout of OpenStreetMap), 256 px. PprzGCS downloads them when they are shown and
keeps them in its tiles folder (Settings, Map), so they also work offline after that.

| Folder | Place | Zoom | Made with |
|---|---|---|---|
| `CYBERZOO` | Cyberzoo, TU Delft | 18 to 23 | `tools/map_tiles` in PprzGCS (from the Gazebo model) |

## Without internet

Download this repository as a ZIP (Code, Download ZIP) and unpack its folders into the tiles folder of
PprzGCS (by default `~/.local/share/pprzgcs/map`).

## Adding a place

1. Make its tiles, e.g. with `make_tiles.py` of `tools/map_tiles` in PprzGCS (any top view: a photo, a plan).
2. Add them here in a folder of their own, `<DIR>/<z>/<x>/<y>.png`, and a line to the table above.
3. Add a source to `data/tile_sources.xml` of PprzGCS with this address and the limits of the place
   (`xMin`/`xMax`/`yMin`/`yMax`, web mercator meters), so no tiles are asked for elsewhere:

```xml
<source name="Cyberzoo" title="Cyberzoo (TU Delft)" dir="CYBERZOO"
    addr="https://paparazzi.github.io/pprzgcs-tiles/CYBERZOO/{z}/{x}/{y}.png"
    xMin="487069" xMax="487374" yMin="6798279" yMax="6798585"
    zoomMin="18" zoomMax="23" tileSize="256" format=".png"/>
```
