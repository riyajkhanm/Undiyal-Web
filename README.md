# Undiyal – web app (Android, iPhone, Windows, Mac)

Runs in any modern browser, installs like an app, works offline, and can sync each person's
data to **their own Google Drive** (hidden app-data folder, only visible to this app + that account).
The code is public; nobody's data is. There is no server.

Your site address will be:  https://riyajkhanm.github.io/Undiyal-Web/

## Part 1 – Put the app online (GitHub Pages)
1. github.com → **+** → **New repository** → name `undiyal` → **Public** → Create.
2. **uploading an existing file** → drag in everything from this folder
   (`index.html`, `config.js`, `manifest.webmanifest`, `sw.js`, the `icons` folder) → Commit.
3. **Settings → Pages** → Source: **Deploy from a branch** → Branch **main**, folder **/ (root)** → Save.
4. After ~1 minute the address above works.

## Part 2 – Google setup (one time, for the owner only)
1. Go to console.cloud.google.com → project selector → **New project** → name `Undiyal` → Create.
2. **APIs & Services → Library** → search **Google Drive API** → **Enable**.
3. **Google Auth Platform** (or APIs & Services → OAuth consent screen) → **Get started**:
   App name `Undiyal`, your email, Audience **External**, your email as contact → Create.
4. **Data Access → Add or remove scopes** → tick
   `.../auth/drive.appdata` ("See, create and delete its own configuration data in your Google Drive") → Update → Save.
5. **Audience → Publish app** (so it says *In production*). This scope is low-risk, so no Google review is needed.
   If you leave it in *Testing*, only people you add by hand can sign in, and they are signed out every 7 days.
6. **Clients → Create client** → type **Web application** →
   * Authorized JavaScript origins: `https://riyajkhanm.github.io`
   * Authorized redirect URIs: `https://riyajkhanm.github.io/undiyal/`
   → Create → copy the **Client ID** (ends with `.apps.googleusercontent.com`).
7. In your GitHub repo open `config.js` → pencil icon → paste the Client ID between the quotes → Commit.
   (Google can take a few minutes to start accepting a new client.)

## Part 3 – Each person
* **Android:** open the address in Chrome → ⋮ → **Install app**.
* **iPhone/iPad:** open it in **Safari** → Share → **Add to Home Screen**.
* **Windows/Mac:** open it in Chrome or Edge → install icon in the address bar.
* Inside the app: **Settings → ☁ Cloud sync → Sign in with Google**. Use the same Google account
  on every device that should show the same data.

## Good to know
* Google sign-in lasts about an hour. After that, tap the ☁ line on the Home screen once to continue.
  Changes made meanwhile stay on the device and sync then.
* Syncing merges changes from several devices (new, edited and deleted entries). If the same entry is
  edited on two devices, the most recent edit wins.
* iPhone: the installed app and Safari keep separate data. Use the installed one, and use Cloud sync or
  Settings → Backup for safety.
* To remove your cloud data: Settings → ☁ Cloud sync → **Delete my cloud copy**, or revoke access at
  myaccount.google.com/permissions.
* To update the app later: replace `index.html` in the repository.
