# Results

This page summarises the main results of the angular decomposition of the five-body decay **B⁺ → K⁺π⁺π⁻ℓ⁻ℓ⁺**.

## Model

The decay amplitude is built in the helicity formalism with the isobar approach, for massless leptons. It is the coherent sum of a non-resonant term and 33 resonant channels, grouped into three topologies:

| Topology | Channels | Coefficients |
|---|---|---|
| Non-resonant | 1 | a_NR |
| B⁺ → (R⁺ → K⁺π⁺π⁻) ℓ⁻ℓ⁺ | 5 | a₁ … a₅ |
| B⁺ → P₁⁺ (R⁰ → P₂⁺π⁻) ℓ⁻ℓ⁺ | 11 | a₆ … a₁₆ |
| B⁺ → [R₁⁺ → P₁⁺ (R₂⁰ → P₂⁺π⁻)] ℓ⁻ℓ⁺ | 17 | a₁₇ … a₃₃ |

The complex coefficients aᵢ are the model parameters, 34 in total.

**Non-resonant amplitude.** The K⁺π⁺π⁻ system is taken in an S-wave (J = 0) with no propagator, so the hadronic part is constant over phase space. The spin projection of the dilepton pair along the dilepton axis, in the massless limit, is fixed to η = λℓ⁻ − λℓ⁺ = ∓1, so the amplitude carries the corresponding Wigner function:

$$\mathcal{A}^\eta_{NR} = a_{NR}\; B_1(q_B)\; H(\eta,0,0,1,\mathrm{NR})\; 2\sqrt{2}\,q\; d^{1*}_{0,\eta}(\theta_\ell)\,\frac{1}{4\pi}.$$

**Differential rate.** Left- and right-handed leptonic currents do not interfere for massless leptons, so

$$\frac{d^8\Gamma}{dq^2\,dm^2_{123}\,dm^2_{23}\,d\Omega} \propto \sum_{\eta=L,R} |\mathcal{A}^\eta|^2 = \sum_i G_i(q^2, m^2_{123}, m^2_{23})\, f_i(\Omega),$$

with Ω = (θℓ, θ₁, θ₂, φ, χ). Each moment can be written as Gᵢ = gᵢᴸ + ωᵢ gᵢᴿ, where ωᵢ = ±1 is the behaviour of the term under the exchange L ↔ R.

## Angular basis

The angular functions are kept in Wigner form, without expanding them into sines and cosines. After reducing the products of Wigner matrices with the Clebsch–Gordan series, every term of |𝒜|² multiplies a product

$$\mathcal{D} = d^{j_\ell}_{m_\ell,0}(\theta_\ell)\; D^{j_1}_{m_1,k_1}(\phi,\theta_1,0)\; D^{j_2}_{m_2,0}(\chi,\theta_2,0).$$

Each product has a partner 𝒟′ with all indices reversed, related by 𝒟* = p·𝒟′ with p = (−1)^Σ(m−k). Because |𝒜|² is real, the coefficient of the partner is A′ = p·A*, and the pair contributes

$$A\,\mathcal{D} + A'\,\mathcal{D}' = 2\,\mathrm{Re}A\;\mathrm{Re}\,\mathcal{D} \;-\; 2\,\mathrm{Im}A\;\mathrm{Im}\,\mathcal{D}.$$

Every pair therefore gives two real, mutually orthogonal functions, Re 𝒟 and Im 𝒟, each with its own real moment. Products with all indices equal to zero are already real.

### Orthogonal basis

| Quantity | Value |
|---|---|
| Real angular functions in the basis | **461** |
| already real 𝒟 | 75 |
| Re 𝒟 | 193 |
| Im 𝒟 | 193 |
| Non-orthogonal pairs (Gram matrix) | **0** |
| Functions with ω = +1 | 296 |
| Functions with ω = −1 | 165 |

All 461 functions are mutually orthogonal under the scalar product

$$\langle f|g\rangle = \frac{1}{32\pi^2}\int_0^{2\pi}\! d\phi \int_0^{2\pi}\! d\chi \int_{-1}^{1}\! d\cos\theta_1 \int_{-1}^{1}\! d\cos\theta_2 \int_{-1}^{1}\! d\cos\theta_\ell\; f(\Omega)\,g^*(\Omega).$$

Orthogonality in θℓ, which has no azimuthal angle of its own, relies on the leptonic index being zero for every function. This holds because the L and R currents do not interfere.

The ranks reached in each subsystem are:

| Subsystem | Maximum rank |
|---|---|
| Leptonic, d^{jℓ}(θℓ) | jℓ ≤ 2 |
| K⁺π⁺π⁻, D^{j₁}(φ, θ₁, 0) | j₁ ≤ 4 |
| P₂⁺π⁻, D^{j₂}(χ, θ₂, 0) | j₂ ≤ 4 |

These are consistent with jmax = 2J for intermediate states of spin up to J = 2 and a leptonic system of spin 1.

### Independent moments

The moments are not all linearly independent: some are fixed linear combinations of others for any value of the dynamical parameters (aᵢ, helicity amplitudes, propagators, Blatt–Weisskopf factors, q²).

| Quantity | Value |
|---|---|
| Linearly independent moments | **340** |
| with ω = +1 | 215 |
| with ω = −1 | 125 |
| Dependent moments | 121 |

Each dependent moment satisfies an exact relation Gₖ = Σⱼ cₖⱼ Gⱼ. Some examples:

```
G_31 = (10/7)·G_5 − (15/7)·G_16
G_44 = 4·G_16
```

For a method-of-moments analysis the approach consists of measuring all 461 moments in the orthogonal basis and using the 121 relations as constraints or cross-checks.
Absorbing the dependent moments into effective functions would reduce the basis to 340 functions, but those functions are no longer orthogonal.


## Files

All files are in [`WignerAmplitude/`](WignerAmplitude/).

| File | Content |
|---|---|
| `MomentiReIm.ipynb` | Full computation, from the saved \|𝒜\|² to the final moments, with a detailed printed summary in the last cell |
| `REIM_moments.pkl` | All 461 functions with their moments gᴸ, gᴿ, symmetry ω, independence flag and relation |
| `REIM_moments_independent.pkl` | The 340 functions with independent moments |
| `Moments_ReIm/D_<i>_omega_<piu\|meno>.txt` | Readable angular function and moment gᴸ for each independent moment |
| `Moments_ReIm/relazioni.txt` | The 121 linear relations between moments |
| `NR_WIGAtotsq.pkl`, `NR_angular_trig_coefficients.pkl` | Cached intermediate results (corrected \|𝒜\|² and its Clebsch–Gordan reduction) |

In the moment expressions, H, H̄ and G are the hadronic helicity amplitudes, with arguments (η, J, λ, L_B, resonance). R is the propagator, BW the Blatt–Weisskopf factor and aᵢ the complex coefficients.

**Reproducing the results.** Run `MomentiReIm.ipynb` from the `WignerAmplitude/` folder. It reads `WIGAtotsq_terms33281.pkl` produced by `AmpiezzaWigner.ipynb` and reuses the cached files when present.

*A full run takes about 10 minutes.*

