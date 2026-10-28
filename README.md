# ShowSync — Plan. Share. Perform.

An original entertainment-calendar Progressive Web App (PWA) prototype, designed for show bookings, rehearsals, radio shifts, production tasks, memos, and personal schedules.

## Included in this build
- Responsive calendar with month, week, day, and list views
- Multiple colour-coded calendars and calendar filters
- Event create/edit/delete, location, production notes, all-day flag, and reminder preference
- Task checklist, memos, activity feed, quick memo, search
- Personal accent colour and week-start preferences
- Local JSON export/import
- PWA manifest, service worker, and custom iPhone Home Screen icon
- Optional Firebase Email/Password sign-in and Firestore private-workspace sync scaffold

## Run locally
Because Firebase SDK modules load from Google's CDN, use a local web server rather than opening `index.html` as a `file://` URL. For example:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080` in a browser.

## Publish on GitHub Pages
1. Create a repository and upload the contents of this folder to the repository root.
2. In GitHub, open **Settings → Pages** and publish from the `main` branch and `/ (root)`.
3. Open the HTTPS GitHub Pages URL in Safari on iPhone.
4. In Safari, tap **Share → Add to Home Screen**.

## Firebase setup for cloud sync
The cloud sync scaffold is not active until you configure your own Firebase project:
1. Create a Firebase project.
2. Enable **Authentication → Email/Password**.
3. Create a **Cloud Firestore** database.
4. Register a Web app and copy its Firebase config.
5. Publish the app over HTTPS, enter the config JSON and credentials under **Settings & sync**, then connect.
6. Add and test Firestore security rules before using real data.

The scaffold writes the signed-in user's data to `users/{uid}/workspace/main`. This is a private single-user workspace, not a complete shared-calendar membership/invitation system. Do not loosen Firestore rules to public read/write. Multi-user sharing requires a proper calendar membership model, invitation flow, and membership-enforcing rules.

## Important limitations
- This is an original starter app, not a pixel-for-pixel copy of TimeTree.
- Data is local by default; cloud sync is optional and needs Firebase setup.
- Browser notifications are device/browser-dependent. The current reminders are scheduled while the page's JavaScript remains alive; this is not reliable background push delivery. True cross-device push notifications require a push service (for example Firebase Cloud Messaging), service-worker push handling, and server-side scheduling.
- This prototype does not yet implement production-grade shared-calendar invitations, live chat, shared albums/file uploads, external calendar import/sync, native widgets, or server-scheduled notifications.
- Do not store sensitive contracts or personal data until authentication, access rules, backups, and deployment security have been reviewed.
