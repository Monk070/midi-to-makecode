# MIDI to MakeCode Arcade Converter V1.2 
## Now with Lyrics Sync!

A browser-based tool that converts MIDI files to MakeCode Arcade's song hex format for use with the `music.play()` block.

🎵 **[Try it live](https://monk070.github.io/midi-to-makecode/)**

## Features

- **Drag & drop** - Simply drop a MIDI file to convert
- **No installation** - Runs entirely in your browser
- **No dependencies** - Single HTML file, works offline
- **Instant output** - Copy the generated TypeScript code directly into MakeCode
- **Adjustable settings:**
  - **Tempo Divisor** - Fit longer songs into the 255 measure limit
  - **Octave** - Auto-detect or manually select pitch range
  - **Note Range Condensing** - Squeeze wide-ranging songs into playable octaves

## How to Use

1. Open the converter in your browser
2. Drag & drop a `.mid` or `.midi` file (or click to select)
3. Adjust settings if needed
4. Click **Copy Code**
5. In MakeCode Arcade, switch to **JavaScript** view
6. Paste the code
7. Your song plays! 🎶

## Output Format

The converter generates code like:

```typescript
music.play(music.createSong(hex`00780004080201...`), music.PlaybackMode.UntilDone)
```

This uses MakeCode Arcade's native song format - no extensions required.

## Limitations

- **255 measures max** - Use the tempo divisor for longer songs
- **Monophonic playback** - Polyphonic MIDIs play all notes but may sound busy  
- **No instrument selection** - Uses MakeCode's default instrument (editable in the song editor after import)

## Technical Details

The hex string encodes:

| Section | Description |
|---------|-------------|
| Header (7 bytes) | Version, BPM, time signature, measures, track count |
| Track | ID, instrument data (28 bytes), note events |
| Note Event | Start tick, end tick, note count, MIDI notes |

Based on the format documented in [microsoft/pxt](https://github.com/microsoft/pxt/blob/master/pxtlib/music.ts).

## Tips

- **Song too long?** Increase the tempo divisor to compress timing
- **Notes sound wrong?** Try a different octave setting
- **Too much range?** Use "Condense to 4 octaves" to shift extreme notes

## Credits

- Format reverse-engineered from [MakeCode Arcade](https://arcade.makecode.com/)
- Inspired by [UnsignedArduino's MIDI-to-MakeCode-Arcade](https://github.com/UnsignedArduino/MIDI-to-MakeCode-Arcade)
- Forum discussion: [New Song Format](https://forum.makecode.com/t/new-song-format/17763)

## License

MIT License - Free to use, modify, and distribute.

---

Made with ❤️ for the MakeCode Arcade community
