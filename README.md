# Bow Hub Catalog

Official catalog used by Bow Hub to discover and organize Bow projects.

Bow Hub reads `catalog.json` remotely. The catalog only stores basic project information such as the project name, description, category, development status, website, and optional icon.

The project's own website is displayed inside Bow Hub and remains responsible for detailed project information, screenshots, release notes, and download links.

## Adding a new project

Add another object to the `apps` array in `catalog.json`.

Example:

```json
{
  "id": "example-app",
  "name": "Example App",
  "description": "Short description of the project.",
  "category": "Utilities",
  "status": "Beta",
  "website": "https://example.potterservice.com",
  "featured": false,
  "icon": ""
}
```

## Fields

- `id` — unique lowercase project identifier.
- `name` — project name shown in Bow Hub.
- `description` — short description shown on project cards.
- `category` — one of the categories listed in `categories`.
- `status` — Concept, Prototype, Alpha, Beta, Stable, or Archived.
- `website` — website Bow Hub should display for the project.
- `featured` — whether the project should appear in featured areas.
- `icon` — optional direct image URL. Leave blank to let Bow Hub use a fallback icon.

## Updating a project

For normal project updates, you do not need to edit the catalog.

Update the project's website and download links normally. Bow Hub will continue loading that website from the same catalog entry.

Only edit `catalog.json` when you want to:

- Add or remove a project
- Change its category
- Change its status
- Change its description
- Change its website
- Feature or unfeature it
- Change its icon

## Suggested repository name

`Bow-Hub-Catalog`
