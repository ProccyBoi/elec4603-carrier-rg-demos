# Carrier Generation and Recombination: Paste-Ready Wiki Sections

Use this as a clean replacement for the current draft sections that still contain `[Equation]` placeholders. Equations are written in plain text/LaTeX-style form so they can be pasted into OneNote equation boxes.

## Section 1: Generation Mechanisms

### Overview

Carrier generation occurs when energy is supplied to create an electron-hole pair. Physically, an electron is promoted from the valence band to the conduction band, leaving a hole behind. The main generation mechanisms in semiconductor devices are thermal generation, optical generation, trap-assisted generation, and impact ionisation [1], [2].

| Mechanism | Energy source | Important when | Main device effect |
|---|---|---|---|
| Thermal generation | Heat / lattice vibrations | High temperature, small bandgap | Leakage current and dark current |
| Optical generation | Photons | `h nu >= E_g` | Photocurrent in solar cells and photodiodes |
| Trap-assisted generation | Defect states in the bandgap | Depletion regions, poor material quality, interfaces | Reverse leakage |
| Impact ionisation | High electric field | Large reverse bias | Avalanche multiplication or breakdown |

### Thermal Generation

Thermal generation occurs because the lattice has thermal energy at any finite temperature. Occasionally, this energy contributes to the creation of a mobile electron-hole pair.

```text
thermal energy -> e^- + h^+
```

Thermal generation is closely related to intrinsic carrier concentration:

```text
n_i proportional to T^(3/2) exp[-E_g/(2 k_B T)]
```

This exponential dependence means temperature and bandgap are critical. Higher temperature increases thermal generation; a larger bandgap reduces it because more energy is required to create an electron-hole pair [1], [2].

Device implication: thermal generation is often unwanted. In reverse-biased diodes it contributes to leakage current. In photodiodes and image sensors it contributes to dark current, which is current that exists even when no light is applied [3], [4].

### Optical Generation

Optical generation occurs when an absorbed photon has enough energy to excite an electron across the bandgap:

```text
h nu >= E_g
```

or, using wavelength,

```text
h c / lambda >= E_g
```

If photon energy is below the bandgap, ideal band-to-band absorption cannot create a mobile electron-hole pair. If photon energy is above the bandgap, absorption can generate a mobile electron and hole [1], [5].

As light enters a semiconductor, the photon flux falls with depth:

```text
Phi(x) = Phi_0 exp(-alpha x)
```

A simple optical generation rate is:

```text
G_opt(x) = eta alpha Phi_0 exp(-alpha x)
```

Equivalently, if incident optical intensity is `I_0`, the incident photon flux is approximately:

```text
Phi_0 = I_0 / (h nu)
```

so

```text
G_opt(x) = eta alpha [I_0/(h nu)] exp(-alpha x)
```

where `eta` is a quantum-efficiency factor, `alpha` is the absorption coefficient, `I_0` is incident optical intensity, `h nu` is photon energy, and `x` is depth. A large `alpha` means carriers are generated near the surface; a smaller `alpha` means light penetrates deeper before being absorbed [1], [5].

| Device | Role of optical generation |
|---|---|
| Solar cell | Generates carriers that are separated and collected as current |
| Photodiode | Converts light intensity into electrical current |
| Image sensor | Converts spatial light patterns into charge/current |
| LED | Optical generation is not the main operation; recombination produces the emitted light |

### Trap-Assisted Generation

Real semiconductors contain defects, impurities, and interface states. These can create trap levels inside the bandgap. Trap-assisted generation lets carriers be generated through intermediate energy states rather than by one direct transition across the full bandgap [1], [2], [6], [7].

In a depletion region, mobile carrier concentrations are low. A trap can emit carriers, and the built-in electric field can sweep the generated electron and hole apart before they recombine. A common approximate depletion-region generation rate is:

```text
G_SRH ~= n_i / tau_g
```

where `tau_g` is the generation lifetime. Higher trap density usually reduces `tau_g`, increasing generation current and reverse leakage [2], [4].

### Impact Ionisation Generation

Impact ionisation occurs when a strong electric field accelerates a carrier to high kinetic energy. If that carrier collides with the lattice and transfers enough energy, it can create an additional electron-hole pair:

```text
fast carrier + valence electron -> extra electron-hole pair
```

The newly generated carriers can also be accelerated and generate more carriers. This chain reaction is avalanche multiplication. Unlike thermal generation, impact ionisation is mainly driven by electric field strength, not just temperature [1], [2].

Impact ionisation is harmful in ordinary diodes when it causes uncontrolled breakdown, but it is useful in avalanche photodiodes where multiplication increases optical sensitivity.

### Generation Dependence on Physical Properties

| Physical property | Effect on generation | Reason |
|---|---|---|
| Temperature `T` | Increases thermal generation | More thermal energy is available; `n_i` rises strongly |
| Bandgap `E_g` | Larger `E_g` reduces thermal generation | More energy is required to create a pair |
| Light intensity `I_0` | Increases optical generation | More incident photons are available |
| Absorption coefficient `alpha` | Controls generation depth | Higher `alpha` means stronger near-surface absorption |
| Trap density `N_t` | Increases trap-assisted generation | More intermediate states are available |
| Electric field `E` | Increases impact ionisation probability | Carriers gain more kinetic energy between collisions |
| Material quality | Better material reduces unwanted generation | Fewer defect and interface states |

## Section 2: Recombination Mechanisms

### Overview

Recombination removes electron-hole pairs. A conduction-band electron loses energy and fills an available hole state in the valence band. Recombination mechanisms mainly differ by where the released energy goes and whether a defect or third carrier is involved [1], [2].

| Mechanism | Released energy goes to | Dominant when | Main device effect |
|---|---|---|---|
| Radiative recombination | Photon | Direct-bandgap materials | LEDs and lasers |
| Shockley-Read-Hall recombination | Lattice vibrations through a trap | Defects/traps present | Shorter lifetime, leakage, silicon losses |
| Auger recombination | Another carrier | High doping or high injection | Efficiency loss and heating |
| Surface recombination | Surface/interface traps | Poor passivation, high surface-area devices | Solar-cell, photodiode, and MOS-interface losses |

### Radiative Recombination

Radiative recombination is direct band-to-band recombination. An electron recombines with a hole and releases energy as a photon:

```text
e^- + h^+ -> h nu
```

A common net radiative recombination rate is:

```text
U_rad = B (n p - n_i^2)
```

where `B` is the radiative recombination coefficient. The term `(n p - n_i^2)` makes the net rate zero at thermal equilibrium [1], [2].

Radiative recombination is more efficient when energy and momentum can both be conserved easily. This is why direct-bandgap materials such as GaAs are useful for LEDs and lasers, while indirect-bandgap silicon is a poor light emitter [1], [2], [8].

### Shockley-Read-Hall Recombination

Shockley-Read-Hall (SRH) recombination occurs through defect or trap states inside the bandgap. Instead of recombining directly across the full bandgap, an electron and hole recombine through an intermediate trap level `E_t` [1], [6], [7].

The standard SRH net recombination rate is:

```text
U_SRH = (n p - n_i^2) / [tau_p0 (n + n_1) + tau_n0 (p + p_1)]
```

where `tau_n0` and `tau_p0` are electron and hole capture lifetimes, and `n_1` and `p_1` are trap-related carrier concentrations:

```text
n_1 = n_i exp[(E_t - E_i)/(k_B T)]
```

```text
p_1 = n_i exp[(E_i - E_t)/(k_B T)]
```

`E_i` is the intrinsic energy level. Traps near the middle of the bandgap are usually strong recombination centres because they are well positioned to capture both electrons and holes [1], [6], [7].

Device implication: SRH recombination is often important in silicon because silicon is an indirect-bandgap material and real devices contain defects, impurities, and interface states.

### Auger Recombination

Auger recombination occurs when an electron-hole pair recombines and transfers its released energy to a third carrier instead of emitting a photon. The third carrier becomes energetic and later loses that energy as heat through scattering [1], [2].

A common net Auger recombination rate is:

```text
U_Auger = (C_n n + C_p p)(n p - n_i^2)
```

where `C_n` and `C_p` are Auger coefficients. Auger recombination requires three carriers to interact, so it becomes much more likely at high carrier concentration, high-level injection, or heavy doping [1], [2].

### Surface Recombination

Surface recombination occurs at semiconductor surfaces and interfaces. At a surface, the periodic crystal lattice is interrupted, creating dangling bonds and interface trap states. These traps provide recombination paths similar to SRH recombination, but localised at the surface [2], [5].

A common surface recombination flux model is:

```text
R_s = S Delta n_s
```

where `S` is the surface recombination velocity and `Delta n_s` is the excess minority-carrier concentration at the surface. In one-dimensional diffusion problems, this is often used as a boundary condition:

```text
D_n (d Delta n/dx)|surface = S_n Delta n_s
```

Surface recombination is especially important in thin devices because a larger fraction of generated carriers can reach a surface before being collected.

### Effective Recombination Lifetime

When multiple independent recombination mechanisms act at the same time, their rates add. This is often written as an effective lifetime:

```text
1/tau_eff = 1/tau_rad + 1/tau_SRH + 1/tau_Auger + 1/tau_surface
```

The shortest lifetime usually dominates because it contributes the largest recombination rate [2], [5].

### Recombination Dependence on Physical Properties

| Physical property | Effect on recombination | Reason |
|---|---|---|
| Trap density | Increases SRH recombination | More intermediate states are available |
| Trap energy | Midgap traps are most effective | Electron and hole capture are both likely |
| Bandgap type | Direct bandgap increases radiative recombination | Momentum conservation is easier |
| Carrier concentration | Higher concentration increases recombination | More electrons and holes are available |
| Doping | Heavy doping can increase Auger recombination | More three-carrier interactions |
| Surface quality | Poor surfaces increase recombination | More interface trap states |
| Lifetime `tau` | Longer lifetime means slower recombination | Excess carriers survive longer |

## Section 3: Carrier Lifetime and Diffusion Length

### Overview

Carrier lifetime `tau` describes how long excess carriers survive before recombining. Diffusion length `L` describes how far they travel before recombining. These quantities determine whether generated carriers are collected or lost [2], [5].

### Excess Carrier Decay

When a semiconductor is disturbed:

```text
n = n_0 + Delta n
```

```text
p = p_0 + Delta p
```

After the excitation is removed, excess carriers decay by recombination. Under low-level injection, the net recombination rate for minority electrons in p-type material is:

```text
U_n ~= Delta n / tau_n
```

For minority holes in n-type material:

```text
U_p ~= Delta p / tau_p
```

With the convention `U = R - G`, positive `U` means net recombination. The units of `U` are usually `cm^-3 s^-1`.

The decay is exponential:

```text
Delta n(t) = Delta n(0) exp(-t/tau_n)
```

After one lifetime:

```text
Delta n(tau_n) = Delta n(0) e^-1 ~= 0.368 Delta n(0)
```

So after one lifetime, about 37% of the original excess minority carriers remain [2], [5].

Under steady uniform generation:

```text
Delta n_ss = G_L tau_n
```

This shows why the same generation rate creates a larger excess carrier population in material with longer lifetime.

### Diffusion Length

The diffusion length is the average distance an excess minority carrier travels before recombining:

```text
L_n = sqrt(D_n tau_n)
```

```text
L_p = sqrt(D_p tau_p)
```

The diffusion coefficient is related to mobility by the Einstein relation:

```text
D_n = mu_n k_B T / q = mu_n V_T
```

```text
D_p = mu_p k_B T / q = mu_p V_T
```

A larger diffusion coefficient or longer lifetime gives a longer diffusion length [5].

### Why It Matters

| Context | Effect |
|---|---|
| Solar cells | Longer `L` improves carrier collection |
| Photodiodes | Carriers must be collected before recombining |
| LEDs | Recombination is desired if it is radiative |
| Fast diodes | Shorter `tau` reduces stored minority charge |
| Defective material | More traps reduce `tau` and `L` |

### Lifetime and Diffusion Length Dependence

| Property | Effect |
|---|---|
| More traps/defects | Shorter SRH lifetime |
| Better crystal quality | Longer lifetime |
| Higher surface recombination | Lower effective lifetime |
| Higher diffusion coefficient | Longer diffusion length |
| Heavy doping | Can shorten lifetime through Auger recombination |
| Higher temperature | Increases `n_i` and thermal generation; lifetime trend depends on mechanism |

## Section 4: Generation/Recombination in Devices

### Overview

Generation and recombination affect device current, leakage, switching speed, optical response, and efficiency. Whether they are useful or harmful depends on the device.

| Device | Useful effect | Unwanted effect |
|---|---|---|
| P-N diode | Recombination supports forward current | Generation causes reverse leakage |
| Solar cell | Light generation creates photocurrent | Recombination reduces collected current |
| Photodiode | Optical generation creates signal | Thermal generation causes dark current |
| LED | Radiative recombination emits light | Non-radiative recombination wastes energy |
| Switching diode | Short lifetime improves turn-off | Too much recombination increases loss |
| BJT | Carrier injection enables gain | Base recombination reduces gain |

### P-N Junction Diodes

Forward bias reduces the junction potential barrier. Majority carriers cross the junction and become minority carriers on the opposite side:

```text
carrier injection -> minority carrier diffusion -> recombination
```

This injected minority-carrier diffusion and recombination supports the forward diode current. The exponential diode current comes from the exponential change in minority-carrier concentrations at the depletion-region edges [4], [9].

Reverse bias widens the depletion region. Thermally generated or trap-generated carriers in or near this region are swept across by the electric field:

```text
thermal/trap generation -> carrier sweep-out -> reverse leakage
```

In the ideal diode model, reverse current approaches the saturation current `I_S`. Real reverse leakage is often larger because of defects, surface leakage, and depletion-region generation [3], [9].

For a long-base diode, an ideal diffusion-limited saturation current can be written as [10]:

```text
I_S = q A n_i^2 [ D_p/(L_p N_D) + D_n/(L_n N_A) ]
```

### Solar Cells and Photodiodes

In solar cells and photodiodes:

```text
light -> electron-hole pairs -> separated/collected current
```

Good optical-device performance requires high optical generation, low recombination, long carrier lifetime, long diffusion length, and low surface recombination [5]. Thermal and trap-assisted generation cause unwanted dark current in photodiodes and image sensors.

### LEDs

In LEDs, recombination is the desired process if it is radiative:

```text
e^- + h^+ -> h nu
```

Efficient LEDs require strong radiative recombination and low non-radiative recombination. Direct-bandgap materials are preferred because radiative recombination is much more efficient than in indirect-bandgap silicon [1], [8].

### Fast Switching Diodes

Forward bias stores minority-carrier charge. During turn-off, this stored charge must be removed before the diode fully blocks reverse voltage. A simple proportionality is:

```text
Q_stored proportional to I_F tau
```

where `I_F` is the previous forward current. A shorter lifetime reduces stored charge and improves switching speed, but it can increase recombination loss while the device is conducting.

### Avalanche Devices

At high reverse bias, impact ionisation can create extra electron-hole pairs. This causes avalanche multiplication. It is harmful in ordinary diodes if uncontrolled, but useful in avalanche photodiodes because multiplication increases photocurrent gain [1], [2].

## Section 5: Sample Problems

### Problem 1: Excess Carrier Decay

Question: A silicon sample has:

```text
Delta n(0) = 1.0e15 cm^-3
tau_n = 5 us
```

After the light is switched off, find:

1. `Delta n` after `5 us`.
2. The time for `Delta n` to fall to 1% of its initial value.

Worked solution:

Use:

```text
Delta n(t) = Delta n(0) exp(-t/tau_n)
```

Concentration after `5 us`:

```text
Delta n(5 us) = 1.0e15 exp(-5/5)
              = 1.0e15 exp(-1)
              = 3.68e14 cm^-3
```

Time to reach 1%:

```text
Delta n(t) / Delta n(0) = 0.01
```

```text
exp(-t/tau_n) = 0.01
```

```text
t = tau_n ln(100)
  = 5 us * 4.605
  = 23.0 us
```

### Problem 2: Diffusion Length and Recombination Rate

Question: A p-type silicon sample at 300 K has:

```text
N_A = 1.0e16 cm^-3
n_i = 1.0e10 cm^-3
D_n = 35 cm^2/s
tau_n = 5 us
Delta n = 2.0e14 cm^-3
```

Find:

1. Equilibrium minority electron concentration `n_0`.
2. Electron diffusion length `L_n`.
3. Recombination rate `U_n`.

Worked solution:

For p-type material:

```text
p_0 ~= N_A
```

```text
n_0 = n_i^2 / p_0
    = (1.0e10)^2 / (1.0e16)
    = 1.0e4 cm^-3
```

Electron diffusion length:

```text
L_n = sqrt(D_n tau_n)
```

Convert lifetime:

```text
tau_n = 5 us = 5.0e-6 s
```

```text
L_n = sqrt(35 * 5.0e-6)
    = 1.32e-2 cm
    = 132 um
```

Recombination rate:

```text
U_n ~= Delta n / tau_n
    = 2.0e14 / 5.0e-6
    = 4.0e19 cm^-3 s^-1
```

Low-level injection check:

```text
Delta n / N_A = 2.0e14 / 1.0e16 = 0.02
```

Since this is much less than 1, the low-level injection approximation is reasonable.

### Problem 3: Reverse Saturation Current

Question: A long-base silicon diode at 300 K has:

```text
A = 1.0e-4 cm^2
n_i = 1.0e10 cm^-3
N_D = 1.0e16 cm^-3
N_A = 1.0e16 cm^-3
D_p = 12 cm^2/s
D_n = 35 cm^2/s
L_p = 50 um
L_n = 100 um
q = 1.60e-19 C
```

Estimate `I_S`.

Worked solution:

Use the long-base diode saturation-current expression:

```text
I_S = q A n_i^2 [ D_p/(L_p N_D) + D_n/(L_n N_A) ]
```

Convert diffusion lengths:

```text
L_p = 50 um = 5.0e-3 cm
L_n = 100 um = 1.0e-2 cm
```

Hole-injection term:

```text
D_p/(L_p N_D) = 12 / [(5.0e-3)(1.0e16)]
              = 2.4e-13 cm^2/s
```

Electron-injection term:

```text
D_n/(L_n N_A) = 35 / [(1.0e-2)(1.0e16)]
              = 3.5e-13 cm^2/s
```

Total bracket:

```text
2.4e-13 + 3.5e-13 = 5.9e-13
```

Now:

```text
q A n_i^2 = (1.60e-19)(1.0e-4)(1.0e20)
          = 1.60e-3
```

Therefore:

```text
I_S = (1.60e-3)(5.9e-13)
    = 9.44e-16 A
```

Interpretation: `I_S` is very small, but it increases strongly with temperature because `n_i` increases strongly with temperature.

### Problem 4: Design Comparison

Question: Why is a short minority-carrier lifetime useful in a fast switching diode but harmful in a silicon solar cell?

Worked solution:

In a switching diode, stored minority-carrier charge must be removed before the diode can turn off:

```text
Q_stored proportional to I_F tau
```

A shorter `tau` means less stored charge, so the diode can turn off faster.

In a solar cell, generated carriers must survive long enough to reach the junction or contact. The diffusion length is:

```text
L = sqrt(D tau)
```

A shorter `tau` reduces `L`, so more photogenerated carriers recombine before collection. Therefore, the same physical change can be helpful for fast switching but harmful for solar-cell efficiency.

### Bonus Problem 5: Surface Recombination Design

Question: A thin p-type silicon photodiode has:

```text
D_n = 35 cm^2/s
tau_bulk = 10 us
W = 20 um
S = 1.0e4 cm/s
G_L = 2.0e20 cm^-3 s^-1
```

Assume both surfaces recombine. Estimate `tau_eff`, `L_eff`, and steady-state `Delta n`.

Worked solution:

For a simple thin slab:

```text
1/tau_eff ~= 1/tau_bulk + 2S/W
```

Convert:

```text
tau_bulk = 10 us = 1.0e-5 s
W = 20 um = 2.0e-3 cm
```

```text
1/tau_eff = 1/(1.0e-5) + 2(1.0e4)/(2.0e-3)
          = 1.0e5 + 1.0e7
          = 1.01e7 s^-1
```

```text
tau_eff = 9.90e-8 s = 99 ns
```

Diffusion length:

```text
L_eff = sqrt(D_n tau_eff)
      = sqrt(35 * 9.90e-8)
      = 1.86e-3 cm
      = 18.6 um
```

Steady-state excess concentration:

```text
Delta n_ss = G_L tau_eff
            = (2.0e20)(9.90e-8)
            = 1.98e13 cm^-3
```

Design interpretation: the bulk lifetime was 10 us, but surface recombination reduces the effective lifetime to about 99 ns. This is why surface passivation is critical in thin photodiodes and solar cells.

## Multimedia and Original Work Links

Use the original interactive simulator included with this repository:

```text
carrier_rg_interactive_demo.html
```

If GitHub Pages is enabled, open the demo from the repository landing page:

```text
index.html
```

Suggested wiki caption:

```text
Original interactive simulator showing how carrier lifetime, generation rate, surface recombination velocity, temperature, and device thickness affect excess-carrier decay and diffusion length.
```

Recommended videos:

| Use | Link |
|---|---|
| Carrier recombination explanation | Purdue/nanoHUB, ECE Purdue Semiconductor Fundamentals L4.4: https://www.youtube.com/watch?v=iBGgzrvwFi8 |
| Carrier generation explanation | Purdue/nanoHUB, ECE Purdue Semiconductor Fundamentals L4.5: https://www.youtube.com/watch?v=9h10p6M3Jo8 |
| Longer lecture on recombination-generation | NPTEL, Carrier recombination-generation I: https://www.youtube.com/watch?v=QpWtFWM29Wg |
| Follow-up recombination-generation lecture | NPTEL, Carrier recombination-generation II: https://www.youtube.com/watch?v=dj6C-t7uGVA |

## References

[1] R. Entner, "2.3 Carrier Generation and Recombination," TU Wien, 2007. [Online]. Available: https://www.iue.tuwien.ac.at/phd/entner/node11.html

[2] S. M. Sze and K. K. Ng, Physics of Semiconductor Devices, 3rd ed. Hoboken, NJ, USA: Wiley, 2007.

[3] C. Honsberg and S. Bowden, "Ideality Factor and I0," PV Education. [Online]. Available: https://www.pveducation.org/pvcdrom/idealty-factor-and-i0

[4] J. A. del Alamo, "Lecture 4: Carrier generation and recombination," MIT OpenCourseWare, 6.720J Integrated Microelectronic Devices, Spring 2007. [Online]. Available: https://ocw.mit.edu/courses/6-720j-integrated-microelectronic-devices-spring-2007/6ea95228c96b5cb849eca384b52f4ccf_lecture4.pdf

[5] C. Honsberg and S. Bowden, "Diffusion Length," PV Education. [Online]. Available: https://www.pveducation.org/pvcdrom/pn-junctions/diffusion-length

[6] W. Shockley and W. T. Read, "Statistics of the recombinations of holes and electrons," Physical Review, vol. 87, no. 5, pp. 835-842, 1952, doi: 10.1103/PhysRev.87.835.

[7] R. N. Hall, "Electron-hole recombination in germanium," Physical Review, vol. 87, no. 2, p. 387, 1952, doi: 10.1103/PhysRev.87.387.

[8] NPTEL, "Band to Band recombination," High Speed Semiconductor Devices archive. [Online]. Available: https://archive.nptel.ac.in/content/storage2/courses/117104071/topic19/19_3.html

[9] C. G. Fonstad, "Lecture 6: p-n Junctions: I-V Relationship," MIT OpenCourseWare, 6.012 Microelectronic Devices and Circuits, Fall 2009. [Online]. Available: https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/a342ce0afb84bfa8e5b7dc819ff3e9bc_MIT6_012F09_lec06.pdf

[10] P. Hadley, "PN diode IV characteristics," TU Graz. [Online]. Available: https://lampz.tugraz.at/~hadley/psd/L6/pnIV.php
