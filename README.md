# Reelpack macOS preview

Public distribution files only. The development repository remains private.

- Apple Silicon / arm64; macOS 14 or later.
- Local ad-hoc signing; this preview is **not notarized**.
- The App contains Swift App/CLI, Python source and native OCR; Python environments and models are separate.
- Native Python 3.12 or an existing uv installation, plus native FFmpeg/ffprobe, are needed for installation.

## Install

Save the installer, verify its hash, then run it. Do not pipe a remote script into a shell.

```sh
curl --fail --location --proto '=https' \
  'https://cdn.jsdelivr.net/gh/Lechoung-J/Reelpack-release@v0.1.0/install.sh' -o install.sh
printf '%s  install.sh\n' '44afef728aeb8df5a0801834dc187ac9a1c705a7ecb74873135186e9f7fc8375' | shasum -a 256 -c -
bash install.sh --public-release \
  --manifest-url 'https://raw.githubusercontent.com/Lechoung-J/Reelpack-release/v0.1.0/release-manifest.json' \
  --gh-proxy-base 'https://gh-proxy.com' \
  --jsdelivr-manifest-url 'https://cdn.jsdelivr.net/gh/Lechoung-J/Reelpack-release@v0.1.0/release-manifest.json'
```

The public download order is GitHub, a configured public proxy, the explicit repository-file CDN URL in the manifest, then a configured Gitee mirror. Each App archive is SHA-256 checked before extraction. This repository does not have a Gitee mirror yet; an unset source is skipped. A third-party proxy never receives GitHub credentials.

Offline installation with a separately verified download:

```sh
bash install.sh --archive 'Reelpack-0.1.0-arm64.zip' --sha256 'Reelpack-0.1.0-arm64.zip.sha256' --no-launch
```

Default locations: `~/Applications/Reelpack.app` and `~/Library/Application Support/Reelpack/runtime/arm64`. The installer creates five isolated native environments and checks imports. It guides model setup without downloading large optional weights. Run `bash install.sh --help` for explicit replacement, verification and offline wheelhouse options.

Music physical descriptors retain their actual backend/status. Optional PANNs tags have an independent status, so absent weights do not hide completed beat/BPM analysis. OCR uses original video frames with a 1920px width cap; subtitles can still contain recognition errors.

## License

See [LICENSE](LICENSE). Dependencies, system tools and model weights keep their own licenses. Intel/x86_64 binary release is not included in this preview.
