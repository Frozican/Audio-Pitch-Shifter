# Audio Speed/Pitch Shifter

A browser-based audio speed shifter that changes the playback speed of audio while keeping the original pitch unchanged.

The entire application runs directly in the browser and is contained in a single HTML file. No server, installation, or external dependencies are required.

## Features

- Change audio speed from **50% to 200%**
- Preserve the original pitch while changing speed
- Preview processed audio directly in the browser
- Export processed audio as a **WAV file**
- Real-time speed and pitch information
- Built-in pitch visualization
- Supports common browser-compatible audio formats
- Runs completely client-side
- No audio files are uploaded to a server

## How It Works

Normally, changing the playback speed of an audio file also changes its pitch.

For example:

- 50% speed → pitch becomes one octave lower
- 100% speed → pitch remains unchanged
- 200% speed → pitch becomes one octave higher

Audio Speed Shifter separates these two properties by using a time-stretching algorithm.

The audio is processed so that its duration changes while the original pitch is preserved.

The pitch indicator still shows the **natural pitch change that would occur without pitch correction**. This makes it possible to see how much the speed change would normally affect the pitch.

## Usage

1. Open the application in a modern web browser.
2. Select an audio file.
3. Move the speed slider to the desired value.
4. Press **Play** to preview the result.
5. Press **Export as WAV** to save the processed audio.

### Speed Range

| Speed | Natural Pitch Change |
|------:|---------------------:|
| 50% | -12 semitones |
| 75% | -4.98 semitones |
| 100% | 0 semitones |
| 125% | +3.86 semitones |
| 150% | +7.02 semitones |
| 175% | +9.68 semitones |
| 200% | +12 semitones |

The natural pitch change is calculated using:

```text
pitchShift = 12 × log2(speed)
```

The actual processed audio does **not** apply this pitch shift.

## Privacy

All audio processing happens locally in your browser.

Your audio files are not uploaded to a server by the application.

## Technology

The application is built using standard browser technologies:

- HTML
- CSS
- JavaScript
- Web Audio API

No backend is required.

The project is intentionally designed as a single HTML file, making it easy to host using services such as GitHub Pages.

## Browser Support

The tool requires a modern browser with support for the **Web Audio API**.

Recommended browsers include:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

Performance can vary depending on the length and complexity of the audio file.

## Project Structure

```text
Audio-Pitch-Shifter/
└── index.html
└── README.md
└── LICENSE
```

The application logic, user interface, audio processing, and WAV export are contained in `index.html`.

## Running Locally

Because the application is client-side, it can be opened directly in a browser.

Alternatively, it can be served using any simple static web server.

For example:

```bash
python -m http.server
```

Then open:

```text
http://localhost:8000
```

## GitHub Pages

The live version is available at:

https://frozican.github.io/Audio-Pitch-Shifter/

## Limitations

Time-stretching audio directly in JavaScript has some limitations.

Very large audio files can require significant amounts of memory and CPU time, and certain types of audio may produce processing artifacts at extreme speed settings.

The quality can also depend on the source material. Music with strong transients, drums, or complex stereo content is generally more difficult to time-stretch cleanly than simpler audio.

## License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

See [`LICENSE`](LICENSE) for the full license text.

## Author

Created by **Frozican**.

---

If you find a bug or have an idea for improving the audio processing, feel free to open an issue or contribute to the project.
