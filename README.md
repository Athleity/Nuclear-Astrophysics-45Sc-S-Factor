# Nuclear Astrophysics: ⁴⁵Sc(α,n)⁴⁸V S-Factor Analysis

[![IAPT NSSP-2025](https://img.shields.io/badge/IAPT-NSSP--2025-blue)](https://github.com/Athleity/Nuclear-Astrophysics-45Sc-S-Factor)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9+-green.svg)](https://www.python.org/)

## 📌 Overview

This repository contains a complete computational analysis of the astrophysical S-factor and thermonuclear reaction rate for the **⁴⁵Sc(α,n)⁴⁸V** reaction. The work uses experimental cross-section data from the EXFOR database and implements Python-based numerical methods to compute S-factors and reaction rates.

### Why This Matters

- The ⁴⁵Sc(α,n)⁴⁸V reaction plays a role in neutron production in stellar environments
- Understanding (α,n) reactions is crucial for modeling the slow neutron capture process (s-process) in AGB stars
- Experimental data at stellar energies is extremely difficult to obtain due to the Coulomb barrier
- Computational methods bridge the gap between higher-energy experimental data and stellar energy regimes

---

## 🔬 Key Physics

### Astrophysical S-Factor

The S-factor removes the strong energy dependence of the cross-section caused by the Coulomb barrier:

$$S(E) = E \cdot \sigma(E) \cdot e^{2\pi\eta}$$

where:
- E = center-of-mass energy (MeV)
- σ(E) = nuclear cross-section (barns)
- η = Sommerfeld parameter

### Sommerfeld Parameter

$$\eta = \frac{Z_1 Z_2 e^2}{\hbar v} = \frac{Z_1 Z_2 e^2}{\hbar} \sqrt{\frac{\mu}{2E}}$$

For the ⁴⁵Sc(α,n)⁴⁸V reaction:
- Z₁ = 2 (alpha particle)
- Z₂ = 21 (Scandium)
- Q-value = -2.241 MeV

### Error Propagation

$$\frac{\Delta S(E)}{S(E)} = \frac{\Delta\sigma(E)}{\sigma(E)}$$

---

## 📁 Repository Structure

```
Nuclear-Astrophysics-45Sc-S-Factor/
│
├── data/
│   ├── reaction_rates_45Sc.xlsx           
│   └── numerical_integration_results.xlsx 
│
├── manuscript/
│   ├── manuscript.pdf                      
│   ├── presentation.pdf                    
│   └── certificate.pdf                     
│
├── notebooks/
│   ├── 01_sfactor_error_propagation.ipynb
│   ├── 02_reaction_rate_integration.ipynb
│   ├── 03_gamow_factor_calculation.ipynb
│   ├── 04_sommerfeld_parameter.ipynb
│   ├── 05_alpha_n_reaction_analysis.ipynb
│   ├── 06_45Sc_sfactor_comparison.ipynb
│   ├── 07_gauss_legendre_integration.ipynb
│   ├── 08_reaction_rate_from_cross_section.ipynb
│   ├── 09_log_sfactor_analysis.ipynb
│   ├── 10_sfactor_kev_units.ipynb
│   ├── 11_physical_constants.ipynb
│   ├── 12_reaction_rate_plotting.ipynb
│   ├── 13_energy_cross_section_analysis.ipynb
│   ├── 14_plot_cross_section.ipynb
│   ├── 15_plot_cross_section_with_errors.ipynb
│   ├── 16_plot_sfactor_formula.ipynb
│   ├── 17_plot_sfactor_polynomial.ipynb
│   ├── 18_plot_sfactor_with_errors.ipynb
│   └── 19_plot_reaction_rates_comparison.ipynb
│
├── graphs/
│   ├── 01_cross_section_vs_energy/
│   ├── 02_reaction_rates_vs_temperature/
│   ├── 03_sfactor_formula_vs_energy/
│   ├── 04_sfactor_comparison/
│   └── 05_sfactor_polynomial_vs_energy/
│
├── README.md
└── requirements.txt
```

---

## 📊 Data Description

### reaction_rates_45Sc.xlsx

| Column | Description |
|--------|-------------|
| EN lab (MeV) | Laboratory energy |
| DATA (MB) | Cross-section in millibarns |
| eta | Sommerfeld parameter |
| S-factor (MeV·barn) | Astrophysical S-factor |
| ln(S-factor) | Natural log of S-factor |
| T9 (GK) | Stellar temperature in 10⁹ K |
| ⟨σv⟩ | Reaction rate in cm³ mol⁻¹ s⁻¹ |

### numerical_integration_results.xlsx

| Method | Points | Description |
|--------|-------|-------------|
| Trapezoidal | 50, 64, 96 | Newton-Cotes integration |
| Gauss-Legendre | 50, 64, 96 | Gaussian quadrature |

The integration evaluates:

$$\langle \sigma v \rangle = \frac{3.7313 \times 10^7}{\sqrt{\mu}} T_9^{-1.5} \int_0^{\infty} E\sigma(E) e^{-11.605E/T_9} dE$$

---

## 🛠️ Requirements

```bash
pip install numpy scipy matplotlib pandas openpyxl jupyter
```

**requirements.txt:**
```
numpy==1.24.3
scipy==1.10.1
matplotlib==3.7.1
pandas==2.0.3
openpyxl==3.1.2
jupyter==1.0.0
```

---

## 📈 Key Results

- S-factor shows smooth energy dependence suitable for extrapolation to stellar energies
- Reaction rates increase exponentially in Gamow window (T₉ = 0.1-1 GK)
- Numerical integration methods (Trapezoidal & Gauss-Legendre) show excellent agreement
- Error propagation implemented using ΔS/S = Δσ/σ

---

## 📝 Notebooks List

| # | Notebook | Description |
|---|----------|-------------|
| 01 | sfactor_error_propagation.ipynb | Propagates cross-section errors to S-factor |
| 02 | reaction_rate_integration.ipynb | Main reaction rate calculation via integration |
| 03 | gamow_factor_calculation.ipynb | Computes Gamow factor and tunneling probability |
| 04 | sommerfeld_parameter.ipynb | Calculates η for given energies |
| 05 | alpha_n_reaction_analysis.ipynb | General (α,n) reaction analysis framework |
| 06 | 45Sc_sfactor_comparison.ipynb | Compares calculated vs. literature S-factors |
| 07 | gauss_legendre_integration.ipynb | Implements Gauss-Legendre quadrature |
| 08 | reaction_rate_from_cross_section.ipynb | Rate calculation from σ(E) data |
| 09 | log_sfactor_analysis.ipynb | Analyzes ln(S) vs. E for polynomial fitting |
| 10 | sfactor_kev_units.ipynb | Converts S-factor to keV·barn units |
| 11 | physical_constants.ipynb | Reference for constants used |
| 12 | reaction_rate_plotting.ipynb | Plotting utilities for rates |
| 13 | energy_cross_section_analysis.ipynb | E-σ(E) product analysis |
| 14 | plot_cross_section.ipynb | Plots σ(E) vs energy |
| 15 | plot_cross_section_with_errors.ipynb | Plots σ(E) with error bars |
| 16 | plot_sfactor_formula.ipynb | Plots S(E) from direct calculation |
| 17 | plot_sfactor_polynomial.ipynb | Plots S(E) from polynomial fit |
| 18 | plot_sfactor_with_errors.ipynb | Plots S(E) with propagated errors |
| 19 | plot_reaction_rates_comparison.ipynb | Compares both rate calculation methods |

---

## 🚀 How to Use

```bash
git clone https://github.com/Athleity/Nuclear-Astrophysics-45Sc-S-Factor.git
cd Nuclear-Astrophysics-45Sc-S-Factor
jupyter notebook notebooks/
```

---

## 👨‍🔬 Author

**Priyansh Bhavsar**
B.S. Physics, Indian Institute of Technology Jodhpur
- GitHub: [@Athleity](https://github.com/Athleity)

## 🙏 Supervisor

**Dr. N. J. Upadhyay**
Assistant Professor (III), Amity University Maharashtra

---

## 📚 Presentation

This work was presented at the **12th IAPT National Students' Symposium on Physics (NSSP-2025)**

| Detail | Information |
|--------|-------------|
| Dates | October 10-12, 2025 |
| Venue | Department of Physics, Panjab University, Chandigarh |
| Type | Oral/Poster Presentation |

---
---
## 📖 Citation

```bibtex
@inproceedings{bhavsar2025astrophysical,
  title={A Computational Analysis of Experimental Nuclear Reaction Data},
  author={Bhavsar, Priyansh and Upadhyay, N.J.},
  booktitle={12th IAPT National Students' Symposium on Physics (NSSP-2025)},
  year={2025},
  organization={Panjab University, Chandigarh}
}

⭐ If you find this work useful, please consider starring the repository!

**Made with ❤️ for Nuclear Astrophysics Research**
