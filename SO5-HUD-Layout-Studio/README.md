# Star Ocean 5 — HUD Layout Studio

**A standalone visual JSON preset editor for the Star Ocean 5: Integrity and Faithlessness Windows / PS4RT HUD research project.**

**Created by Hoverbike51** · **Current editor version: v2.2:** 
<a href="https://hoverbike51.github.io/SO5-HUD-Layout-Studio" rel="nofollow"><img src="https://camo.githubusercontent.com/faed9fa5201b528f62cb0e2069fb7cfea299bc459b282aa92030db22e30133b8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4f70656e2d53747564696f2d707572706c653f7374796c653d706c6173746963266c696e6b3d6874747073253341253246253246686f76657262696b6535312e6769746875622e696f253246534f352d4855442d4c61796f75742d53747564696f" alt="Open Studio" data-canonical-src="https://img.shields.io/badge/Open-studio-purple?style=plastic" style="max-width: 100%;"></a>


![SO5 HUD Layout Studio v2.2](assets/logo_hud_studio_HMV.png)

<p align="center">
<a href="https://ps4rt.dev" rel="nofollow"><img src="https://camo.githubusercontent.com/6cb97f075e7a4d8be62beba66e1c9ff78ba3d867d7d9f2a78a0a186c6403eed3/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f576562736974652d50533452542d677265656e6c3f7374796c653d666f722d7468652d6261646765" alt="Website PS4RT" data-canonical-src="https://img.shields.io/badge/Website-ps4rt-greenlight?style=for-the-badge" style="max-width: 100%;"></a></p>
<p align="center">  
<a href="https://github.com/Hoverbike51/Star-Ocean-Integrity-and-Faithlessness-PS4RT/releases" rel="nofollow"><img src="https://camo.githubusercontent.com/03a3895182681b7b79a28e779557a9d8c3db90d46522cf60d08cd643ec9d22ae/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f57696e646f77732d72656c656173652d626c75653f7374796c653d666f722d7468652d6261646765266c6f676f3d77696e646f7773266c696e6b3d68747470732533412532462532466769746875622e636f6d253246486f76657262696b653531253246537461722d4f6365616e2d496e746567726974792d616e642d46616974686c6573736e6573732d505334525425324672656c6561736573" alt="Windows Release" data-canonical-src="https://img.shields.io/badge/Windows-release-blue?style=for-the-badge" style="max-width: 100%;"></a>
</p>

![SO5 HUD Layout Studio Preview](assets/studio-preview.png)

## Overview

SO5 HUD Layout Studio lets you **inspect, adjust, calibrate, and export HUD layout JSON presets** without manually editing their structure. It supports three independent display profiles: **16:9**, **21:9**, and **32:9**.

The editor runs entirely in the browser. There is **no installer, server component, account requirement, build step, or external JavaScript dependency**. You may use it online through GitHub Pages or open `index.html` locally in a modern browser.

The application is a **research/development preview**, not the game's renderer. Its visual HUD bounds are calibration aids and must not be confused with guaranteed in-game coordinates.

## Features

| Feature | What it does |
| --- | --- |
| Three aspect-ratio profiles | Switch between separate 16:9, 21:9, and 32:9 HUD layouts. |
| Resolution presets | Select common screen sizes or enter custom canvas width and height. |
| Adaptive HUD preview | Scales the on-canvas layout with resolution; the game JSON keeps its logical coordinate system. |
| Visual positioning | Drag supported HUD groups or edit `offset_x` / `offset_y` directly. |
| Scale and anchor controls | Edit the supported group's `scale` and `anchor` settings. |
| Visibility controls | Show/hide individual HUD groups in the exported JSON. |
| Only Selected | Isolate the currently selected group **in the preview only**; does not rewrite JSON visibility. |
| Lock inside canvas | Prevent supported layout items from being moved outside the preview bounds. |
| Grid and guides | Toggle the grid, hidden-item display, and native-base visual guides. |
| Screenshot calibration | Import a PNG/JPEG/WebP screenshot to help align visual reference positions. |
| Separate calibration data | Save/import aspect-specific visual references independently of game layout JSON. |
| Original HUD safety reset | Restore all 31 groups to original anchors, zero offsets, scale 1 and visibility enabled, without changing the aspect family. |
| Preset name editor | Change a profile's JSON `name` and use it for the suggested exported filename. |
| Undo / Redo | Reverse and reapply preset changes. |
| Validated JSON import | Import up to three compatible files, one per aspect, with atomic validation before replacing profiles. |
| Unsaved-work protection | Track unsaved changes, warn before closing, and keep a browser-local recovery copy when storage is available. |
| Themed confirmations | Confirm resets, replacement imports, and recovery actions inside the editor. |
| Save As JSON | Use a native file-save picker where the browser permits, with a download fallback. |
| Export all · ZIP | Export the three aspect-ratio layouts together. |

### Special visibility-only controls

The following groups intentionally **do not expose X/Y, anchor, or scale editing**, matching the current Windows runtime contract:

| Category | Group IDs |
| --- | --- |
| Global visibility | `all_native_ui` |
| Target selection | `battle_target_selection` |
| World-attached indicators | `world_markers`, `enemy_awareness`, `damage_numbers`, `damage_received`, `healing_numbers` |
| Background visibility | `menu_background`, `menu_animated_background`, `battle_menu_background`, `establishment_background`, `quest_background` |

`all_native_ui` is highlighted red and acts as the global HUD visibility switch. World-attached indicators do not have one fixed screen rectangle. Full-screen backgrounds retain their runtime-defined composition.

The existing non-visibility JSON fields of these groups remain intact when editing their visibility. A visible control does not establish that every underlying game-side binding is verified; check the selected group's information and validate the result in game.

### Visual references and placement

The editor includes several research-based preview references, including:

- A **seven-slot party-status group** using the Windows runtime envelope: X −40, Y 855, width 1892 and height 196 in the 1920 × 1080 logical reference frame.
- A **battle radial menu** whose marker uses the runtime bounds (X 673, Y 316, 511 × 448). Its inspector also retains the separate decoded `bm_topmenu/BM_BASE2` asset reference for comparison.
- A **760 × 180 dialogue-window reference** with an inferred centered screen position.

Known fixed bounds and anchor/scale calculations follow the Windows runtime. Other dynamic or local-space positions remain **preview/calibration references**. The markers use schematic artwork rather than the game's textures. Use in-game screenshots and tests to refine unverified placements. Subtitle movement remains explicitly unverified in game.

## Quick start

### Online

1. Open <a href="https://hoverbike51.github.io/SO5-HUD-Layout-Studio" rel="nofollow"><img src="https://camo.githubusercontent.com/faed9fa5201b528f62cb0e2069fb7cfea299bc459b282aa92030db22e30133b8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4f70656e2d53747564696f2d707572706c653f7374796c653d706c6173746963266c696e6b3d6874747073253341253246253246686f76657262696b6535312e6769746875622e696f253246534f352d4855442d4c61796f75742d53747564696f" alt="Open Studio" data-canonical-src="https://img.shields.io/badge/Open-studio-purple?style=plastic" style="max-width: 100%;"></a>
2. Select **16:9**, **21:9**, or **32:9**.
3. Select a HUD group from the left sidebar.
4. Edit permitted fields in **Element Inspector**, or drag the group on the canvas.
5. Click **Save As JSON** for the active profile, or **Export all · ZIP** for all three.

### Offline

Download `index.html`, then open it using **Chrome** or **Edge**. The app does not require a local web server.

### Import a preset

Click **Import JSON** and select up to three compatible layout files, with one file per aspect. A file replaces the in-memory profile associated with its `aspect` value. Every file is validated before any profile is replaced. Duplicate aspects or incompatible files reject the entire batch. Replacing unsaved work requires confirmation.

The bundled starting profiles contain **31 HUD groups per aspect ratio**. Studio 2.0 preserves those supplied layouts and provides a separate **31-group original-placement safety reset** for each aspect. **Restore original native HUD** resets placement and visibility; **Reset active JSON to imported values** restores the profile as it was imported. These actions are intentionally different.

## How to use the canvas

1. **Select** a HUD group in the left list, or click its marker on the canvas.
2. Choose the editing mode:
   - **Edit JSON offsets** — modifies the selected group's supported JSON layout fields.
   - **Calibrate reference positions** — moves the visual reference **without modifying JSON offsets**.
3. Choose a display resolution, or edit **WIDTH** and **HEIGHT**. Enable **Keep ratio** to retain the chosen aspect relationship.
4. Use **Fit** or the zoom controls if needed.
5. Enable **Grid**, **Base guides**, or **Only Selected** to make individual layout checks easier.
6. Enable **Lock inside canvas** if you do not want interactive edits to put markers off-screen.

The canvas uses the JSON's `logical_1080_anchor_relative` unit convention. Changing the preview resolution does **not** convert `offset_x` or `offset_y` into raw display pixels or add resolution fields to the game JSON.

### Keyboard and navigation

- **Arrow keys** — move a selected editable group by one logical unit.
- **Shift + arrow keys** — move it by ten logical units.
- **Ctrl + Z** — Undo.
- **Ctrl + Y** or **Ctrl + Shift + Z** — Redo.
- **Escape during a drag** — cancel that drag and restore its initial state.

Command-key Undo/Redo shortcuts are also recognized where supported. A completed drag creates one undo entry.

Some commands are not applicable to visibility-only groups. Check the on-screen status for the active editing mode.

## JSON compatibility and integrity

The current editor targets HUD-layout JSON objects with this general structure:

```json
{
  "schema_version": 1,
  "layout_map": "so5-cusa03219-01.00-hud-research",
  "title_id": "CUSA03219",
  "app_ver": "01.00",
  "name": "My SO5 HUD Preset",
  "aspect": "16:9",
  "units": "logical_1080_anchor_relative",
  "groups": [
    {
      "id": "party_status",
      "anchor": "original",
      "offset_x": 0,
      "offset_y": 0,
      "scale": 1,
      "visible": true
    }
  ]
}
```

> The example shows the expected **field structure**, not the complete 31-group preset. Use the app's bundled layouts or your compatible source JSON for actual editing.

The editor validates imported layouts and exported JSON, preserves group identity and count, and restricts edits to supported layout fields plus the preset `name`. Unmodified JSON can be exported without changing its existing structure and formatting.

### Supported schema and limits

- **Schema 1**: group transforms and visibility.
- **Schema 2**: also preserves existing `elements` overrides.
- **Schema 3**: also preserves existing `reference_output` dimensions.
- Compatibility target: `CUSA03219`, APP_VER `01.00`, layout map `so5-cusa03219-01.00-hud-research`.
- Maximum preset size: **1 MiB**; maximum JSON nesting depth: **16**.
- Imported profiles contain **1–31 known, unique group IDs**. Existing element overrides are preserved, with a limit of 4096 entries.
- `offset_x`: **−3840 to +3840** logical units; `offset_y`: **−1080 to +1080**.
- `scale`: **0.5–2.0**. All numbers must be finite; visibility must be boolean.
- Preset names: **1–64 Unicode characters**, at most 256 UTF-8 bytes, without control characters or invalid surrogate sequences.
- Duplicate JSON member names, duplicate group IDs, unknown properties and unsupported transforms are rejected.

The HTML editor does not provide an individual-element authoring interface. Existing `elements` and `reference_output` data are retained unchanged. Changing the preview canvas size does not rewrite schema 3 reference dimensions.

**Always keep a backup** of working in-game presets. A syntactically valid JSON export does not establish that every game-side hook, HUD group, or placement works at runtime.

## Screenshot and calibration workflow

1. Select the corresponding aspect ratio and resolution.
2. Choose **Load screenshot** and import a PNG, JPEG or WebP image, up to 24 MiB and 40 megapixels.
3. Adjust its opacity to compare HUD groups and the background image.
4. Choose **Calibrate reference positions**.
5. Move the preview markers to match the screenshot.
6. Choose **Save calibration** to export those references separately.
7. Use **Import calibration** to restore them on another browser or PC.

Calibration reference positions are also stored in browser `localStorage` when available. They are **not** automatically written into the actual layout JSON. Clearing browser site data can delete locally stored calibration; export a calibration backup when the results matter.

## Save and export

- **Save As JSON**: validates and exports the active profile. Chrome/Edge may offer the native Windows **Save As** dialog; the suggested starting directory is **Downloads**, but the browser controls the actual location. When that API is unavailable, the normal download workflow is used.
- **Export all · ZIP**: bundles all three validated ratio-specific layouts.
- **Preset name**: changes the active layout's JSON `name` field; it can also influence the proposed file name.
- **Reset active JSON to imported values**: restores the selected aspect's imported values after confirmation.
- **Restore original native HUD**: restores original placement and visibility for every group present in the active layout. It does not reset preview calibration.

ZIP exports use separate filenames for each aspect. Native Save As cancellation leaves the layout unsaved. The fallback requests a browser download; confirm that the file was actually saved, since the editor cannot confirm a browser-controlled download destination.

## Unsaved changes and local recovery

The status indicator distinguishes unsaved changes from values that merely differ from the imported preset. Supported browsers can warn before leaving or reloading a page with unsaved changes. The browser controls that warning's appearance and whether it is displayed.

When browser storage is available, unsaved layouts are copied to local recovery storage. On a later visit, **Restore local recovery copy** offers to recover them. **Discard earlier recovery** removes that previous copy after confirmation. Startup does not silently overwrite an earlier recovery copy.

Recovery is a convenience, not a replacement for exported files. It is specific to the browser profile and site origin; it is not synchronized across computers or browsers. Storage restrictions, clearing site data or using private browsing may prevent persistence. Export your JSON and calibration before changing browser, profile or site domain.

## Privacy and requirements

- All editor processing takes place in your browser; the current application does not include a backend or a feature for uploading your imported JSON to a server.
- Imported game screenshots are processed locally for the on-page preview.
- GitHub Pages is a public hosting service, and GitHub may process ordinary site-visitor metadata under its own privacy terms.

## What's new in 2.0

- Runtime-aligned anchors, scale pivots, bounds and visibility-only restrictions.
- Original-placement safety resets for all 31 groups, separate from imported-layout resets.
- Strict schema validation and atomic multi-file imports.
- Reliable direct numeric editing, drag cancellation and undo/redo.
- Full scaled-rectangle canvas locking and clearer off-canvas handling.
- Unsaved-work warnings, local recovery and themed confirmations.
- Correct aspect association for delayed screenshot loads and file saves.
- Improved responsive layout, keyboard focus and fitted-canvas captions.
- Verified JSON preservation and ZIP exports.

The delivered version passed **25 automated browser scenarios** covering local HTTP deployment, standalone offline use, JSON validation, editing, exports, asynchronous operations and recovery. Layout checks covered 1024 × 768, 1366 × 768, 1920 × 1080 and 2560 × 1440. These checks do not replace gameplay validation of the exported layouts.

## Known limitations

- The canvas is a **layout preview, not live game rendering**. This HTML editor does not directly apply changes to a running game. Export a preset and use the game's existing HUD layout workflow.
- Some native HUD elements are unmapped, visibility-only, or have unverified game-side bindings.
- The 31-group safety reset supplies original relative transforms; it is not a complete set of absolute screen coordinates for every dynamic HUD element.
- Visual bounding boxes are based on available research, decoded UI information, and screenshots; not all are confirmed in-game.
- Different game versions, executables, or hooks may behave differently from this research profile (`CUSA03219`, `01.00`).
- GitHub Pages alone does not provide user accounts or a shared server-side preset database; downloaded presets remain files unless an additional service is added.
- All-filter groups can overlap because they represent different game contexts. Use category filters or Only Selected for precise editing.
- No universal sub-3-ms response-time guarantee is implied; browser scheduling, refresh rate and device load affect visible response.
- Mobile editing is not included; use a desktop-size browser window.

## Related project and credits

**Studio development and attribution:** Hoverbike51 — [GitHub profile](https://github.com/Hoverbike51)

**Associated research/Windows port:** [Star Ocean 5 — PS4RT Windows project](https://github.com/Hoverbike51/Star-Ocean-Integrity-and-Faithlessness-PS4RT)

This tool is an **unofficial fan/research utility** and is not affiliated with or endorsed by **Square Enix** or **tri-Ace**. *Star Ocean*, its characters, logos, game code, and original assets remain the property of their respective rights holders. Do not upload proprietary game assets to this repository unless you have permission to distribute them.

## License

**Proposed license: [MIT](LICENSE)**, for the original source code of this HUD editor. It permits use, modification, and redistribution while requiring retention of the copyright and license notices. The MIT license **does not transfer ownership or grant redistribution rights** over Star Ocean game assets, third-party trademarks, or other material you do not own.

**Copyright © 2026 Hoverbike51.**

