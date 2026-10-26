# Assignment requirements audit

This audit distinguishes the assignment's required behavior from implementation assumptions and submission work that still requires the owner's accounts.

| Assignment requirement | Implementation / evidence | Status |
| --- | --- | --- |
| React frontend and Python backend | `frontend/src/` and `backend/app.py` (FastAPI) | Implemented |
| Show latest wind forecast available for day-ahead decisions | Filters WINDFOR history by `publishTime`, selecting the latest issue no later than the chosen previous-day cutoff | Implemented with an explicit cutoff assumption |
| Quantify forecast accuracy | MAE, RMSE, signed bias, and WAPE over matched observations | Implemented |
| Actuals from Elexon FUELHH, `fuelType=WIND` | Downloader filters FUELHH records to WIND; snapshot and actuals CSV are in `backend/data/` | Implemented |
| Forecasts from Elexon WINDFOR | Downloader uses the assignment-linked `datasets/WINDFOR/stream`, filtered by publication time to retain forecast versions for replay | Implemented |
| January 2026 purchase decisions | Decision dates Jan 1–31; delivery data Jan 2–Feb 1. Jan 1 delivery is omitted because its day-ahead decision was Dec 31 | Implemented using the wording in the brief |
| Comparable actual/forecast periods | For the January 2026 query, the specified WINDFOR stream returned hourly target timestamps. Two 30-minute FUELHH actuals are averaged to the matching hour | Partially met: the brief implies 30-minute targets for both, but the linked WINDFOR feed returned hourly targets; within-hour error is not measured |
| Docker | Multi-stage Dockerfile and Compose; local build and endpoints verified | Implemented and verified locally |
| README with file list, run steps, deployment link | README lists files and startup steps; public app URL must be added after deployment | Partly complete |
| Public anonymous GitHub repository | No public repository has been created or linked | Owner action required |
| Vercel or Heroku deployment | Local Docker app runs; no public host deployment has been made | Owner account/action required |
| Two-part unlisted YouTube demo, max ten minutes | Recording outline is in `demo-run-sheet.md`; no video has been recorded or uploaded | Owner action required |
| Microsoft submission form and incognito URL checks | Form is linked in the checklist; no form has been submitted and no public URLs exist to verify | Owner action required |
| AI tools disclosed in README | AI assistance is disclosed | Implemented |

## Modeling assumptions

- The brief says decisions are made one day ahead but does not give a decision clock time. The dashboard defaults to 11:00 Europe/London on the prior day and lets the reviewer change that cutoff. Results can change when the cutoff changes.
- The brief identifies a 30-minute actual target and says forecast `startTime` is similar, which implies period-matched comparison. The assignment-linked WINDFOR stream was queried for January 2026 and returned hourly target timestamps (for example, every target in a Jan 1 publication response was on the hour). Until a half-hourly forecast field is available from the required source, the app compares hourly mean actual generation with the hourly forecast and documents this limitation; it does not repeat a forecast into half-hour periods.
- Metrics describe wind-generation forecast errors only. They do not estimate demand, residual load, purchase volume, price, or cost.
