# Privacy Policy — Annotations to Zeplin

_Last updated: 2026-11-10_

"Annotations to Zeplin" is a plugin for Figma that copies Dev Mode annotations
from selected Figma frames into a Zeplin project as screen annotations. It runs
entirely inside Figma's plugin sandbox and talks directly to Zeplin's own API —
there is no backend server operated by the plugin author, and the author does
not receive, log, or store any data the plugin processes.

## What the plugin reads from Figma

When you run the plugin against your current selection, it reads only:

- The name, width, and height of each selected frame.
- The name and ID of any node inside those frames that has a Dev Mode
  annotation attached.
- Each annotation's content/label, category, and a position normalized to the
  frame's bounds (0–1 on each axis).
- The names of the file's annotation categories, to translate each
  annotation's category ID into a label.

No other layers, pages, or files in the document are read. Frame and node names
are used only on your machine, to match frames to Zeplin screens; they are not
sent to Zeplin.

## What the plugin reads from Zeplin

Using the token you provide, the plugin reads your list of active Zeplin
projects, then the screen names and sizes and the annotation types of the
project you pick. This is used only to build the frame-to-screen match table.

## What the plugin sends, and to whom

- Your Zeplin Personal Access Token (PAT), which you paste in yourself, is sent
  only as an `Authorization: Bearer` header on requests to Zeplin's official
  API (`api.zeplin.dev`). The plugin's manifest restricts network access to that
  one domain — no other domain is reachable from the plugin.
- After you pick a Zeplin project and review the frame-to-screen match table,
  clicking **Import annotations** sends each selected frame's annotations —
  content, position, and category (when it resolves to one of that project's
  Zeplin annotation types) — to the Zeplin screen you confirmed, via Zeplin's
  public annotations API.
- Nothing is sent anywhere else. There is no analytics, telemetry, or
  third-party tracking of any kind in this plugin.

## Where your data is stored

- Your Zeplin PAT is saved on your computer via Figma's own `clientStorage` API,
  scoped to this plugin. It is not stored in your Figma file, and the plugin
  does not encrypt it. It never leaves your machine except as the
  Authorization header described above.
- Use **Forget saved token** in the plugin at any time to delete it
  immediately.
- The plugin keeps no other persistent state; closing it discards the current
  scan.

## Third parties

The only third party involved is Zeplin, via its documented public API, using
the credentials you provide. Annotations created in Zeplin are then held by
Zeplin; see [Zeplin's own privacy policy](https://zeplin.io/privacy) for how it
handles data once it receives it. This plugin is not affiliated with or
endorsed by Figma or Zeplin.

## Changes to this policy

If this plugin's data handling changes, this document will be updated and the
change reflected in the plugin's Community listing.

## Contact

Questions about this plugin's data handling: open an issue at <https://github.com/therustyrobot/annotations-to-zeplin/issues>.
