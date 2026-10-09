# meta/ — kooaa oyun bilgileri

Her oyunun kooaa platformunda görünen bilgileri burada durur. Klasör adı oyunun slug'ıdır ve `games/<slug>.html` ile aynı olmalıdır.

```
meta/<slug>/kooaa.json
meta/<slug>/logo.jpg
```

## kooaa.json

```json
{
  "category": "puzzle",
  "color": "#ff8a3d",
  "logo": "logo.jpg",
  "tr": { "name": "Neon 2048", "description": "Işık karolarını kaydır ve birleştir" },
  "en": { "name": "Neon 2048", "description": "Slide and merge tiles of light" }
}
```

| Alan | Zorunlu | Kural |
|---|---|---|
| `category` | Evet | `puzzle`, `reflex`, `calm`, `physics` gibi kısa bir anahtar. En fazla 32 karakter. |
| `color` | Hayır | `#rrggbb`. Kapak yüklenemezse arka plan rengi. |
| `logo` | Hayır | Bu klasördeki görsel dosyası: jpg, png veya webp. Dilden bağımsızdır. |
| `en` | Evet | `name` (zorunlu, en fazla 255 karakter) ve `description` (kısa, tek cümle). |
| `tr` | Hayır | `en` ile aynı yapı. Yoksa Türkçe arayüzde İngilizce gösterilir. |

## Build için gereken

`meta/` klasörü **yayınlanan çıktıda** bulunmalıdır. kooaa bu repoyu her 10 dakikada bir çeker ve `meta/` dosyalarını okur. `build.py` yayın sırasında bu klasörü olduğu gibi çıktıya kopyalamalıdır. Kaynakta tutulacak yer önerisi: `assets/meta/` → çıktıda `meta/`.

`meta/<slug>/` olmayan oyunlar için kooaa eski yönteme döner: bilgileri `index.html` içindeki katalogdan okur (yalnızca İngilizce).

## Yeni oyun eklerken

1. `meta/<slug>/kooaa.json` dosyasını oluşturun.
2. Logoyu aynı klasöre koyun.
3. Yayınlayın. Oyun kooaa'ya taslak olarak gelir; kooaa yöneticisi yayına alır.

> Ad ve açıklama kooaa'da yalnızca **ilk kez** veya kooaa'daki alan **boşsa** yazılır. Sonradan yapılan değişiklikler kooaa yönetici panelinden yapılır.
