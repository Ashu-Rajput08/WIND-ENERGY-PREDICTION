# Deploying the pilot

## Recommended: one Docker service

The app serves the built React website and `/api/...` endpoints from one FastAPI process. This keeps the browser/API origins aligned and avoids CORS setup.

1. First make sure `docker compose up --build` runs locally and that the app and `/api/health` work.
2. Create a GitHub public repository with an anonymous/random name and push this folder.
3. Create and verify your Heroku account. Current Heroku account verification requires a payment method for app creation and deploys; dynos are billed according to usage. Check the current plan and your billing page before leaving the app running.
4. Install Git, Docker Desktop, and the Heroku CLI. In PowerShell from this folder, run:

   ```powershell
   heroku login
   heroku create YOUR-RANDOM-APP-NAME --stack container
   heroku container:login
   heroku container:push web --app YOUR-RANDOM-APP-NAME
   heroku container:release web --app YOUR-RANDOM-APP-NAME
   heroku open --app YOUR-RANDOM-APP-NAME
   ```

   Heroku's official Docker route builds and pushes the image with its Container Registry. Keep the public GitHub repository as the source code submission; a Docker Hub account is not needed for this Heroku route.
5. Open the assigned HTTPS URL in a private browser window. Check the dashboard, `/api/health`, date controls, and CSV export.
6. Put that URL in the README and assignment form.

Heroku's account, billing, and deployment workflow may change. Read the official [Docker deployment steps](https://devcenter.heroku.com/articles/container-registry-and-runtime), [account verification requirements](https://devcenter.heroku.com/articles/account-verification), and [usage and billing](https://devcenter.heroku.com/articles/usage-and-billing) before proceeding. Deployment is optional until you are ready to submit; local Docker requires no paid hosting.

## Vercel alternative

Vercel supports FastAPI directly, but this project packages React static assets inside FastAPI for the single-container path. Splitting the frontend and backend across Vercel requires adding a Vercel build/output configuration and setting `VITE_API_URL` to the API's public base URL plus a matching backend `CORS_ORIGINS` value. Vercel's [FastAPI guide](https://vercel.com/docs/frameworks/backend/fastapi) explains the supported Python runtime and deployment. For a beginner following this project's existing Docker configuration, use the single Docker service above.

## Common terms

- **Repository**: the online folder containing your source code.
- **Build**: compiling React and installing the Python service dependencies.
- **Deploy**: starting the built app on a public host.
- **Environment variable**: a setting supplied by the host, such as `PORT`; never commit passwords or tokens.
- **Public URL**: the internet address the reviewer can visit.
