# Assignment checklist and submission guide

## Implemented in this folder

- React frontend and Python FastAPI backend.
- Elexon FUELHH WIND actuals and WINDFOR forecast publication history, January 2026.
- Quantified forecast errors with an explicit day-ahead forecast selection cutoff.
- Downloaded source tables and the default-cutoff hourly comparison as CSV files under `backend/data/`.
- Dockerfile and Docker Compose.
- README, methodology notes, demo outline, and deployment instructions.
- Requirement-by-requirement audit with assumptions and outstanding submission steps.
- AI assistance disclosed in the README.

## Still needs your account and personal action

The brief requires a public GitHub repository, an app hosted on Vercel or Heroku, an unlisted YouTube demo (maximum ten minutes, split into two parts), and Microsoft form submission. These public release and submission deliverables are separate from the local source files in this folder. Review and understand the project before publishing it and recording the pitch.

1. Review the app and this code. Run it locally and understand the metrics.
2. Create a GitHub account if needed. Create a new **public** repository with a random, non-identifying name. Do not put your name, email, API secrets, or private client data in the repository.
3. Push this folder to GitHub. In PowerShell from this folder:

   ```powershell
   git init
   git config --local user.name "Your non-identifying author name"
   git config --local user.email "Your GitHub noreply address"
   git add .
   git commit -m "Build wind forecast accuracy dashboard"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-RANDOM-REPO.git
   git push -u origin main
   ```

   Git commit author details are visible in a public repository. Use an identity
   that matches the assignment's anonymity requirement; do not use your personal
   email address. GitHub provides a noreply address in account settings.

4. Deploy the app by following [`deployment.md`](deployment.md). After deployment, add the public app URL to the README.
5. Record a maximum-ten-minute demo. The supplied [`demo-run-sheet.md`](demo-run-sheet.md) gives a suggested 4-5 minute customer section and 4-5 minute technical section. Upload to YouTube as **Unlisted**.
6. Open the repository, app, and video in a private/incognito browser window. Check that all load without signing in.
7. Complete the [Microsoft submission form](https://forms.cloud.microsoft/r/FTX6K2bbnU) with the repository, deployed app, and video links.

## Docker in plain language

Docker packages the frontend and backend in a repeatable container, so the same app can run on your laptop and on a hosting service. Install Docker Desktop for Windows and start it. You can use `docker compose up --build` without making a Docker account. An account is useful if you later publish a container image to Docker Hub, but this deployment path does not need that.

## Heroku in plain language

Heroku is a hosting service that runs your app on the internet. For this Docker project, create/verify an account, install the Heroku CLI, then use the container deployment commands in [`deployment.md`](deployment.md). Heroku provides a public URL you can share and bills deployed resources by usage. Vercel is another permitted host, but this app's single-container setup is documented for Heroku. See [`deployment.md`](deployment.md) before choosing a host.
