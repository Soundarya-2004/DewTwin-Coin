# DewTwin-Coin
### An Autonomous Framework for Lunar Water-Ice Prospecting using Chandrayaan-3 LIBS and ChaSTE Observations

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Overview

**DewTwin-Coin** is a lightweight, rule-based framework for onboard lunar water-ice prospecting. It fuses data from the Chandrayaan-3 **LIBS** instrument on Pragyan rover and **ChaSTE** instrument on Vikram lander to make autonomous drill/no-drill decisions without ground intervention.

This framework was developed and validated on 3,165 publicly available LIBS spectra and 387 ChaSTE temperature readings from the Chandrayaan-3 Vikram landing site.

**Key Finding**: At the recorded surface temperature of 271.4 K and max H/O ratio of 1.786, the framework correctly reported zero water-ice detections. This validates that the logic will avoid false-positive drilling commands in warm terrain, a necessary step for Chandrayaan-4 autonomy.

---

## Repository Structure
DewTwin-Coin/
├── DewTwin_Coin_Paper.pdf          # Preprint of the paper
├── process_libs_chaste.py          # Main processing and classification script
├── requirements.txt                # Python dependencies
├── Fig1_DewTwin_Coin_Ch3.png       # Simulated rover traversal path
├── README.md                       # This file
└── LICENSE                         # MIT License

---

## Methodology

The core decision rule is:
$$ 
\text{Drill} = \text{True} \quad \text{if} \quad T < 110 \text{ K} \; \text{and} \; 1.7 < \frac{I_H}{I_O} < 2.3 
$$
Where:
- `T` = Surface temperature from ChaSTE
- `I_H` = Hydrogen line intensity at 656.3 nm from LIBS  
- `I_O` = Oxygen line intensity at 777.4 nm from LIBS

The framework also includes a 1D random-walk model to simulate rover coverage for visualization.

---

## Results Summary

| Metric | Value |
| --- | --- |
| Total LIBS Observations | 3,165 |
| ChaSTE Surface Temperature | 271.4 K |
| Max H/O Ratio Observed | 1.786 |
| Sites Classified as Water-Ice | 0 |
| False Positives | 0 |

A hypothetical validation case at 95.0 K and H/O = 2.05 is included to demonstrate positive detection logic.

---

## Data Availability

All raw data used in this study are publicly available from the ISRO PRADAN Archive:  
https://pradan.issdc.gov.in

- **LIBS Data**: Pragyan Rover, Level-2 products, Sol 1-10
- **ChaSTE Data**: Vikram Lander, Level-2 products

---

## Installation and Usage

1.  Clone the repository
```bash
git clone https://github.com/yourusername/DewTwin-Coin.git
cd DewTwin-Coin
CitationIf you use this code or data in your research, please cite:
@article{soundarya2026dewtwin,
  title={DewTwin-Coin: An Autonomous Framework for Lunar Water-Ice Prospecting using Chandrayaan-3 LIBS and ChaSTE Observations},
  author={Soundarya, R.},
  journal={arXiv preprint},
  year={2026}
AcknowledgmentsI thank the Indian Space Research Organisation (ISRO) and the PRADAN team for making Chandrayaan-3 data publicly accessible.
This work was carried out as part of an undergraduate project at The Oxford College of Engineering, Bengaluru.Author: Soundarya R.
Email: soundaryaramachandra2003@gmail.com
Affiliation: Department of Computer Science and Engineering, The Oxford College of Engineering
MIT License

Copyright (c) 2026 Soundarya R

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
