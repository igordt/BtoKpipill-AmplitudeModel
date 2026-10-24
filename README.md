# BtoKpipill-AmplitudeModel

## Description

This repository contains the calculations for the amplitude model of the rare five-body decay **B⁺ → K⁺π⁺π⁻ℓ⁻ℓ⁺**, induced by the FCNC b → s ℓ⁻ℓ⁺ transition. They were developed for the Master thesis *"Amplitude model for 5-body b → s ℓ⁻ℓ⁺ decays"* (University of Pisa).

The decay amplitude is built in the helicity formalism with the isobar approach, for massless leptons. It sums a non-resonant term and 33 resonant channels, which cover three topologies:
- three-body resonances, R⁺ → K⁺π⁺π⁻;
- a single two-body resonance, B⁺ → P₁⁺(R⁰ → P₂⁺π⁻)ℓ⁻ℓ⁺;
- cascades of two resonances, B⁺ → [R₁⁺ → P₁⁺(R₂⁰ → P₂⁺π⁻)]ℓ⁻ℓ⁺.

The squared amplitude is then decomposed onto an **orthogonal basis of real angular functions** written with Wigner D-matrices.
Each function is multiplied by a real angular moment that depends only on q², m²(K⁺π⁺π⁻) and m²(P₂⁺π⁻). These moments are the angular observables of the decay and are meant for a method-of-moments analysis.

## Main results

| Quantity | Value |
|---|---|
| Model parameters (complex coefficients aᵢ) | 34 |
| Real, mutually orthogonal angular functions | **461** |
| with L ↔ R symmetry ω = +1 / ω = −1 | 296 / 165 |
| Linearly independent angular moments | **340** |
| Exact linear relations between the remaining moments | 121 |

The full results, with the definition of the basis, the form of the moments and the list of output files, are in **[Results.md](Results.md)**.

## Repository structure

### Wigner-basis decomposition (main computation)

Folder: [`WignerAmplitude/`](WignerAmplitude/)

- **[`AmpiezzaWigner.ipynb`](WignerAmplitude/AmpiezzaWigner.ipynb)** computes the squared amplitude:
  - builds the decay amplitude for all channels, with the angular dependence kept in Wigner D-matrices;
  - computes the squared amplitude, summed over the two chiralities of the leptonic current;
  - saves the result in `WIGAtotsq_terms33281.pkl`.
- **[`MomentiReIm.ipynb`](WignerAmplitude/MomentiReIm.ipynb)** starts from the saved squared amplitude and computes the moments:
  - writes the non-resonant amplitude with the leptonic structure required by the V−A current;
  - reduces the products of Wigner matrices with the Clebsch–Gordan series;
  - builds the real orthogonal basis from Re 𝒟 and Im 𝒟;
  - extracts the moments and their L ↔ R symmetry ω;
  - identifies the linearly independent moments and the relations between the others;
  - checks every step numerically and prints a detailed summary in the last cell.
- **`Moments_ReIm/`** holds one readable text file per independent moment, with the angular function and the moment gᴸ, plus `relazioni.txt` with the linear relations between moments.
- **`.pkl` files** contain saved intermediate and final results: `REIM_moments*.pkl` for the moments and `NR_*.pkl` as caches.

### Expansion in sines and cosines

Folder: [`ExpandedAmplitude/`](ExpandedAmplitude/)

- **[`Ampiezza.ipynb`](ExpandedAmplitude/Ampiezza.ipynb)** builds the same amplitude and expands its squared modulus in products of sines and cosines of the angular variables. This is an alternative representation. It does not include the corrections applied in `MomentiReIm.ipynb`.

### Three- and four-body decays

These notebooks validate the method on simpler decays, comparing with known results in the literature.

- **[`B to Kℓℓ.ipynb`](B%20to%20Kℓℓ.ipynb)**: B → K ℓℓ in the helicity formalism.
- **[`B to Kπℓℓ.ipynb`](B%20to%20Kπℓℓ.ipynb)**: B → (K* → Kπ) ℓℓ in the helicity formalism.
- **[`LeptonicHA.ipynb`](LeptonicHA.ipynb)**: explicit calculation of the leptonic helicity amplitudes.

## Notation in the moment expressions

- **H(η, J, λ, L, R)**, **H̄(η, J, λ, L, R)**, **G(η, J, λ, L, R)** are the hadronic helicity amplitudes for B → K_J, B → K*_J and B → R P₁ respectively. Their arguments are:
  - **η**, the chirality of the leptonic current (−1 for left-handed, +1 for right-handed);
  - **J**, the spin of the hadronic system produced in the B decay;
  - **λ**, the helicity of the hadronic system;
  - **L**, the orbital angular momentum between the decay products of the B;
  - **R**, the resonance produced in the B decay (`NR` for the non-resonant term).
- **R(Res)** is the propagator of resonance Res.
- **BW(L, r, q)** is the Blatt–Weisskopf form factor for orbital angular momentum L, radius r and break-up momentum q.
- **aᵢ** are the complex coefficients that weight each decay channel.
- **q** is √q², the dilepton invariant mass.

## Running the notebooks

The notebooks use Python 3.12. The required packages are listed in [`requirements.txt`](requirements.txt) and can be installed with

```
pip install -r requirements.txt
```

The versions of `sympy` and `dill` should match those listed, so that the saved `.pkl` files load correctly.

The calculations are computationally heavy, so intermediate results are saved in `.pkl` files and reloaded when present. To reproduce the main results, run `WignerAmplitude/MomentiReIm.ipynb` from its folder. It reads the saved squared amplitude and takes about 10 minutes.

## License

GNU General Public License v3.0, see [LICENSE](LICENSE).
