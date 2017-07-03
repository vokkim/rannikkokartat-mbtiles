# Rannikkokartat

Liikenneviraston rannikkokartat
 * MBTiles-tiedostona: https://drive.google.com/file/d/0B2ZBtWtdUvsfdFkzYnoyeDhtNG8/ (5.32 GB)
 * Hostattuna: http://rannikko.merikartat.space/v1/{z}/{x}/{y}.png

- Tasot 4-10: `Yleiskartat`
- Tasot 11-15: `Rannikkokartat`

Lähde: Liikennevirasto. Ei navigointikäyttöön. Ei täytä virallisen merikartan vaatimuksia.

Versio 1.0 ladattu 1.6.2017 liikenneviraston WMTS-palvelusta: https://julkinen.liikennevirasto.fi/rasteripalvelu/wmts

Kartta-aineistojen käyttölupa on [Creative Commons 4.0 Nimeä ja käytettävä attribuutio](https://creativecommons.org/licenses/by/4.0/).

## Karttojen luonti

Karttojen tasot on laskettu `gdaladdo`-työkalulla ja tämän jälkeen yhdistetty yhdeksi MBTiles-tiedostoksi.

```
wmts-to-mbtiles --layer 'liikennevirasto:Yleiskartat public' --zoom 10 --output yleiskartat.mbtiles
wmts-to-mbtiles --layer 'liikennevirasto:Rannikkokartat public' --zoom 15 --output rannikkokartat.mbtiles
gdaladdo -r cubic yleiskartat.mbtiles 2 4 8 16 32 64
gdaladdo -r cubic rannikkokartat.mbtiles 2 4 8 16
```
