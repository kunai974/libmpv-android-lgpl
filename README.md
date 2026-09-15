# libmpv for Android — LGPL build

Based on [mpv-android](https://github.com/mpv-android/mpv-android), forked from
[jarnedemeulemeester/libmpv-android](https://github.com/jarnedemeulemeester/libmpv-android).

## Differences with upstream

This fork builds libmpv **without GPL components** so it can be used, as a separately
replaceable shared library, by applications that are not GPL:

- FFmpeg is configured with `--enable-version3` only (no `--enable-gpl`) → **LGPL v3 or later**
  (`version3` is required by mbedtls, Apache-2.0).
- mpv is configured with `-Dgpl=false` → **LGPL v2.1 or later**.
- Lua scripting is disabled (`-Dlua=disabled`): the embedding app drives mpv through the client API only.

Everything else (dependency versions, patches, build steps) is unchanged. The AAR produced by the
"Build libmpv-android" GitHub Actions workflow of this repository is the exact binary shipped.

Source code of the bundled libraries: see the versions in
[`buildscripts/include/depinfo.sh`](buildscripts/include/depinfo.sh) and the download URLs in
[`buildscripts/include/download-deps.sh`](buildscripts/include/download-deps.sh).

## Building from source

Take a look at [README.md](buildscripts/README.md) inside the `buildscripts` directory.
