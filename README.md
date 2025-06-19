# 🚀 DevOps Project: CI/CD + Monitoring on Azure Kubernetes Service (AKS)

Proyek ini menunjukkan implementasi pipeline CI/CD menggunakan **Azure DevOps** untuk deploy aplikasi container ke **Azure Kubernetes Service (AKS)** dan monitoring dengan **Prometheus** serta **Azure Log Analytics**.

---

## 🗂️ Teknologi yang Digunakan

| Komponen           | Teknologi                             |
|--------------------|---------------------------------------|
| CI/CD              | Azure DevOps Pipelines                |
| Containerization   | Docker                                |
| Container Registry | Azure Container Registry (ACR)        |
| Orchestration      | Azure Kubernetes Service (AKS)        |
| Monitoring         | Prometheus, Azure Log Analytics Azure |
| Agent Build        | Self-Hosted Agent VM Azure            |
 
---

## 🧱 Struktur Project

├── azure-pipelines.yml # Pipeline CI/CD utama
├── deployment.yaml # Konfigurasi deployment app ke AKS
└── service.yaml # Konfigurasi akses LoadBalancer
├── prometheus-deployment.yaml
└── grafana-deployment.yaml
├── README.md # Dokumentasi ini


---

## ⚙️ Alur CI/CD

1. **Commit ke GitHub** → trigger pipeline Azure DevOps
2. **Build Docker image** dari source code
3. **Push image** ke Azure Container Registry (ACR)
4. **Deploy image** ke AKS
5. **Expose aplikasi** via LoadBalancer
6. **Monitor aplikasi** dengan Prometheus & Log Analytics

---

## 🔍 Monitoring

- **Prometheus** digunakan untuk scraping metrics dari pod.
- **Azure Log Analytics** untuk logging container & query Kusto.
- **Grafana** (opsional): UI dashboard visualisasi jika diaktifkan.

---

## 📈 Output & Hasil

| Komponen      | Status       | Keterangan                            |
|---------------|--------------|----------------------------------------|
| CI/CD         | ✅ Sukses     | Build & Deploy otomatis ke AKS        |
| Monitoring    | ✅ Aktif      | Prometheus jalan di namespace `monitoring` |
| Log Analytics | ✅ Terhubung | AKS mengirim log ke Log Analytics      |
| Akses Web     | ✅ Live       | Aplikasi dapat diakses via LoadBalancer IP |

---

## 🏁 Akses Aplikasi

Setelah pipeline berhasil, aplikasi dapat diakses melalui:

```bash
kubectl get svc -n default
Cari bagian EXTERNAL-IP dari landing-page service.