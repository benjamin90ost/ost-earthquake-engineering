# Response Spectra and SDOF Oscillator

Interactive teaching tool for the lecture *AK 1 Earthquake Engineering* (Lecture 9), OST Rapperswil.
It runs entirely in the browser: static HTML files, no server, no installation. English (`index.html`) and German (`de.html`); the language button in the header switches between them, and visitors with a German browser language are sent to the German version on their first visit.

**Live version:** `https://<github-user>.github.io/<repository>/`

## Features

| Tab | Content |
|---|---|
| 1 SDOF oscillator | Linear SDOF response to a ground motion: a_g(t), u(t), a_abs(t), peak values, animated oscillator |
| 2 Response spectrum | Sa, Sv, Sd and pseudo values; damping family; all ground motions scaled to equal PGA with mean; inelastic overlay for a given R_y (peak absolute acceleration, velocity and displacement of the bilinear SDOF, plus Sa,el/R_y); SIA 261:2020 elastic and design spectra for comparison |
| 3 Nonlinear SDOF | Bilinear SDOF (kinematic hardening), input via strength reduction R_y; hysteresis, ductility demand, residual displacement; u_NL/u_el(T) and μ(T) (equal displacement rule) |
| 4 Theory and method | Equations, algorithms, assumptions |

Further: custom ground motion upload (.txt/.csv; one column a_g or two columns t, a_g; unit m/s², g or cm/s² selectable; Δt for single-column files; warning and shading for Δt > 0.02 s), projector mode, PNG export of every chart, spectrum export as tab-separated text, responsive layout for desktop, tablet and phone.

## Method (summary)

- Newmark, constant average acceleration (β = 1/4, γ = 1/2), substeps h ≤ T/50 with linearly interpolated excitation, peaks searched in every substep; checked against the exact state-space solution (deviation of spectral values < 0.5 %).
- Nonlinear: Newmark in total form with Newton-Raphson iteration per substep (Chopra, *Dynamics of Structures*, Sec. 5.7).
- Every record is extended internally by a free-vibration phase with a_g = 0 (max(5 s, 5·T), at most 50 s).
- Inelastic overlay: for every spectrum period one nonlinear analysis with F_y = F_el(T)/R_y.

## Deploy on GitHub Pages

1. Create a new public repository on GitHub (e.g. `response-spectra`).
2. Upload `index.html`, `de.html`, `README.md` and `THIRD_PARTY_LICENSES.md` (*Add file → Upload files*, then *Commit changes*).
3. *Settings → Pages → Build and deployment*: Source *Deploy from a branch*, Branch `main`, folder `/ (root)`, *Save*.
4. After about one minute the app is available at `https://<github-user>.github.io/<repository>/`.

To update, upload new `index.html` / `de.html` files with the same names; GitHub Pages republishes automatically.

## Run locally

Open `index.html` or `de.html` in any current browser (Chrome, Edge, Firefox, Safari).

## Credits

Benjamin Schmid · OST Rapperswil.
Charts: [uPlot](https://github.com/leeoniya/uPlot) (MIT licence, see `THIRD_PARTY_LICENSES.md`).
