# Cisco Catalyst 9300 vs Aruba CX 6300 — Campus & Core Switching POC

[![Category](https://img.shields.io/badge/Category-Network%20%26%20Switching-indigo)](#)
[![Evaluator](https://img.shields.io/badge/Evaluator-Febriyansyah-0ea5e9)](#)
[![Score](https://img.shields.io/badge/Overall%20Score-9.2%20%2F%2010-brightgreen)](#)
[![POC](https://img.shields.io/badge/POC%20Status-Verified%20%26%20Passed-success)](#)

---

## 🎯 1. Executive Summary

- **Primary Focus:** Komparasi mendalam antara switch access/aggregation enterprise unggulan: **Cisco Catalyst 9300 Series (IOS-XE)** vs **Aruba CX 6300 Series (AOS-CX)**.
- **Kebutuhan Enterprise:** Penyediaan infrastruktur jaringan kampus/kantor pusat bank dengan dukungan 90W PoE (UPOE+/Class 8), penanganan segmentasi jaringan dinamis (EVPN-VXLAN), dan otomasi berbasis API.
- **Hasil Evaluasi Singkat:** Cisco Catalyst 9300 tetap menjadi standar industri untuk ekosistem Cisco DNA/Catalyst Center dan densitas daya tinggi. Namun, Aruba CX 6300 menawarkan arsitektur modern berbasis microservices database (*AOS-CX State Database*), engine analitik bawaan (*NAE - Network Analytics Engine*), dan fleksibilitas integrasi Python REST API tanpa lisensi berulang yang agresif.

---

## 🏗️ 2. Arsitektur Pengujian

```text
[ Core Aggregation Spine: 2x 100GbE ]
          │                    │
    (LACP Port-Channel)  (LACP Port-Channel)
          │                    │
[ Access Stack A: Cisco C9300-48UXM ]   [ Access Stack B: Aruba CX 6300M 48SR5 ]
  ├── StackWise-480 (480 Gbps fabric)     ├── VSF Stacking (200 Gbps fabric)
  ├── 90W UPOE+ Ports (Wi-Fi 6E APs)      ├── 60W Class 6 PoE Ports
  └── DNA Center Telemetry                └── NAE Analytics + Aruba Central
```

---

## 📊 3. Matriks Evaluasi Fitur & Performa

| Kriteria Pengujian | Cisco Catalyst 9300 | Aruba CX 6300 | Skor Unggul |
| :--- | :--- | :--- | :---: |
| **Stacking Throughput** | StackWise-480 (480 Gbps dedicated ring) | VSF (Front-panel 50G/100G uplinks, hingga 200 Gbps) | **Cisco** |
| **Otomasi & Programabilitas** | NETCONF/YANG, Python on-box, RESTCONF | Full REST API ke State DB, Python on-box, NAE | **Aruba** |
| **Dukungan PoE Budget** | 90W Cisco UPOE+ per port (Class 8 ready) | 60W Class 6 Smart Rate per port | **Cisco** |
| **Segmentasi Dinamis** | Cisco TrustSec (SGT) & Software-Defined Access | Aruba Dynamic Segmentation & EVPN-VXLAN | **Seri (Tie)** |
| **Model Lisensi Operasional** | Wajib Cisco DNA Spaces Subscription (3/5/7 thn) | Lisensi terpadu (Aruba Central opsional, API bebas) | **Aruba** |

---

## 💡 4. Rekomendasi Arsitektur Presales

- **Gunakan Cisco Catalyst 9300** jika organisasi Anda telah berinvestasi besar pada *Cisco ISE (Identity Services Engine)*, Cisco DNA Center, atau membutuhkan PoE 90W untuk IoT LED Lighting dan kamera PTZ berdaya tinggi.
- **Gunakan Aruba CX 6300** jika Anda memprioritaskan otomatisasi infrastruktur modern berbasis CI/CD pipeline, monitoring proaktif tanpa software tambahan (*Network Analytics Engine*), serta pengendalian biaya lisensi tahunan.
