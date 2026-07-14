# Greater Radiative Efficiency of Indian Anthropogenic CO₂ Relative to China in the Early Transport Stage

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Journal: Atmosphere (MDPI)](https://img.shields.io/badge/Journal-Atmosphere%20(MDPI)-blue.svg)](https://www.mdpi.com/journal/atmosphere)

**Authors:** Zhiyin Zou<sup>1,2</sup>, Zhe Wang<sup>1,*</sup>, Xueshun Chen<sup>1</sup>, Wending Wang<sup>3</sup>, Huansheng Chen<sup>1</sup>, Zijian Jiang<sup>1,2</sup>, Zifa Wang<sup>1,2,3,*</sup>

<sup>1</sup> State Key Laboratory of Atmospheric Environment and Extreme Meteorology, Institute of Atmospheric Physics, Chinese Academy of Sciences, Beijing 100029, China  
<sup>2</sup> College of Earth and Planetary Sciences, University of Chinese Academy of Sciences, Beijing 100049, China  
<sup>3</sup> Laboratory of Atmospheric Boundary Layer, Institute of Atmospheric Physics, Chinese Academy of Sciences, Beijing 100029, China  

---

## 📖 Overview

This repository contains the dataset and analysis scripts supporting the paper:

> **"Greater Radiative Efficiency of Indian Anthropogenic CO₂ Relative to China in the Early Transport Stage"**


### Key Findings

Past research on CO₂ greenhouse effects has mostly relied on the **globally uniform mixing assumption**, which neglects the spatial heterogeneity of CO₂ radiative effects during the non-uniform distribution stage. This study focuses on fossil fuel combustion emissions from **China and India** in 2010, employing:

- **WRF-ARW (v3.9.1.1)** for global meteorological field simulation
- **IAP-AACM** with online source-tagging for CO₂ transport and source attribution
- **libRadtran (v2.0.6)** for offline longwave radiative transfer calculation

**Headline Results:**
- Global annual mean **Radiative Efficiency (RE)** in 2010: **China = 3.15 mW/m2/GtC**, **India = 3.46 mW/m2/GtC**
- India's RE exceeds China's by **~9.8%**
- India's maximum local annual mean RE (~10.0 mW/m2/GtC) is approximately **1.8×** that of China (~5.5 mW/m2/GtC)
- The RE difference is driven by: warmer underlying surface temperature, colder upper-air transport, and lower cloud water path along India's CO₂ transport pathway — these three factors overcome the stronger water vapor masking effect

---

## 📁 Repository Structure

```
.
├── README.md                          # This file
├── LICENSE                            # CC BY 4.0
├── .gitignore                         # Git ignore rules
├── data/
│   ├── Fig1_2_Country_xco2_mon.nc           # Monthly XCO₂ distributions (China & India)
│   ├── Fig3_CVw_daily_data.nc               # Daily CVw (mass-weighted coefficient of variation)
│   ├── Fig4_Vertical_Mass_monthly_mesh.nc   # Monthly vertical mass distribution
│   ├── Fig5_Radiative_Efficiency_2010.nc    # Annual mean TOA radiative efficiency (2010)
│   └── Fig6_moteo_Means_monthly.nc          # Monthly mass-weighted meteorological factors
└── figures/                          # (Optional) Figure outputs
```

---

## 📊 Data Description

All data are provided in **NetCDF (.nc)** format. Each file corresponds to a figure in the manuscript.

### Fig1_2_Country_xco2_mon.nc
Column-averaged dry-air mole fraction of CO₂ (XCO₂) contributed by China and India fossil fuel emissions.

| Dimension | Description |
|-----------|-------------|
| `lon` | Longitude (1° × 1°) |
| `lat` | Latitude (1° × 1°) |
| `time` | Monthly (2010–2012) |
| Variables | `xco2_china`, `xco2_india` (units: ppm) |

### Fig3_CVw_daily_data.nc
Mass-weighted coefficient of variation (CV) — quantifies the spatial uniformity of CO₂ mixing globally on a daily basis.

| Dimension | Description |
|-----------|-------------|
| `time` | Daily (2010–2012) |
| Variables | `cv_china`, `cv_india` (dimensionless) |

### Fig4_Vertical_Mass_monthly_mesh.nc
Vertical mass distribution (mass fraction per layer) of CO₂ emitted from China and India.

| Dimension | Description |
|-----------|-------------|
| `level` | Vertical layers (three categories: LT/MT/UT) |
| `time` | Monthly |
| Variables | `mass_frac_china`, `mass_frac_india` (units: %) |

### Fig5_Radiative_Efficiency_2010.nc
Annual mean TOA longwave radiative effect efficiency (RE) for China and India CO₂ emissions in 2010.

| Dimension | Description |
|-----------|-------------|
| `lon` | Longitude (1° × 1°) |
| `lat` | Latitude (1° × 1°) |
| Variables | `re_china`, `re_india` (units: mW/m2/GtC) |

### Fig6_moteo_Means_monthly.nc
Mass-weighted annual mean meteorological factors along CO₂ transport pathways.

| Variable | Description | Unit |
|----------|-------------|------|
| `tsk_china` / `tsk_india` | Surface skin temperature | °C |
| `t_china` / `t_india` | Air temperature | °C |
| `pw_china` / `pw_india` | Precipitable water vapor | kg m⁻² |
| `cwp_china` / `cwp_india` | Cloud water path | g m⁻² |

---

## 🛠 Model Chain

```
[WRF-ARW v3.9.1.1]           [IAP-AACM + Source Tagging]        [libRadtran v2.0.6]
 Meteorological         →     CO₂ Transport & Source       →     Longwave Radiative
 Field Simulation              Attribution                        Transfer Calculation
 (1° × 1°, global)            (China/India tagging)             (REPTRAN medium, DISORT)
```

- **Emission scenario:** 2010 fossil fuel CO₂ (China & India), 2011–2012 emission-free mixing phase
- **Initial/Boundary CO₂:** CarbonTracker CT2022 (NOAA)
- **Key radiative scheme:** REPTRAN medium resolution; DISORT 4-stream solver; thermal IR band 3–100 µm

---

## 📝 Citation

If you use this dataset in your research, please cite:

```bibtex
@article{zou202xgreater,
  title     = {Greater Radiative Efficiency of Indian Anthropogenic CO₂ Relative to China in the Early Transport Stage},
  author    = {Zou, Zhiyin and Wang, Zhe and Chen, Xueshun and Wang, Wending and Chen, Huansheng and Jiang, Zijian and Wang, Zifa},
  journal   = {Atmosphere},
  year      = {202x},
  publisher = {MDPI},
  doi       = {10.xxxx/atmosxxxxxxx}
}
```

---

## 📬 Contact

For questions about the data or methodology, please contact:

- **Zhe Wang** — [wangzhe@mail.iap.ac.cn](mailto:wangzhe@mail.iap.ac.cn)
- **Zifa Wang** — [zifawang@mail.iap.ac.cn](mailto:zifawang@mail.iap.ac.cn)

Institute of Atmospheric Physics, Chinese Academy of Sciences, Beijing, China

---

## 📄 License

This dataset is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license, consistent with the MDPI Atmosphere open access policy.

---

<br>

# 印度人为源CO₂在早期输送阶段辐射效率高于中国

## 📖 研究概述

本研究聚焦**2010年中国和印度化石燃料燃烧排放CO₂**，利用在线源标记技术获取两国CO₂浓度贡献，结合辐射传输模型计算不同情景下的辐射效率（RE），定量比较非均匀分布阶段两国CO₂排放RE差异，并从关键气象要素角度探讨差异成因。

### 核心发现

- 2010年全球年均RE：中国 **3.15 mW/m2/GtC**，印度 **3.46 mW/m2/GtC**，印度高出约 **9.8%**
- 局地最大年均RE：印度（~10.0 mW/m2/GtC）约为中国（~5.5 mW/m2/GtC）的 **1.8 倍**
- 印度排放CO₂覆盖更高地表温度区域，且被深对流输送至更冷的高层大气，输送路径上云水含量较低——这三个因素共同超过了水汽掩蔽效应的抑制作用，导致印度RE更高
- 研究证明：**均匀混合假设在短时间尺度上存在局限**，CO₂非均匀分布阶段的RE强度和空间格局受源区地理位置和三维输送路径共同控制

---

## 📊 数据文件说明

| 文件 | 内容 | 时空分辨率 |
|------|------|-----------|
| `Fig1_2_Country_xco2_mon.nc` | 中印CO₂贡献的XCO₂分布 | 1°×1°, 月均 |
| `Fig3_CVw_daily_data.nc` | 质量加权变异系数CVw | 全球, 日均 |
| `Fig4_Vertical_Mass_monthly_mesh.nc` | CO₂垂直质量分布 | 月均 |
| `Fig5_Radiative_Efficiency_2010.nc` | 2010年TOA辐射效率 | 1°×1°, 年均 |
| `Fig6_moteo_Means_monthly.nc` | 输送路径质量加权气象因子 | 月均 |

---

## 🛠 技术链

WRF-ARW (v3.9.1.1) → IAP-AACM + 在线源标记 → libRadtran (v2.0.6)，1°×1°全球配置。

---

## 📝 引用与联系

数据使用请引用对应论文。联系邮箱：wangzhe@mail.iap.ac.cn / zifawang@mail.iap.ac.cn
