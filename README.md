# 🏥 Federated Learning for Privacy-Preserving Healthcare AI

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Google Colab](https://img.shields.io/badge/Google-Colab-orange.svg)

## 📌 Project Overview

**Problem:** Hospitals cannot share patient data due to privacy laws (HIPAA, GDPR). How can multiple hospitals collaboratively train AI models without sharing sensitive medical images?

**Solution:** This project implements 5 different Federated Learning (FL) approaches enabling hospitals to train shared models while keeping patient data completely private.

**Best Result:** Ensemble FL achieves **79.33% accuracy** on pneumonia detection - outperforming individual methods by 1.45%.

---

## 🏆 Key Results

| Rank | Method | Test Accuracy | Privacy | Training Accuracy |
|------|--------|---------------|---------|-------------------|
| 🥇 | **Ensemble FL (EFL)** | **79.33%** | ✅ Yes | 98% |
| 🥈 | Horizontal FL (HFL) | 77.88% | ✅ Yes | 97% |
| 🥉 | Centralized (Baseline) | 77.72% | ❌ No | 97% |
| 4th | Transfer FL (TFL) | 75.96% | ✅ Yes | 98% |
| 5th | Vertical FL (VFL) | 62.98% | ✅ Yes | 90% |

### Key Findings
- ✅ Ensemble FL improves accuracy by **+1.45%** over best individual method
- ✅ Horizontal FL achieves **97% of baseline accuracy** with FULL privacy
- ✅ 20% generalization gap (97% train → 77% test) - normal for medical imaging

---

## 🧠 FL Methods Explained

### 1. Horizontal FL (HFL)
**Different patients, same features across hospitals**

3 hospitals with different sick ratios (63%, 72%, 81%) train locally and share only model updates. Result: 77.88% accuracy with full privacy.

### 2. Vertical FL (VFL)
**Same patients, different features**

Hospital A sees TOP half of X-ray, Hospital B sees BOTTOM half. Neither sees full image! Result: 62.98% accuracy (harder task).

### 3. Transfer FL (TFL)
**Pre-train on source hospitals, fine-tune on target**

Hospitals A+B train first, then transfer knowledge to Hospital C. Result: 75.96% accuracy.

### 4. Ensemble FL (EFL) - BEST 🏆
**Combine all methods using Weighted Soft Voting**

HFL + VFL + TFL with weights [0.34, 0.33, 0.33] = 79.33% accuracy!

---

