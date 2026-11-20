# Rebar3D

**Learn reinforcement detailing in 3D.**

A browser-based reinforced concrete (RCC) teaching and screening aid. Create and edit member schedules, review quantity estimates and detailing checks, inspect reinforcement in 3D, and export project data and models.

## Features

- Teaching build-up mode for concrete outline, main bars, links/ties, secondary bars, and the complete cage.
- Worked cut-length, total-length, and bar-mass calculations for the selected member.
- One-click beam, cantilever, tied-column, and one-way-slab textbook examples.
- Hidden-answer schedule exercises with answer feedback that does not reveal the expected values, plus a printable assignment worksheet.
- Class/projector display mode with larger labels and controls.
- Beam, column, retaining wall, footing, and slab schedules.
- Concrete and reinforcement quantity estimates, a printable/copyable BBS with descriptive bar profiles and dimensions, and cost estimates using entered rates.
- Member-level input validation and IS 456 detailing checks. These checks are informational and are not a substitute for structural design review.
- Optional IS 13920:2016 beam/column detailing screens for selected Zones III–V, plus preliminary simply supported UDL beam action/capacity screens when a factored load is entered.
- Interactive 3D member views with overlap-aware annotations, section/side/top views, measurement, explode, concrete/rebar visibility controls, fit/reset view, PNG export with labels and legend, and selected-member DXF export.
- An illustrative 1–4 bay X/Z assembly preview placing selected footings, columns, beams, and slab panels together; a selected wall is shown beside the frame.
- Schedule search, sort, error filtering, inline edits, and pagination.
- A millimetre/inch display toggle for dimension fields, schedule geometry, and 3D labels. Calculations and data exports remain in the app's standard metric units.
- An on-demand first-fit decreasing cutting plan for 12 m stock bars, grouped by diameter, with waste estimates and copyable cut patterns.
- Undo and redo for supported project edits.
- Import/export of complete project JSON files; compressed project links when the app is hosted on HTTP(S); CSV import and copy for the selected member type.
- Print-friendly project report with quantities, rates, BBS, and member-level checks.
- Automatic saving to the browser's local storage.
- Responsive mobile layout with the 3D view above Input / Results / Checks panels, touch orbit and pinch zoom, and reduced rendering detail on small screens.
- A minimal landing page with an embedded, slowly rotating live beam demo and section/explode controls.

## Run the app

No build step or package installation is required.

1. Download or clone this repository.
2. Open `index.html` for the landing page or `rcc_3d_schedule_app.html` to launch the app directly.
3. Use the controls to edit member data, review quantities, and inspect the 3D model.

The pages load Three.js and IBM Plex Sans from CDNs, so an internet connection is needed for those external resources. For the landing page's live demo, serve the repository over HTTP(S); browsers do not reliably load a local HTML file in an iframe. Project data is saved in the current browser profile; use **Save JSON** to keep a portable project backup or move it to another browser. For share links, first host the app on an HTTP(S) site; opening the file directly cannot create a portable link.

## Using the schedule

- Choose a member type from the tabs, then add, duplicate, delete, or edit members.
- Search by mark or dimensions. Sort by schedule order, mark, size, member count, or steel weight; filter to valid rows or rows with input errors.
- Edit marks, geometry, and member counts directly in the schedule, or use the member details fields.
- Use **Undo** and **Redo** (also `Ctrl+Z` and `Ctrl+Y`) to recover supported changes.
- Click an input validation error to jump to its field. Detailing warnings are shown separately.
- Choose a textbook example and load it as a starting point. Use **Build-up mode** to step through the reinforcement layers, **Worked calculations** to inspect the app's arithmetic, or **Class / projector mode** for larger controls and labels.
- **Start hidden-answer exercise** presents a schedule prompt and checks entered bar values without disclosing the expected values. **Print one-page assignment** creates a blank worksheet for class.
- Select a seismic zone to activate the limited seismic screens where available. For beam action checks, enter a **factored** full-span UDL; the model assumes a simply supported beam and applies no additional load factors.

## Project and schedule files

- **Save JSON / Open JSON:** export or restore the complete project, including all member schedules and settings. Opening a project replaces the current project after confirmation; the replacement can be undone.
- **Share link:** copy a compressed URL fragment containing the complete project. The recipient must be able to access the same hosted app page and confirm the import. The project data is readable by anyone who receives the link; do not share sensitive project data this way. Large projects may exceed the URL size limit; use JSON files instead.
- **Import CSV / Copy CSV:** import or copy a schedule for the currently selected member type. CSV import adds rows to that schedule; it does not replace the complete project.
- **Copy summary for Excel:** copy project quantities and the full BBS as tab-separated text.
- **Optimize 12 m cuts:** create and copy a per-diameter stock-bar cutting plan. It is an estimate and excludes saw kerf and splice design.
- **Print / PDF:** open the browser print dialog for the project report.
- **Export DXF:** export the selected member as a faceted 3D DXF model in millimetres. Concrete and reinforcement are assigned to separate layers. A retaining wall export uses its full entered length, even when the 3D preview is shortened.

## Notes and limitations

- The textbook presets are illustrative classroom examples, not engineered designs. Preset reinforcement is not proof of adequacy for any real structure.
- Worked calculations explain this app's formulas and simplifying assumptions. They are intended for teaching and should be compared with the applicable standard, drawings, and instructor guidance.
- Hidden-answer exercises are client-side learning checks, not secure assessment or anti-cheating controls. Their example data is delivered to the browser.
- Quantities and costs are estimates derived from the entered geometry, reinforcement, member counts, and rates. Check project inputs and assumptions before using exported results.
- BBS profile labels are descriptive app references, not official IS 2502 shape codes. The displayed profile dimensions and cut lengths use simplified assumptions; no fabrication-ready hook, bend-radius, anchorage, or splice schedule is produced. Verify every cut against approved drawings and site requirements before fabrication.
- Stock-bar optimization uses a first-fit decreasing heuristic, rounds cuts up to whole millimetres, and reports pieces longer than 12 m separately. It does not account for saw kerf, stock availability, or designed splices.
- Detailing checks are not a structural analysis or design approval. The IS 13920:2016 and UDL features are limited screening aids, not complete detailing or capacity design. Verify applicable standards, project requirements, and calculations independently with a qualified structural engineer.
- Seismic checks are limited IS 13920:2016 screening rules for selected beam/column members; they do not establish seismic-zone applicability or check joints, system classification, ductility analysis, complete confinement, lap zones, or strong-column/weak-beam behavior. Zone II is not assessed.
- UDL calculations are preliminary rectangular singly reinforced beam screens only. The entered UDL must already be factored and include all loads. The flexural screen ignores compression reinforcement and flange action; the shear check compares average shear stress to a code upper-bound stress and does not calculate concrete-plus-stirrup shear capacity. Do not use these results as a design certificate.
- DXF geometry is exported as faceted 3DFACE entities, not native AutoCAD solid objects.
- The assembly preview uses schematic placement based on repeated copies of the selected beam span and member types; it is not a coordinated structural model, and project quantities remain member-level regardless of displayed bay counts.
- Browser local storage is specific to the browser profile and device. It is not a shared or cloud backup; export JSON regularly for safekeeping. Share links embed the project in the URL fragment; although the fragment is not sent in normal HTTP requests, anyone with the full link can inspect its project data.
- The app uses external CDN-hosted Three.js and font resources. Their availability and terms are controlled by their respective providers.
- The mobile layout and touch interactions were checked in browser viewport emulation, not on a physical Android device. Rendering speed and touch behavior should be validated on the target phones before classroom/site deployment.

## Project links

- Landing page: [`index.html`](./index.html)
- Application: [`rcc_3d_schedule_app.html`](./rcc_3d_schedule_app.html)
- GitHub: <https://github.com/Pranit-satnurkar/Rebar3D>
