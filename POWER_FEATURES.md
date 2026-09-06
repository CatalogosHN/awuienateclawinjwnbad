# HeliBoard Power – productivity fork

This fork keeps the HeliBoard keyboard engine and adds a productivity layer focused on fast customer support and repetitive typing.

## Added in power1

- Unlimited quick replies stored locally in SQLite (limited only by device storage).
- Quick reply fields: title, content, category, tags, favorite, manual order index, use count, last used, created/updated timestamps.
- Quick reply manager in Settings with add/edit/delete/search.
- Quick reply search from the keyboard toolbar.
- Category filters in quick reply search.
- Template variables such as `{cliente}` / `{precio}` (prompted before insertion).
- Built-in variables: `{fecha}` / `{date}`, `{hora}` / `{time}`, `{portapapeles}` / `{clipboard}`.
- Clipboard text search from the clipboard toolbar.
- Clipboard retention defaults to **No limit**.
- Clipboard file-size limit defaults to **No limit** (actual device storage is the real limit).
- Existing HeliBoard pinned clipboard entries remain supported.
- Quick replies are included in HeliBoard's existing database backup/restore flow.
- Separate application id (`helium314.keyboard.power`) so it can coexist with official HeliBoard.
- GitHub Actions builds an installable debug APK on push, pull request, or manual run.

## Build from GitHub

1. Create a new GitHub repository.
2. Upload/push the complete project contents (the folder containing `gradlew`).
3. Open **Actions** → **Build installable APK**.
4. Run the workflow manually, or push to `main`/`master`.
5. Open the completed workflow and download the `HeliBoardPower-debug-apk` artifact.
6. Extract the artifact ZIP and install the APK on Android.

## Local build

```bash
./gradlew assembleDebug
```

APK output:

```text
app/build/outputs/apk/debug/
```

## License

This is a derivative of HeliBoard and remains subject to the upstream GPL-3.0 licensing requirements. Keep source code available when distributing binaries.

## power1 scope / next modules

This first build contains the complete local productivity core: quick replies, variables, search, categories/tags/favorites, usage sorting, manual reorder, searchable persistent clipboard, and backup/restore.

Not included in `power1` yet:

- Live cloud synchronization (Drive/WebDAV/custom server).
- Online translation provider integration.
- Content/OCR search inside clipboard images; image/file clipboard items still remain available in HeliBoard's normal clipboard UI.

These are intentionally left as separate modules so the first GitHub build can validate the keyboard/IME integration before adding network permissions or external services.

## Validation note

The project XML, string resources, toolbar mappings, and GitHub Actions workflow were statically validated in the preparation environment. A full local Gradle build could not be completed there because the sandbox cannot reach `services.gradle.org`; GitHub Actions is configured to perform the real Android build.
