# Quarto interactive Lloyd demo

Files:

- `lloyd_demo.html`: standalone browser demo.
- `lloyd_demo.qmd`: Quarto page that embeds the standalone demo with an iframe.
- `lloyd_demo_iframe_snippet.html`: minimal raw HTML snippet to paste into another `.qmd` page.

## Add to a Quarto website

Copy the `interactive/` directory into your Quarto project, then link to `interactive/lloyd_demo.qmd` from your website navigation or paste the iframe snippet into an existing page.

The demo runs client-side in the browser and uses D3's Delaunay/Voronoi implementation.  It is intended for explanation and intuition, not for replacing the Python/freud-analysis simulations.

## Controls included

- Number of points
- Initial condition: random, regular triangular-like, jittered regular
- Constraint / boundary: periodic torus, bounded square
- Voronoi colour mode: n-sided cells or hexatic phase angle
- Perturbation schedule: none, persistent, finite window, single impulse, annealed
- Perturbation amplitude, proportion, distribution, and location, with hover annotations
- Local radius / strip width
- Center-of-mass correction for perturbation displacements

## Display included

Left panel:

- Evolving point pattern, with currently perturbed points highlighted in red
- Corresponding Voronoi cellular pattern
- Colour by n-sided cells, with 5 = blue, 6 = white, 7 = red
- Colour by phase of the hexatic order parameter using a cyclic colour map, with a -pi to pi colourbar

Right panel:

- Total quantizer energy
- Mean-square displacement
- Mean hexatic-order modulus
- `S_k` low-wavenumber structure-factor proxy
- 5/6/7-sided cell fractions

## Practical limits

The browser demo is most responsive for roughly 20-250 points.  It allows up to 360 points, but animation speed will depend on the user's device.

The demo uses `S_k` for the low-wavenumber structure-factor proxy: an average of S(k)=|sum_j exp(-i k.r_j)|^2/N over a small set of low Fourier modes. It measures large-scale density fluctuation suppression in a finite browser-scale system.
