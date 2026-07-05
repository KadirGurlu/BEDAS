# CK Enerji Boğaziçi Elektrik - Plansız Kesinti Etki Tahmini

Bu Streamlit web uygulaması, uç değerleri temizlenmiş plansız elektrik kesintisi verisiyle eğitilmiş **Random Forest + Log dönüşümü** modelini kullanır.

## Bu Sürümdeki Güncelleme

- Önceki web sitesi tasarımı korunmuştur.
- Veri seti **%90 eğitim / %10 test** olacak şekilde yeniden bölünmüştür.
- Model **Random Forest + Log dönüşümü** yöntemiyle yeniden eğitilmiştir.
- Model metrikleri 90-10 bölme sonucuna göre güncellenmiştir.
- CK Enerji Boğaziçi Elektrik logosu, kurumsal lacivert/turkuaz/yeşil renk tasarımı, harita ve aksiyon önerisi kutusu korunmuştur.

## Arayüz Özellikleri

- Tahmin sonucu için renkli etki sınıflandırması:
  - Yeşil: 0-50 müşteri
  - Turuncu: 51-99 müşteri
  - Kırmızı: 100+ müşteri
- Etki seviyesine göre **Aksiyon Önerisi Kutusu**:
  - Yeşil: Düşük etkili kesinti. Standart saha müdahalesi yeterli olabilir.
  - Turuncu: Orta etkili kesinti. Ekip yönlendirme ve müşteri bilgilendirmesi önerilir.
  - Kırmızı: Yüksek etkili kesinti. Öncelikli müdahale, saha ekibi takibi ve müşteri iletişimi önerilir.
- İstanbul Avrupa Yakası haritasında seçilen ilçe tahmin rengine göre gösterilir.
- Son tahmin özeti bölümünde ilçe, kesinti nedeni, süre, sıcaklık, tahmin, risk ve aksiyon bilgisi görünür.

## Model Bilgisi

- Model: Random Forest Regressor + log dönüşümü
- Eğitim/Test bölünmesi: %90 eğitim / %10 test
- Hedef değişken: Etkilenen abone/müşteri sayısı
- Veri satırı: 4675
- Eğitim satırı: 4207
- Test satırı: 468

## Dosyalar

- `app.py`: Streamlit web uygulaması
- `assets/ck_enerji_logo.png`: Uygulamada kullanılan logo
- `avrupa_plansiz_elektrik_kesintileri_uclari_temizlenmis.xlsx`: Temizlenmiş veri seti
- `rf_log_model.pkl`: 90-10 bölme ile eğitilmiş Random Forest + Log modeli
- `model_metrics.json`: 90-10 model değerlendirme metrikleri
- `requirements.txt`: Gerekli Python paketleri

## Yerel Bilgisayarda Çalıştırma

Klasörü açıp terminalde şunları çalıştırın:

```bash
pip install -r requirements.txt
streamlit run app.py
```

Uygulama açıldıktan sonra tarayıcıda genellikle şu adreste görünür:

```text
http://localhost:8501
```

## Google Colab'de Çalıştırma

Zip dosyasını Colab'e yükleyin. Sonra şu hücreleri sırasıyla çalıştırın:

```python
!rm -rf bedas_app
!unzip -o ck_enerji_rf_log_webapp_90_10.zip -d bedas_app
%cd /content/bedas_app/bedas_rf_log_webapp
!pip install -r requirements.txt
```

Ardından Streamlit'i başlatmak için:

```python
!npm install -g localtunnel
!streamlit run app.py & npx localtunnel --port 8501
```

Colab size `loca.lt` uzantılı bir URL verecektir. O URL üzerinden web uygulamasını açabilirsiniz.

Localtunnel şifre isterse şunu çalıştırın:

```python
!curl ipv4.icanhazip.com
```

Çıkan IP adresini şifre olarak girin.
