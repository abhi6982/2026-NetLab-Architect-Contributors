# Contributing to NetLab Architect

Thanks for your interest in contributing! This project is a single-file HTML application, so contributing is straightforward.

## Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/abhi6982/2026-NetLab-Architect-Contributors.git`
3. Open `public/index.html` directly in a browser, or serve it:
   ```bash
   python3 -m http.server 8080 -d public
   ```

## Making Changes

The entire application lives in `public/index.html`. It's organized in sections:

- **CSS** (lines 10-600) — Theming, layout, component styles
- **HTML** (lines 600-800) — DOM structure, modals, sidebar
- **JavaScript** (lines 800+) — All application logic:
  - `ICONS` — SVG device icons
  - `COMPONENTS` — Sidebar component library
  - `CABLE_TYPES` — Connection types
  - `PORT_TYPES` — Physical port type definitions
  - `DEVICE_DATABASE` — Real-world device specs and port layouts
  - Core functions: `addNode`, `renderNode`, `openPanel`, `renderConnections`, etc.

## Pull Request Guidelines

- Keep changes focused — one feature or fix per PR
- Test in both dark and light themes
- Test with existing saved diagrams (backward compatibility)
- If adding devices to `DEVICE_DATABASE`, include accurate specs and port layouts from manufacturer documentation

## Adding New Devices

To add a device to the database, add an entry to the appropriate array in `DEVICE_DATABASE`:

```javascript
{
  id: 'manufacturer-model',           // unique kebab-case ID
  manufacturer: 'Brand',              // display name
  model: 'Model Name',                // model string
  formFactor: '1U',                   // 1U, 2U, Desktop, Ceiling, etc.
  specs: 'Brief spec summary',        // shown in device selector
  portGroups: [
    {
      label: 'GE',                    // group label
      type: 'rj45_1g',               // key from PORT_TYPES
      count: 4,                       // number of ports
      namePattern: 'GE0/{i}',        // {i}=0-based, {I}=1-based
      startX: 20,                     // X position in front panel SVG
      startY: 12,                     // Y position
      spacing: 16,                    // pixels between ports
    },
  ],
}
```

## Reporting Issues

- Include browser name and version
- Include steps to reproduce
- If possible, include a screenshot or the browser console output
