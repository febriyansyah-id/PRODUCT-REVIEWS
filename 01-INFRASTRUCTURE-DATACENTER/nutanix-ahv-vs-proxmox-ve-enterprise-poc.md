# Nutanix AHV vs Proxmox VE — Enterprise HCI & Virtualization POC

[![Category](https://img.shields.io/badge/Category-Datacenter%20%26%20HCI-blue)](#)
[![Evaluator](https://img.shields.io/badge/Evaluator-Febriyansyah-0ea5e9)](#)
[![Score](https://img.shields.io/badge/Overall%20Score-9.4%20%2F%2010-brightgreen)](#)
[![POC](https://img.shields.io/badge/POC%20Status-Verified%20%26%20Passed-success)](#)

---

## 🎯 1. Executive Summary

- **Primary Focus:** Evaluasi komparatif antara Hyper-Converged Infrastructure (HCI) komersial (**Nutanix Cloud Platform / AHV**) dengan solusi KVM Virtualization terdistribusi open-source (**Proxmox VE + Ceph Storage**).
- **Konteks Implementasi:** Kebutuhan modernisasi virtualisasi perbankan menghadapi kenaikan biaya lisensi VMware pasca akuisisi Broadcom.
- **Hasil POC Singkat:** Nutanix AHV unggul mutlak dalam automasi lifecycle, dukungan enterprise SLA 24/7, dan integrasi micro-segmentation bawaan (*Nutanix Flow*). Proxmox VE terbukti sangat tangguh dan stabil untuk cluster non-critical, development, dan disaster recovery (DR) dengan penghematan TCO hingga 70%.

---

## 🏗️ 2. Topologi & Arsitektur Pengujian POC

```text
[ Nutanix AHV 3-Node Cluster ]           [ Proxmox VE + Ceph 3-Node Cluster ]
  ├── Node 1: Supermicro / Intel Xeon        ├── Node 1: Supermicro / Intel Xeon
  ├── Node 2: Supermicro / Intel Xeon        ├── Node 2: Supermicro / Intel Xeon
  └── Node 3: Supermicro / Intel Xeon        └── Node 3: Supermicro / Intel Xeon
  └── Dual 25GbE Uplinks (LACP)              └── Dual 25GbE Uplinks (LACP)
  └── Distributed Storage Fabric (DSF)       └── Ceph OSD Pool (NVMe All-Flash)
```

---

## 📊 3. Matriks Komparasi Teknis

| Kriteria Pengujian | Nutanix AHV Enterprise | Proxmox VE + Ceph (Open Source) | Pemenang POC |
| :--- | :--- | :--- | :---: |
| **High Availability (HA) Failover** | Otomatis restart VM < 15 detik via Acropolis | Otomatis restart VM ~18-20 detik via Corosync/pve-ha | **Nutanix** |
| **Penyimpanan Terdistribusi** | Nutanix DSF (RF2/RF3, Data Locality) | Ceph Bluestore OSD (CRUSH Map, Replica 3) | **Nutanix** (Data Locality) |
| **Manajemen Terpusat** | Prism Central (Multi-cluster, HTML5) | Proxmox Cluster Manager (Web GUI bawaan) | **Nutanix** |
| **Live Migration VM** | Zero packet drop, buffer transfer mulus | Zero packet drop via KVM live migration | **Seri (Tie)** |
| **Backup & Snapshot** | Protection Domains, NearSync, Metro Availability | Proxmox Backup Server (PBS) Deduplikasi Cepat | **Proxmox** (PBS sangat efisien) |
| **Total Biaya Kepemilikan (TCO)** | Model langganan tahunan per-core (Enterprise) | Bebas lisensi per-core (Subscription support opsional) | **Proxmox** (Sangat hemat) |

---

## 💡 4. Rekomendasi Presales & Implementasi

1. **Mission-Critical Core Banking & Production DB**: Gunakan **Nutanix AHV**. Jaminan audit regulator (OJK/BI), dukungan vendor 24/7 dengan MTTR ketat, serta fitur *Flow Network Security* (micro-segmentation) memitigasi risiko keamanan lateral.
2. **Branch Office, Staging, DR & DevOps Infrastructure**: Gunakan **Proxmox VE + PBS**. Menghilangkan biaya lisensi tahunan yang mahal tanpa mengorbankan kestabilan performa KVM dan penyimpanan Ceph.
