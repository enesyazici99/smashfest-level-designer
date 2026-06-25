# Brik Level Designer (Web)

SmashFest için tarayıcıda **Brik** level tasarım aracı. Unity'dekiyle **aynı 23 Brik parçası** (GLB), aynı ızgara/koordinatlar. Tasarla → **Çıktı Al** (`level.json`) → Unity'de içe aktar.

## Çalıştırma (yerel sunucu gerekir)
GLB modelleri `fetch` ile yüklendiği için dosyayı çift tıkla AÇMAZ — yerel sunucu lazım. Bu klasörde (`WebLevelDesigner/`) terminal aç:

```bash
python -m http.server 8000
# veya Node varsa:
npx serve -l 8000
```
Sonra tarayıcıda: **http://localhost:8000**

## Arkadaşlarla paylaşım (GitHub Pages)
1. GitHub repo ▸ Settings ▸ Pages ▸ Source = `main`, klasör = `/`.
2. URL: `https://<kullanıcı>.github.io/SmashFest/WebLevelDesigner/`
3. Arkadaşın bu URL'den tasarlar, `level.json` indirir, sana yollar.

## Kullanım
- **Sol tık:** seçili parçayı yerleştir (Boya/Sil modunda boya/sil)
- **Sağ tık + sürükle:** sahneyi 3B döndür • **Tekerlek:** yakınlaş
- **WASD:** gez • **Q/E:** alçal/yüksel
- **R:** parçayı 90° döndür • **`[` / `]`:** kat (yükseklik) aşağı/yukarı

**Akış:** Parça seç → renk seç → **kat** (yükseklik) seç → masaya tıkla. Üst kata çıkıp istifle.

### Masalar (çoklu + boyutlandırılabilir)
- Sağdaki **Masalar** panelinden masa ekle/sil, **En/Boy** (hücre sayısı) ve **X/Z** konumunu ayarla.
- Aktif masanın ızgarası üst yüzeyde görünür; parçalar stud-grid'e snap'lenir.
- Birden fazla masa kullanabilirsin (her biri ayrı kule taşır).

### Çıktı / Yükleme
- **⬇️ Çıktı Al** → `level.json` iner. Format: `{ shotCount, tables[], pieces[] }`.
- **⬆️ JSON Yükle** → mevcut bir `level.json`'u açıp düzenle.

## Unity'ye aktarma
Unity ▸ **Tools ▸ SmashFest ▸ Import Brik Level** ▸ `level.json` seç → `Assets/_Project/Levels/` altına kopyalanır ve sahnedeki `_BrikLevel` (BrikLevelBuilder) ona bağlanır. Play'e bas → level kurulur.

## Koordinat sözleşmesi (Unity ile birebir)
Hücre `0.5`, **Y=0 = masa üst yüzeyi**, +Y istif (0.5 katları). Parça pivotu bottom-center.
JSON: `tables:[{x,z,cellsW,cellsD}]`, `pieces:[{type,x,y,z,rotY,color}]`.
`type` = 23 Brik'ten biri (brick_1x1 … arch/ramp/dome/cyl). `color` = red/blue/yellow/green/white/gray/wood/stone/brick.
