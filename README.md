# Research_VPPC2026

**A Survey of AI-Based Methods for SiC MOSFET Management in Automotive Traction Inverters**

Mahdi Mounzer — INSA Strasbourg, Génie Électrique
Prepared for the **IEEE Vehicle Power and Propulsion Conference (VPPC) 2026**, Special Session 6.

📄 [Read the paper (PDF)](paper/VPPC2026_SiC_AI_Survey.pdf)

---

## Abstract

Silicon Carbide (SiC) MOSFETs have become the device of choice for electric vehicle traction inverters, offering higher switching frequencies, lower conduction losses and better thermal performance than Si-IGBTs. However, the higher power density and highly dynamic thermal loading of real drive cycles make junction temperature (T<sub>j</sub>) management a critical, unsolved reliability challenge. Direct T<sub>j</sub> measurement inside packaged modules is impractical, and classical electro-thermal models cannot account for the nonlinear dependence of thermo-sensitive electrical parameters on load current, gate voltage and device aging at the same time.

This paper surveys the state of the art in AI-based methods for three core problems: **real-time T<sub>j</sub> estimation**, **aging and remaining useful life (RUL) prediction**, and **thermally-aware closed-loop control**. It reviews neural network surrogates, digital twins with NTC synchronisation, condition monitoring via body diode voltage, and equivalent gate resistance controllers. The reviewed results show T<sub>j</sub> estimation errors below 3.5 %, independent tracking of gate oxide and packaging degradation, and lifetime extensions of more than 2× under dynamic load. The survey identifies the lack of a unified, aging-aware, real-time deployable framework as the main open research gap.

**Keywords:** SiC MOSFET · traction inverter · junction temperature · artificial intelligence · neural network · digital twin · condition monitoring · remaining useful life · active thermal control · electric vehicles

---

## Paper structure

| Section | Topic | Key methods reviewed |
|---|---|---|
| I | Introduction | SiC vs Si-IGBT, 800 V platforms, the three management problems |
| II | Junction temperature estimation | Electro-thermal models, NTC thermistors, TSEPs (R<sub>ds,on</sub>, V<sub>gs,th</sub>), 4H-SiC PN-diode sensor; **ANN surrogate trained on CFD + ROM data** [4]; **FEM-trained neural-network digital twin with NTC synchronisation** [5] |
| III | Aging & RUL prediction | Gate oxide vs package degradation, PoF lifetime models (Bayerer/CIPS 2008, LESIT), rainflow counting; **body-diode voltage (V<sub>SD</sub>) condition monitoring at 0 V / −5 V gate bias** [3]; hybrid PoF + ML RUL [6] |
| IV | Thermally-aware real-time control | Switching-frequency and gate-resistance control; **Equivalent Gate Resistance Control (EGRC)** with TCOS/JTCC [8]; T<sub>j</sub>-based PWM hysteresis control [6]; digital-twin predictive control [5] |
| V | Conclusion | Open challenges and the integration gap |

## Key findings

| Problem | Result from the reviewed literature |
|---|---|
| T<sub>j</sub> estimation | ANN surrogate: < 3.5 % error, inference ≈ 1 s instead of 150 min of CFD [4] |
| Full 3-D thermal map | NN digital twin estimates all 10 junction temperatures of a Wolfspeed module in 0.063 s [5] |
| Degradation tracking | Gate oxide and packaging degradation tracked independently from a single parameter (V<sub>SD</sub>) [3] |
| Active thermal control | T<sub>j</sub> fluctuation reduced from 18.83 °C to 9.85 °C → estimated lifetime × 2.18 [8] |

**Open gap:** most AI models are validated in the lab or in simulation rather than on real drive cycles, SiC field-aging data is still scarce, and no framework yet combines T<sub>j</sub> estimation, RUL prediction and thermal control in one deployable system.

---

## Repository contents

```
Research_VPPC2026/
├── paper/
│   ├── VPPC2026_SiC_AI_Survey.pdf     # Final paper (4 pages, IEEE conference format)
│   ├── VPPC2026_SiC_AI_Survey.docx    # Editable source of the paper
│   └── Final Digest.docx              # Final digest version submitted to VPPC
├── notes/
│   ├── Pre research info 1.docx       # Background notes: EV powertrain, inverters, Si vs SiC, Tj
│   ├── Pre Research info 2.docx       # SiC challenges in EVs, thermal focus, abstract drafts
│   └── Draft for digest.docx          # Digest working draft
└── template/
    └── conference-template-letter.docx  # IEEE conference template (US letter)
```

## References

1. B. Shi, A. I. Ramones, Y. Liu, H. Wang, Y. Li, S. Pischinger and J. Andert, "A review of silicon carbide MOSFETs in electrified vehicles: Application, challenges, and future development," *IET Power Electronics*, vol. 16, no. 12, pp. 2103–2120, 2023.
2. S. Mocevic, V. Mitrovic, J. Wang, R. Burgos and D. Boroyevich, "Gate-driver integrated junction temperature estimation of SiC MOSFET modules," *IEEE JESTPE*, 2021.
3. E. Ugur, C. Xu, F. Yang, S. Pu and B. Akin, "A new complete condition monitoring method for SiC power MOSFETs," *IEEE Trans. Industrial Electronics*, 2020.
4. G. Egin Martin, B. Verbrugge, M. M. Hasan, M. El Baghdadi, C. Romano and O. Hegazy, "Artificial intelligence-driven thermal management in electric vehicle traction inverters: Cooling system optimization and real-time temperature prediction," *IEEE Access*, vol. 13, 2025.
5. K. B. Troldborg, S. I. Skov, A. Fathollahi and J. H. Pedersen, "Advanced machine learning approach for fast temperature estimation in SiC-based power electronics converters," *Electronics*, vol. 15, no. 6, p. 1325, 2026.
6. A. Y. Amare, "Active thermal control of SiC MOSFET power converters," M.Sc. thesis, Chalmers University of Technology, Gothenburg, Sweden, 2024.
7. N. Zhang and A. P. Pisano, "Harsh environment temperature sensor based on 4H-silicon carbide PN diode," in *Proc. Transducers*, Barcelona, Spain, pp. 1016–1019, Jun. 2013.
8. Q. Zhang and P. Zhang, "A novel active temperature management strategy for SiC MOSFETs," preprint, SSRN, doi: [10.2139/ssrn.4888608](https://doi.org/10.2139/ssrn.4888608).
9. J. Fu, Y. Li and Z. Zheng, "Overview of online junction temperature monitoring for SiC MOSFET based on temperature-sensitive electrical parameters," in *Proc. EPREC*, Durg, India, 2026, pp. 1–6, doi: [10.1109/EPREC66546.2026.11412294](https://doi.org/10.1109/EPREC66546.2026.11412294).
10. L. M. Tolbert, S. K. Islam and M. S. Chinthavali, "Wide bandgap semiconductors for utility applications," in *Proc. IASTED Int. Conf. Power and Energy Systems*, 2003.
11. M. Ciappa, "Selected failure mechanisms of modern power modules," *Microelectronics Reliability*, vol. 42, no. 4, pp. 653–667, 2002.

Copies of the referenced papers are not redistributed here; they are available from the publishers via the DOIs and citations above.

---

## Author

**Mahdi Mounzer** — Electrical engineering student (FIP Génie Électrique), INSA Strasbourg
✉️ mahdi.mounzer@insa-strasbourg.fr

## Citation

```bibtex
@inproceedings{mounzer2026sicai,
  author    = {Mounzer, Mahdi},
  title     = {A Survey of AI-Based Methods for SiC MOSFET Management in Automotive Traction Inverters},
  booktitle = {IEEE Vehicle Power and Propulsion Conference (VPPC)},
  year      = {2026}
}
```
