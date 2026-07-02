# ELEC4603 Carrier Generation and Recombination Demos

This repository contains shareable teaching resources for an ELEC4603 wiki page on carrier generation, recombination, carrier lifetime, diffusion length, and device applications.

## Contents

- `index.html` - landing page linking the resources.
- `carrier_rg_interactive_demo.html` - interactive lifetime, surface recombination, and diffusion length simulator.
- `pn_junction_photodiode_demo.html` - interactive p-n diode / photodiode simulator for dark current, photocurrent, saturation current, and open-circuit voltage.
- `carrier_rg_wiki_document.tex` - LaTeX source for the wiki reference document.
- `carrier_rg_wiki_document.pdf` - compiled PDF reference.
- `carrier_rg_wiki_paste_ready_sections.md` - paste-ready OneNote/wiki sections.

## How To Use

Open `index.html` in a browser, or use GitHub Pages if enabled for this repository.

The demos are standalone HTML files. They do not require a build step, external JavaScript libraries, or internet access.

## Academic Context

The demos are simplified teaching models. They are useful for explaining trends and design trade-offs, but they are not a replacement for a full semiconductor device simulator.

Key models used:

- `Delta n(t) = Delta n(0) exp(-t/tau)`
- `Delta n_ss = G_L tau`
- `L = sqrt(D tau)`
- `I_S = q A n_i^2 [D_p/(L_p N_D) + D_n/(L_n N_A)]`
- `I = I_S [exp(V/(eta V_T)) - 1] - I_L`
- `V_OC = eta V_T ln(I_L/I_S + 1)`

## References

- R. Entner, "2.3 Carrier Generation and Recombination," TU Wien.
- S. M. Sze and K. K. Ng, *Physics of Semiconductor Devices*, 3rd ed., Wiley, 2007.
- C. Honsberg and S. Bowden, "Diffusion Length," PV Education.
- C. G. Fonstad, "Lecture 6: p-n Junctions: I-V Relationship," MIT OpenCourseWare.
- P. Hadley, "PN diode IV characteristics," TU Graz.

