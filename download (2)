# Bow Hub Catalog

The official catalog and content repository for **Bow Hub**.

Bow Hub is a Windows desktop application designed to give users one place to discover, install, update, launch, and learn about software and projects built by Bow.

This repository is intentionally separate from the Bow Hub desktop application's source code. Bow Hub reads this repository remotely so new projects, categories, development-status changes, icons, banners, and custom project pages can be published **without releasing a new version of Bow Hub**.

## How it works

Bow Hub downloads `apps.json` when the application starts or refreshes the catalog. Each catalog entry tells Bow Hub what the project is, how it should be displayed, and where its releases can be found.

For applications hosted on GitHub, Bow Hub should use the project's **GitHub Releases** to determine the latest available version. This means normal application updates do not require editing `apps.json`.

Typical update workflow:

1. Update the program's code in its own repository.
2. Build the new installer.
3. Publish a new GitHub Release, such as `v0.4.0`.
4. Bow Hub checks GitHub Releases and detects the new version automatically.
5. Users with an older installed version are shown an available update.

The catalog only needs to be changed when adding a new project or changing catalog information such as its name, category, status, icon, display mode, repository, or links.

## Repository structure

```text
Bow-Hub-Catalog/
├── apps.json
├── categories.json
├── statuses.json
├── README.md
├── icons/
│   └── .gitkeep
├── pages/
│   ├── .gitkeep
│   └── example-app.html
├── assets/
│   ├── banners/
│   │   └── .gitkeep
│   └── screenshots/
│       └── .gitkeep
└── schemas/
    └── app.schema.json
```

## Project categories

Categories describe what type of project something is. They are separate from development status so users can filter by either one.

Initial categories include:

- Utilities
- Developer Tools
- Networking
- Privacy & Security
- Browser Extensions
- Web Tools
- Other

Categories are defined in `categories.json` and can be expanded later without changing the Bow Hub application, provided Bow Hub treats unknown categories dynamically.

## Development statuses

Bow Hub supports the following initial statuses:

- **Concept** — idea or design stage.
- **Prototype** — early proof of concept.
- **Alpha** — early development; bugs and missing features are expected.
- **Beta** — usable testing build that may still contain bugs.
- **Stable** — normal public release.
- **Deprecated** — still available but no longer recommended.
- **Archived** — no longer actively maintained.

Statuses are defined in `statuses.json`.

## App entries

A basic project entry looks like this:

```json
{
  "id": "example-app",
  "name": "Example App",
  "shortDescription": "A short description of the project.",
  "category": "utilities",
  "status": "alpha",
  "featured": false,
  "installable": true,
  "icon": "icons/example-app.png",
  "github": {
    "repo": "YOUR-GITHUB-USERNAME/Example-App",
    "releaseChannel": "stable",
    "assetMatch": ".exe"
  },
  "display": {
    "type": "generated"
  }
}
```

## Automatic version checking

For an app with a `github.repo` value, Bow Hub should request the latest eligible GitHub Release for that repository and compare its release version with the version installed on the user's computer.

Bow Hub should use **releases rather than commits**. A normal code push should not cause users to receive an update notification.

The `assetMatch` setting tells Bow Hub which release asset should be treated as the installer. The desktop application can later support more advanced matching rules when a release contains multiple installers.

## Display modes

Bow Hub supports three planned project-page modes.

### Generated

```json
"display": {
  "type": "generated"
}
```

Bow Hub creates the project page from catalog metadata.

### Website

```json
"display": {
  "type": "website",
  "url": "https://example.com"
}
```

Bow Hub displays or opens the project's normal website.

### Custom HTML

```json
"display": {
  "type": "custom-html",
  "html": "pages/example-app.html"
}
```

Bow Hub loads an HTML file from this repository. This allows a project to have a completely custom page without requiring a Bow Hub application update.

Custom HTML content should always be treated as untrusted web content by the desktop client. It should run in a sandbox with Node.js integration disabled and should not receive unrestricted filesystem, shell, Electron, or Windows access.

## Concept projects

Projects do not need an installer. A concept can be included like this:

```json
{
  "id": "future-project",
  "name": "Future Project",
  "shortDescription": "A project currently being explored.",
  "category": "privacy",
  "status": "concept",
  "installable": false,
  "display": {
    "type": "custom-html",
    "html": "pages/future-project.html"
  }
}
```

Bow Hub can show **View Concept** or **Learn More** instead of an Install button.

## Adding a new project

1. Add the project to `apps.json`.
2. Add its icon to `icons/` if needed.
3. Add optional screenshots or banners under `assets/`.
4. Add a custom HTML page under `pages/` if the project uses `custom-html` display mode.
5. Commit and push the changes.
6. Bow Hub will receive the new catalog entry during its next catalog refresh.

## Updating an existing program

If the app uses GitHub Releases, **do not change the catalog just because the application version changed**.

Publish the new version as a GitHub Release in that application's repository. Bow Hub should discover it automatically.

Edit the catalog only when the app's catalog metadata needs to change.

## Goals

The catalog is designed around a few simple goals:

- Add new Bow projects without rebuilding Bow Hub.
- Detect program updates automatically from GitHub Releases.
- Support Concept, Prototype, Alpha, Beta, Stable, Deprecated, and Archived projects.
- Allow filtering by project category and development status.
- Support installable programs, browser extensions, websites, and concepts.
- Allow optional custom HTML project pages.
- Keep system-level installation logic inside Bow Hub rather than inside remote HTML.

## License

A license can be added when the Bow Hub project licensing decision is finalized.
