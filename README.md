# SmashFest — Web Level Designer

Unity bilmeyen arkadaşların tarayıcıdan level tasarlayabilsin diye. Unity'dekiyle **aynı LEGO parçaları** (GLB), aynı ızgara/koordinatlar. Tasarla → **Çıktı Al** (`level.json`) → Unity'de içe aktar.

## Çalıştırma (yerel)
Tarayıcı, GLB modellerini `file://` ile yükleyemez (CORS). Bir yerel sunucu gerekir:

```bash
cd WebLevelDesigner
# Python varsa:
python -m http.server 8000
# veya Node varsa:
npx serve .
```
Sonra tarayıcıda: `http://localhost:8000`

## Arkadaşlarla paylaşım (GitHub Pages)
1. GitHub repo ▸ Settings ▸ Pages ▸ Source = `main` / klasör = `/` (veya `/WebLevelDesigner`).
2. URL: `https://<kullanıcı>.github.io/SmashFest/WebLevelDesigner/`
3. Arkadaşların bu URL'den tasarlar, `level.json` indirir, sana yollar.

## Kullanım
- **Mod:** Yerleştir / Boya / Sil
- **Sol tık:** uygula • **Sağ tık-sürükle:** kamera • **Tekerlek:** yakınlaş
- **R:** döndür • **Q/E:** derinlik sırası (arka katman)
- **Çıktı Al:** `level.json` indirir.

## Unity'ye aktarma
Unity ▸ **Tools ▸ SmashFest ▸ Import Web Level (JSON)** ▸ `level.json` seç ▸ yeni sahne adı ver.
Parçalar otomatik stud-gizleme + fizik ile kurulur, masa parçalara sığar.

## Koordinat sözleşmesi (Unity ile aynı)
`x = stud*0.5`, `y = 2.5 + kat*0.717`, `z = 6 + derinlik*1.0`. JSON: `{type, x, y, z, rotY, color}`.
`color` = Unity materyal adı (LegoRed/Blue/Green/Yellow/Orange/Gray/Brown/White).
