# Fortinet FortiGate vs Palo Alto Networks — Enterprise NGFW POC

[![Category](https://img.shields.io/badge/Category-Cybersecurity%20%26%20NGFW-red)](#)
[![Evaluator](https://img.shields.io/badge/Evaluator-Febriyansyah-0ea5e9)](#)
[![Score](https://img.shields.io/badge/Overall%20Score-9.6%20%2F%2010-brightgreen)](#)
[![Compliance](https://img.shields.io/badge/Compliance-OJK%20%7C%20PCI--DSS-purple)](#)

---

## 🎯 1. Executive Summary

- **Primary Focus:** Evaluasi perbandingan dua pemimpin pasar Next-Generation Firewall (NGFW): **Fortinet FortiGate (FortiOS 7.4 + ASIC SPU)** vs **Palo Alto Networks (PAN-OS 11 + Single-Pass Parallel Processing)**.
- **Kasus Penggunaan:** Perlindungan perimeter Data Center perbankan, inspeksi mendalam lalu lintas terenkripsi (TLS 1.3 / SSL Decryption), dan mitigasi ancaman Zero-Day via Sandboxing.
- **Hasil Ringkasan POC:** Fortinet FortiGate menawarkan performa throughput inspeksi SSL dan harga per-Gbps terbaik di kelasnya berkat akselerasi hardware ASIC (*Security Processing Unit*). Di sisi lain, Palo Alto Networks memberikan akurasi identifikasi aplikasi Layer-7 (*App-ID*) dan inteligensi ancaman Zero-Day (*WildFire*) yang paling komprehensif dan minim false-positive.

---

## 🏗️ 2. Topologi Pengujian Keamanan

```text
               [ Internet / WAN Inbound ]
                           │
      ┌────────────────────┴────────────────────┐
      ▼                                         ▼
[ FortiGate 600F Cluster ]            [ Palo Alto PA-3420 Cluster ]
  ├── Active/Passive HA                 ├── Active/Passive HA
  ├── SP5 ASIC Acceleration             ├── Single-Pass Architecture (SP3)
  ├── FortiGuard AI/ML Threat           ├── Advanced WildFire Sandboxing
  └── Deep SSL Inspection (TLS 1.3)     └── Advanced Threat Prevention
      │                                         │
      └────────────────────┬────────────────────┘
                           ▼
           [ Enterprise Banking Core Network ]
```

---

## 📊 3. Matriks Evaluasi & Benchmarks

| Kategori Pengujian | Fortinet FortiGate | Palo Alto Networks | Skor Unggul |
| :--- | :--- | :--- | :---: |
| **Throughput Deep SSL Inspection** | Sangat Tinggi (didukung chip ASIC CP9/SP5) | Tinggi (CPU-based Single-Pass architecture) | **Fortinet** |
| **Akurasi App-ID & Layer-7** | Sangat Baik (Signature & Heuristic) | Standar Emas Industri (Patented App-ID & Content-ID) | **Palo Alto** |
| **Deteksi Zero-Day & Sandbox** | FortiSandbox (Cloud / On-Premise appliance) | WildFire Real-Time inline machine learning | **Palo Alto** |
| **Manajemen Terpusat** | FortiManager (Terintegrasi ke FortiAnalyzer) | Panorama (Sangat stabil untuk ribuan firewall) | **Seri (Tie)** |
| **Biaya Hardware & Lisensi (TCO)** | Sangat Kompetitif (Rasio ROI tinggi) | Premium (Investasi awal dan tahunan tinggi) | **Fortinet** |

---

## 💡 4. Rekomendasi Presales & Arsitektur

1. **Datacenter Edge dengan Volume Lalu Lintas Sangat Besar**: FortiGate 600F/1000F adalah opsi terbaik dari segi efisiensi daya, throughput inspeksi SSL terenkripsi, dan rasio biaya per gigabit.
2. **Kepatuhan Regulasi Finansial Tertinggi (Core Ingress / Payment Gateway)**: Palo Alto Networks PA-3400/4400 memberikan keyakinan tertinggi bagi CISO dan auditor perbankan dalam mencegah serangan bertarget tingkat lanjut (*Advanced Persistent Threats*).
