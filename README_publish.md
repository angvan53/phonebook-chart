# 📦 Helm Chart Yayınlama Rehberi (GitHub Pages üzerinden)

Bu rehberde, Helm chart'ınızı GitHub Pages üzerinden nasıl yayınlayacağınızı adım adım açıklıyoruz.

---

## 📁 1. Helm Chart Paketleme

```bash
helm package phonebook
```

Bu işlem sonunda şu dosya oluşur:
```
phonebook-0.1.0.tgz
```

---

## 🗂️ 2. index.yaml Oluşturma

```bash
helm repo index . --url https://angvan53.github.io/phonebook-chart/
```

Bu komut, bulunduğunuz dizine `index.yaml` dosyasını ekler.

---

## 🧬 3. Git Başlat ve Dosyaları Push Et

```bash
git init
git add README.md phonebook-0.1.0.tgz index.yaml
git commit -m "Helm chart ve index dosyası eklendi"
git remote add origin https://github.com/angvan53/phonebook-chart.git
git branch -M main
git push -u origin main
```

---

## 🌐 4. GitHub Pages Ayarları

1. GitHub repo → **Settings** → **Pages**
2. `Branch: main` ve `Folder: /(root)` seç
3. **Save** butonuna bas

---

## 🚀 5. Repo Erişimini Test Et

```bash
helm repo add phonebook-repo https://angvan53.github.io/phonebook-chart/
helm repo update
helm install phonebook-release phonebook-repo/phonebook
```

Alternatif olarak:

```bash
curl https://angvan53.github.io/phonebook-chart/index.yaml
```

200 OK ve YAML içeriği görüyorsanız her şey başarıyla çalışıyor ✅

---

## ✅ Özet

| Adım | Açıklama                           |
|------|------------------------------------|
| 1    | Helm chart'ı paketle `.tgz` oluştur |
| 2    | `index.yaml` üret `--url` ile      |
| 3    | Dosyaları GitHub'a push et         |
| 4    | GitHub Pages'i aktif et            |
| 5    | Helm üzerinden kurulumu test et    |

---

**Hazırlayan:** angvan53  
**Tarih:** 2025-07-23  
