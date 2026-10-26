# Demo run sheet (maximum 10 minutes)

Use your own words and screen-share the live deployed app and repository. Avoid claiming the dashboard recommends a purchase; demand and price are outside this pilot's data scope.

## Part 1 - customer overview (about 4 minutes)

1. **Problem (30 sec):** Day-ahead buyers need to assess how much weather-dependent wind generation may be available and how uncertain that estimate is.
2. **Dashboard (60 sec):** Point out January 2026 decision dates, the delivery-day filter, and the configurable prior-day cutoff assumption.
3. **Forecast (60 sec):** Explain that the default view selects the latest WINDFOR issue published by 11:00 Europe/London on the previous day. The brief does not specify a clock time; change the assumed cutoff and delivery day to show the view updates.
4. **Accuracy (60 sec):** Explain MAE, signed bias, and WAPE; show the forecast/actual lines and export a CSV.
5. **Scope (30 sec):** State that the pilot uses only Elexon wind records and is an input to wider trading judgement, not a standalone buy recommendation.

## Part 2 - technical review (about 4 minutes)

1. **Architecture (45 sec):** React/Vite frontend, FastAPI backend, local JSON snapshot, one Docker image.
2. **Data (60 sec):** Explain FUELHH `fuelType=WIND`, the assignment-linked WINDFOR stream, delivery `startTime`, publication history, UTC storage, and Europe/London cutoff.
3. **Method (60 sec):** Explain that the January 2026 WINDFOR stream response has hourly target timestamps, while FUELHH actuals are half-hourly. The app averages the two actual readings to hourly MW, uses only forecasts published before cutoff, and calculates MAE/RMSE/bias/WAPE on paired hourly points. State that this does not measure within-hour errors.
4. **Code and operations (45 sec):** Show `backend/fetch_data.py`, `backend/app.py`, React `src/App.jsx`, and `Dockerfile`; mention health endpoint and data refresh command.
5. **Limits (30 sec):** Explain that January is a historical pilot and that demand, market prices, generation constraints, and uncertainty bands were not requested.

Record both parts into one video, keep the total under ten minutes, upload to YouTube as Unlisted, then open the link in an incognito/private window to verify viewing access.
