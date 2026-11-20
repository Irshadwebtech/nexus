# NEXUS AI — Personal Assistant (PWA)

A mobile-first, local-first browser assistant with configurable OpenAI-compatible chat, personal memory, task planner, weather, GPS, voice, contact dial shortcuts, WhatsApp message preparation, file picker, and GitHub Pages deployment.


## Run locally
1. Install Node.js 20+ from https://nodejs.org/.
2. Extract this project and open a terminal in its folder.
3. Run `npm install`
4. Run `npm run dev` and open the shown URL.

## Publish to GitHub Pages
1. Create a GitHub repository (for example `nexus-ai`).
2. Upload/push all project files to the `main` branch.
3. Open **Settings → Pages** and set **Build and deployment: GitHub Actions**.
4. The included `.github/workflows/deploy.yml` will build and deploy on push. Wait for the Actions workflow to finish, then open the Pages URL.

The workflow sets a relative Vite base path so the project can be hosted from a repository subpath.

## AI setup
Go to Settings inside NEXUS and configure:
- API endpoint: `https://api.openai.com/v1/chat/completions` (or your compatible provider's endpoint)
- Model: a model available to your API account
- API key: your key

**Security warning:** this is a static PWA. The API key is stored in browser local storage and is visible to that browser/user. This is acceptable only for personal testing with your own key; do not publish a key, use shared devices, or use this frontend pattern for a public service. A production app should proxy AI requests through a secured backend.

## Features and limits
- Memory, planner tasks, contacts, conversation and preferences persist in local browser storage. This does not sync between devices. Use Settings → Export backup to save a JSON backup.
- AI chat supports OpenAI-compatible function calling when the configured provider/model supports it.
- Weather uses Open-Meteo and requires network access. GPS requires HTTPS and browser permission.
- Voice input uses browser SpeechRecognition (support varies by browser); voice output uses SpeechSynthesis.
- Calling uses `tel:` and opens the phone dialer; user confirms call.
- WhatsApp action opens a message draft; user presses Send in WhatsApp.
- Files are selected manually using the browser file picker. NEXUS does not scan phone storage. Text files can be previewed in-app; images/PDFs open in browser where supported.
- Web/PWA cannot silently launch every installed native app, send messages, make calls, set native alarms, or run guaranteed background reminders.
- Service worker caches the app shell for limited offline access. AI and live weather need internet.

## Privacy and data
This project has no server database. Local records are stored in this browser's localStorage. Clearing site data removes records. Export a backup before switching browsers/devices. Keep personal data private and use Settings → Clear all local data when needed.
