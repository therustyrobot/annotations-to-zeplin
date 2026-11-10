# Annotations to Zeplin

A plugin for Figma that copies Dev Mode annotations from the frames you select into a Zeplin project, as screen annotations.

Not affiliated with or endorsed by Figma or Zeplin.

## Requirements

- A Zeplin account, and a Zeplin project whose screens are named like your Figma frames.
- A Zeplin Personal Access Token: in Zeplin, avatar → Profile → Developer Settings → Personal Access Tokens → Create.

## Use

1. In Figma, select one or more top-level frames that contain Dev Mode annotations, then run **Plugins → Annotations to Zeplin**.
2. Paste your Zeplin token. It is stored on your computer in Figma's local plugin storage (not in the Figma file). Use the settings icon → **Forget saved token** to remove it.
3. Pick the Zeplin project the file belongs to.
4. Review the frame → screen matches, tick the frames you want, and click **Import annotations**.
5. Open the project in Zeplin and check the annotations landed on the right screens.

## How frames are matched

- A frame matches a screen with the same name (case-insensitive).
- If several screens share the name, the plugin compares size using the export scale it infers from your uniquely named frames. An exact size hit is pre-checked.
- A closest-size or aspect-ratio-only match is flagged **verify** and starts **unchecked**.
- If two or more screens are indistinguishable, the frame is listed as ambiguous and cannot be imported.
- An annotation's Figma category is mapped to the Zeplin annotation type with the same name. Categories with no match are imported untyped and listed in the final report.

## Limitations

- Import writes to Zeplin immediately and the plugin cannot undo it. Delete unwanted annotations in Zeplin.
- Running the plugin again on the same frames creates duplicate annotations.
- Only selected `FRAME` nodes are scanned (annotations on any layer inside them are included); selected sections, components or groups are ignored.
- If Zeplin rate-limits requests, the plugin waits for the delay Zeplin asks for and retries a few times before counting the annotation as failed.

## Privacy

See [PRIVACY.md](PRIVACY.md).

## Support

Open an issue at <https://github.com/therustyrobot/annotations-to-zeplin/issues>.
