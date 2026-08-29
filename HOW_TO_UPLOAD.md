# Getting this onto GitHub (phone-friendly, no Termux / git CLI needed)

## One-time setup

**1. Create the repo.**
On github.com (works fine from your phone's browser), tap **+ → New repository**.
Name it something like `mama-rosas-app`. Public or private, your call. Don't
add a README/gitignore/license on the creation screen — leave it empty.

**2. Turn on write permissions for Actions** (needed once, or the two
workflows below can't commit/publish anything):
Repo → **Settings → Actions → General** → scroll to **Workflow permissions**
→ select **Read and write permissions** → **Save**.

**3. Upload this whole project.**
Unzip the project folder I sent you (any file manager, e.g. MiXplorer, can
unzip). From the repo's main page: **Add file → Upload files**, then add
everything — the `.github` folder, `android` folder, `www` folder, `incoming`
folder, and the loose files (`package.json`, `package-lock.json`,
`capacitor.config.ts`, `.gitignore`) — the same way you've uploaded folders
for your other Android projects before. Type a commit message like "Initial
commit" and hit **Commit changes directly to the main branch**.

**4. Watch it build.**
Go to the repo's **Actions** tab — a "Build APK" run should already be in
progress (it starts automatically whenever `android/` or `www/` changes,
which they just did). Give it a couple of minutes.

**5. Get the APK.**
Once that run finishes, go to the repo's **Releases** page (right sidebar
on the repo's main page, or `github.com/<you>/<repo>/releases`). There's a
release tagged **latest** with `MamaRosas-debug.apk` attached — tap it to
download straight to your phone, then open it with your file manager
(MiXplorer, etc.) to install.

**Bookmark this link** — it always points at the newest successful build,
so you never have to go hunting for it again:

    https://github.com/<you>/<repo>/releases/latest/download/MamaRosas-debug.apk

(swap in your actual GitHub username and repo name)

## Every time after that (updating the menu, theme, photos, etc.)

When I send you a new zip of the app's web content:

1. Go to the repo's **incoming** folder → **Add file → Upload files** →
   select the zip → commit straight to main.
2. That's it. The **Unzip Web Assets** workflow notices the new zip,
   extracts it into `www/`, deletes the zip, and commits — which
   automatically kicks off **Build APK** right after. A couple minutes
   later, `releases/latest` has the refreshed APK.

You never need to unzip anything yourself, and you never need to touch
`android/` for a normal content update — that folder only changes when the
app's native behavior itself changes (a new feature, not a menu/photo/theme
edit), which I'll walk you through separately if it ever comes up.

## If something doesn't build

Open the failed run under the **Actions** tab and send me a screenshot of
the red step — that's exactly what I need to fix it.
