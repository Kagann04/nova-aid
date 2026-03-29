# nova-aid
uzaya gönderilmek istenen roket, uydu ve yörünge araçlarının belirli faktörler baz alınarak güvenlik riskini hesaplayarak yeryüzünde en uygun fırlatma noktalarını tespit eden ve roket kalkış ve ürün tedarik merkezlerini gösteren  yapay zeka destekli Chatbot modülü içeren simülasyon aracı tasarlanmıştır.


##Proje Uçtan Uca Nasıl Çalışıyor?
Simülasyonumuz, Kritik Veri Entegrasyonu Sistemi üzerinden üç ana veri beslemesini birleştiren bir mimariye sahiptir:
## 
Veri Katmanlarının Analizi:
Fırlatma sahasının tam konumu (enlem, boylam, rakım) gibi coğrafi veriler,
Rüzgar hızı, bulut yoğunluğu, sıcaklık, nem, görüş mesafesi gibi fırlatma limitlerini belirleyen meteorolojik kriterler,
Roket kütlesi, sistem enerji verimliliği, yakıt ikmal şekilleri gibi lojistik entegrasyonlar,

## Hesaplama Mantığı:
Parametrelerin tümü, Ağırlıklı Parametre Hesabı algoritması ile sisteme sokulur. Meteorolojik kısıtlar ve yakıt analizi, belirlenen ağırlık katsayalarına göre hesaplanarak fırlatma güvenlik oranı ve başarı olasılığı belirlenir.

## Karar Destek Çıktıları:
Hesaplama sonuçları, interaktif bir panel üzerinden kullanıcıya sunulur. Fırlatma rotası, risk seviyesi, yakıt analizi gibi kritik bilgiler bu panel üzerinden kullanıcıya sunulur.

## Hangi Problemi Çözüyor?

**Belirsizliğin Giderilmesi:**
Karmaşık meteorolojik ve lojistik verileri birleştiren bir sistemle, “Fırlat/Bekle” kararı Yeşil, Sarı ve Kırmızı renklere dönüştürülür. Herkes tarafından anlaşılır bir formda zaman çizelgesi oluşturulur.

**Güvenlik ve Risk Yönetimi:**
Roket düşme riski

## Hangi teknolojiler kullanıldı?

**Temel Web Teknolojileri:**

- HTML5 & CSS3: Modern arayüz tasarımı, CSS Değişkenleri, Flexbox yapısı, CSS animasyonları ve "Glassmorphism" kullanıldı.
- JavaScript: DOM manipülasyonu, asenkron veri çekme işlemleri (async / await), olay dinleyicileri (event listeners) ve temel matematik/mantık hesaplamaları için saf JavaScript tercih edildi.

**Görüntüleme ve Harita Kütüphaneleri**

- Three.js: WebGL tabanlı 3D grafik oluşturma motoru. Dünya, ay, güneş ışınları, atmosfer katmanı ve noktalar arası bağlantı çizgilerini 3 boyutlu uzayda render etmek için kullanıldı.
- OrbitControls.js: Three.js kamerasını fare ile döndürmek, yakınlaştırmak ve pan yapmak için kullanıldı.
- Leaflet.js: 2D etkileşimli haritalar oluşturmak için kullanılan açık kaynaklı, popüler bir JavaScript kütüphanesi.

**Tipografi:**

- Google Fonts: Siberpunk/Taktiksel hissiyatı vermek için Outfit ve Share Tech Mono fontları entegre edildi.

## Veri kaynakları neler?

**API:**

- Hava Durumu Verisi (Open-Meteo API): Koordinatlara göre anlık sıcaklık, nem, rüzgar hızı, bulutluluk oranı ve görüş mesafesi verilerini çekmek için kullanıldı (https://api.open-meteo.com/...). Tamamen ücretsiz ve açık kaynaklı bir hava durumu API'si.
- Konum Arama / Geocoding (Nominatim - OpenStreetMap): Sol menüdeki "GBT TERMİNALİ" üzerinden girilen şehir veya işletme isimlerini enlem ve boylam (koordinat) verisine çevirmek için kullanıldı (https://nominatim.openstreetmap.org/search...).


**Harita ve Doku Kaynakları:**

- 2D Uydu Haritası (ArcGIS World Imagery): İkinci dosyadaki Leaflet haritasının arka planında yüksek çözünürlüklü uydu görüntülerini sağlamak için Esri/ArcGIS sunucuları kullanıldı.
- 3D Gezegen Dokuları (Three.js GitHub Reposu): İlk dosyadaki Dünya ve Ay'ın üzerindeki kaplamalar (normal map, specular map, bulutlar vb.) direkt olarak mrdoob/three.js GitHub deposundan çekildi.

**Statik (Gömülü) Veriler**

- Tesis ve Lojistik Noktaları: Kodun içerisine doğrudan yazılmış olan pointsList ve factoryPoints dizileri. Uzay endüstrisi şirketlerinin (SpaceX, Blue Origin, NASA, ASELSAN, Avio vb.) üretim merkezleri, koordinatları ve kargo risk analizleri statik veri olarak tanımlandı.
