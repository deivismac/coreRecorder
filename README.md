# Core Cinematics Recorder

Standalone Windows companion app for the **Core Cinematics** FiveM resource.

Captures the GTA window and produces an `.mp4` (with synthetic motion blur) or a raw `.mkv`. Runs in the background; the in-game editor talks to it on `http://127.0.0.1:7861`.

## Download

Grab the latest `coreRecorder-vX.Y.Z.zip` from this repo (or the [Releases](../../releases) page). Unzip anywhere, run the exe once, then launch GTA.

**Latest: v0.2.0** — new GPU window-capture backend (Windows.Graphics.Capture, the same one OBS uses). ~5% CPU vs the old gdigrab path's ~50%, captures only the FiveM window instead of your whole desktop, and output speed matches reality even on machines that run the game above the recorder's target framerate. See `README.txt` inside the zip for the full changelog.

## First-time setup

1. Run `core-cinematics-recorder.exe` once. On first boot it:
   - Writes a default `config.json` next to the exe.
   - Auto-downloads `ffmpeg.exe` (BtbN's static Windows build) next to itself if it can't already find one.
   - Starts listening on `127.0.0.1:7861`.
2. Edit `config.json` if you want a different output folder, port, or capture window title.
3. Launch GTA. When the in-game **Export** button hits the recorder, you get a `.mp4` (or `.mkv`) in `<output_dir>`.

If the auto-download fails (firewall, offline, etc.) you can drop your own `ffmpeg.exe` next to the recorder and the next boot will use it.

## Logs

Daily-rotated under `logs/recorder.log.YYYY-MM-DD` next to the exe. Set `RUST_LOG=debug` for verbose output.
