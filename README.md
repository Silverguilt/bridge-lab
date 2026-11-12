# Bridge Lab

**An interactive 3D craft-stick bridge studio for learning through construction.**

BroLabbet helps students explore bridge geometry, manage a fictional materials budget and compare designs before building a physical model. It runs entirely in the browser, with Swedish and English interfaces and no build step, external dependencies or account requirement.

## Project origin

BroLabbet grew out of helping with a Year 7 school project about bridge construction. The practical challenge was to plan a bridge made from craft sticks while meeting dimensional requirements and staying within a materials budget. A visual planning aid evolved into an interactive building studio, with individual sticks, camera controls, automatic budgeting and an illustrative load comparison. It was developed iteratively with assistance from ChatGPT.

## Features

- Position individual 110 × 10 × 2 mm craft sticks in a 3D canvas.
- Orbit and zoom, or select side, opposite side, front, rear and top views.
- Drag sticks and rotation handles, or enter exact positions and angles.
- Duplicate and mirror members across the bridge.
- Track a fictional SEK 3,500,000 budget, with sticks at SEK 35,000 each.
- Record glue sticks, paper and string purchases.
- Explore Warren-style and Pratt-style construction sketches.
- Check approximate dimensions against a 40 × 10 × 15 cm target.
- Save locally, export/import project JSON and undo recent edits.
- Compare designs with an explicitly simplified geometry-based load score.

## Quick start

Requirements: a modern browser. Python 3 is optional for the recommended local server.

```sh
git clone https://github.com/Silverguilt/bridge-lab.git
cd bridge-lab
python3 -m http.server 8000 --bind 127.0.0.1
```

Open http://localhost:8000 and choose **Svenska** or **English**. Direct routes are `/sv/` and `/en/`.

Alternatively, open `index.html` directly. No package installation is needed. Browser storage behavior for `file://` pages varies, so a local server is recommended for reliable persistence.

## Using the studio

1. Add a stick, or choose a template. Each new manual placement is charged automatically.
2. Select a member and drag it, use its blue rotation handle, or enter coordinates.
3. Use the layer selector and mirror tool to build both sides and cross bracing.
4. Check dimensions and remaining budget.
5. Set the illustrative load and run the comparison.
6. Export your project as JSON to keep a portable backup.

Deleting a member does not refund its purchase. Undo reverses a recent change. Templates retain existing purchases and charge only for a shortfall in stock. Clearing the workspace preserves the materials budget.

## Simulation limitations

The load laboratory is an **educational heuristic, not structural engineering software**. Its score uses member counts, orientations, approximate dimensions and bracing checks. The displayed deflection is derived from that score; it is not a beam or finite-element solution.

The app does not solve connectivity, force equilibrium, glue strength, buckling or real failure loads. Members that appear to meet are not necessarily connected. Templates are sketches, not verified construction drawings. Displayed sticks use a simplified canvas rendering; dimensions are evaluated from member centerline endpoints.

A reported pass does not establish that a physical bridge can carry the selected load. Physical performance must be checked through appropriately supervised experiments.

## Files and data

```text
index.html       Language selection
sv/index.html    Swedish studio
en/index.html    English studio
README.md        Project and setup documentation
```

Both language versions use the same project schema and the `brolabbet-03` browser-storage key on the same origin. This lets users switch language while retaining their design. Exported files contain `{ "version": 2, "project": ... }`. Existing BroLabbet 0.3 exports remain compatible.

Everything is processed locally. No analytics, remote scripts or network services are used. Browser storage can be cleared by the browser; exported JSON files are the recommended backup. Import only trusted BroLabbet project files; this prototype does not yet provide comprehensive schema validation.

## Development

The studio uses plain HTML, CSS and JavaScript with Canvas 2D projection of 3D coordinates. Edit the HTML files and refresh the browser. Keep behavior and translations aligned between both language versions.

Useful future improvements include shared application modules, stronger project validation, explicit joint modeling and calibration against physical test samples.
