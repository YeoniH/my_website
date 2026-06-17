# Interactive persistent homology demo

This folder contains a standalone browser app for demonstrating persistent homology of a 2D point pattern using either a Čech or Vietoris--Rips filtration.

## Files

- `persistent_homology_demo_app.html`: the actual standalone interactive app.
- `index.qmd`: optional Quarto wrapper page that embeds the app in an iframe.
- `README.md`: this file.

## Suggested placement in your Quarto site

You can keep this as a separate top-level folder:

```text
interactive_persistence/
├── index.qmd
├── persistent_homology_demo_app.html
└── README.md
```

Or, if you expect several interactive demos, use a shared parent folder:

```text
interactive/
├── lloyd/
│   ├── index.qmd
│   └── lloyd_demo_app.html
└── persistence/
    ├── index.qmd
    └── persistent_homology_demo_app.html
```

If using the shared `interactive/` structure, update the iframe in `interactive/persistence/index.qmd` to:

```html
<iframe src="persistent_homology_demo_app.html" ...></iframe>
```

and use this in `_quarto.yml`:

```yaml
project:
  type: website
  output-dir: docs
  resources:
    - interactive/**
```

If using the separate top-level folder, use:

```yaml
project:
  type: website
  output-dir: docs
  resources:
    - interactive_persistence/persistent_homology_demo_app.html
```

## Links

From a research subpage, for the separate top-level folder:

```markdown
[Launch interactive persistent homology demo](../interactive_persistence/){.btn .btn-primary}
```

From a research subpage, for the shared folder structure:

```markdown
[Launch interactive persistent homology demo](../interactive/persistence/){.btn .btn-primary}
```

## Technical note

The app computes the 2D filtration up to triangles. In the radius convention used here:

- vertices appear at `r = 0`
- edges appear at half the pairwise distance
- Čech triangles appear at the smallest enclosing-circle radius of three points
- Vietoris--Rips triangles appear at half the longest side length of the triple

The maximum number of points is capped at 60 because the number of triangles scales as `N choose 3`.
