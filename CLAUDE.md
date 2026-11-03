# Study Buddy (joshistudies.in)

Exam-prep web app for a Class 9 student. GitHub Pages serves `index.html` from `main`.

## The file

`index.html` is the whole app: plain HTML, CSS and JavaScript in one file.

- Until November 2026 it was a self-unpacking bundle: the app was stored as a JSON string inside
  `<script type="__bundler/template">` and rebuilt in the browser on every visit. That made phones
  slow to open the app, so the wrapper was removed. **Do not wrap it again**, and do not look for
  the template: edit `index.html` directly.
- All `<style>` blocks are in `<head>`, in cascade order. Add new CSS as a new `<style>` block at
  the end of `<head>`.
- The app's scripts sit at the end of `<body>`. The Firebase module script is in `<head>` and runs
  after them.
- `#sbBoot` is the loading tile ("Getting your desk ready…"). The small script after the app's last
  script removes it. Keep that script last.
- Keep the app in one file. Split files could reach a phone as a mix of old and new versions.

## Every change

- Bump `APP_VERSION` (search for `const APP_VERSION`). The sign-in screen and the admin bar show
  it, so you can tell which build is live.
- Pull first, because several sessions push to `main`.
- The lessons and all of the student's progress live in Firestore, not in this file. Never put
  passcodes in the file: it holds salted hashes only.
