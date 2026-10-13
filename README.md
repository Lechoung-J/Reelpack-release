# Reelpack macOS release preparation

Source repository: [Lechoung-J/Reelpack](https://github.com/Lechoung-J/Reelpack).

Both the source repository and this distribution repository are currently **private**. Publication is on hold until the owner explicitly authorizes it. Existing Release assets are retained as a draft; no published Release is available from this repository.

## Prepared artifacts

- Apple Silicon / arm64; macOS 14 or later.
- Local ad-hoc signing; the prepared build is **not notarized**.
- The App contains Swift App/CLI, Python source and native OCR; Python environments and models are separate.
- Native Python 3.12 or an existing uv installation, plus native FFmpeg/ffprobe, are needed for installation.

## Internal installation review

Use the draft assets with repository access, or a separately verified local copy. Public GitHub/proxy/CDN commands are withheld from this README while publication is paused.

```sh
bash install.sh --archive 'Reelpack-0.1.0-arm64.zip' \
  --sha256 'Reelpack-0.1.0-arm64.zip.sha256' --no-launch
```

Default locations: `~/Applications/Reelpack.app` and `~/Library/Application Support/Reelpack/runtime/arm64`. The installer creates five isolated native environments and checks imports. It guides model setup without downloading large optional weights. Run `bash install.sh --help` for explicit replacement, verification and offline wheelhouse options.

Music physical descriptors retain their actual backend/status. Optional PANNs tags have an independent status, so absent weights do not hide completed beat/BPM analysis. OCR uses original video frames with a 1920px width cap; subtitles can still contain recognition errors.

## License

See [LICENSE](LICENSE). Dependencies, system tools and model weights keep their own licenses. Intel/x86_64 binary preparation is still pending.
