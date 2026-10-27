# UE Mod Manager metadata

`manifest.json` is read by UE Mod Manager at every start, from
`https://raw.githubusercontent.com/KintaroModding/metadata/main/uemodmanager/manifest.json`.

## `ue4ss`

The UE4SS release each game should use, keyed by the game profile id
(`phantom-blade-zero`, `mortal-shell-2`, ...):

| Field | Meaning |
| --- | --- |
| `version` | Release version, such as `v3.0.1-1181-g83330635`. Users whose installed UE4SS has another version are offered an update. |
| `url` | Direct `https://` download link of the release zip (`dwmapi.dll` + `ue4ss/` at the top). |
| `sha256` | SHA-256 of that zip, as in the release's `SHA256SUMS.txt`. A download that differs is refused. |

To ship a new UE4SS build: publish the release, then update `version`, `url`
and `sha256` of the game and commit. Users get it at their next start (GitHub
may serve the old file for up to about 5 minutes).

A game without an entry, or a manifest that cannot be reached, simply offers no
update; installing UE4SS from a downloaded file always works.
