# Phonograph Plus AA (Album Artist edition)

An **unofficial** build of [Phonograph Plus](https://github.com/chr56/Phonograph_Plus) with one
extra option: the **Artists** tab can list **album artists only**.

Turn it on in the Artists tab: tap the **tune icon** (top right) → tick **Album artists only**.
With it on, the Artists tab only shows artists who are the *Album Artist* of at least one album.
Albums with no Album Artist tag fall back to the track artist. Compilations and features stop
filling the list with one-off track artists. Opening an artist still shows all of their songs.
Off by default.

Everything else is identical to upstream Phonograph Plus. The fork is based on the version
named in the release title.

## Installing next to your existing Phonograph Plus (keeps your data)

This build uses its own package name (`player.phonograph.plus.albumartist`) and its own signing
key. It **installs next to** the official app instead of replacing it, and nothing in the official
app is touched. Android only lets an app update over an existing install when the developer's
signing key matches, and only the upstream developer has that key. So an in-place "patch" over
the official app is not possible. Copy your data across with the app's built-in backup instead:

1. In your **current** Phonograph Plus: **Settings** → **⋮** menu (top right) → **Export Backup**.
   Leave every item ticked and save the `.zip` somewhere you can find it, such as Downloads.
2. Install the APK from this release. Allow "install unknown apps" for your browser or file manager
   if Android asks.
3. Open **Phonograph Plus AA**, grant the media permission, and let it scan your library.
4. In Phonograph Plus AA: **Settings** → **⋮** → **Import Backup** → choose the `.zip` from
   step 1, and import everything.

What comes across: settings, favourites, Phonograph's internal playlists, play history, play
counts, playing queues and path filters. Your songs, albums and artists are read from the music
files on the phone, so they appear on their own after the scan. Playlists stored as system/`.m3u`
playlists live outside the app and show up in both apps.

Once you're happy with the new app, you can uninstall the official one, or keep both.

## Building

```bash
./gradlew app:assembleModernAlbumartistRelease
```

Signed release APKs come from the `album-artist-release` GitHub Actions workflow when an
`aa-*` tag is pushed.
