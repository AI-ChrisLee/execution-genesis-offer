# Recording a call, and getting the text

The paragraphs the warm lesson (g4) and the sales lesson (g6) quote. Every transcriber here
runs on the laptop; nothing is uploaded anywhere.

## A 20-minute warm call

Zoom, free, hosted from the desktop app (a phone host records nothing). Press Record. In
person: the phone's recorder. Free Google Meet records nothing; take the call on Zoom or in
person. When the call ends, drop the file in `squad/interviews/`, named after the person
(`daniel.m4a`), and say: "/the-winning-offer I put my interview with Daniel in
squad/interviews. Build the offer from it." It transcribes on the laptop.

## How the squad transcribes (the agent runs this; the founder says yes once)

**The yes, asked only when `~/.squad/whisper` (`%USERPROFILE%\.squad\whisper` on Windows) is
not there yet, in one line:** "I install a small transcriber on this laptop
(faster-whisper, about 150MB of model weights downloaded once). Your recording never leaves
the laptop. Yes?" On the yes, run the install in its own folder, so nothing else on the
laptop changes:

```
# Mac / Linux
python3 -m venv ~/.squad/whisper
~/.squad/whisper/bin/pip install faster-whisper

# Windows (PowerShell)
py -m venv $HOME\.squad\whisper
& $HOME\.squad\whisper\Scripts\pip install faster-whisper
```

No ffmpeg install. faster-whisper decodes the recording itself through PyAV, which ships the
decoders inside the package.

**The transcription.** Pick the smallest model that runs cleanly, in this order: `base`
(every laptop; the default), `small` when the call is not in English, `tiny` when `base`
fails to load. Write one line per segment to the person's `transcript.md`:

```
from faster_whisper import WhisperModel
model = WhisperModel("base", device="cpu", compute_type="int8")
segments, info = model.transcribe("<recording path>", vad_filter=True)
with open("<folder>/transcript.md", "w") as out:
    out.write("source: <recording file name> · <date>\n\n")
    for s in segments:
        out.write(s.text.strip() + "\n")
```

That first line is written here, by the transcriber, and it is the only record the recording
was processed. Without it the same file is transcribed again on the next run.

Write those lines to a temp file at `~/.squad/whisper/transcribe.py`
(`%USERPROFILE%\.squad\whisper\transcribe.py` on Windows), never in the company folder, and
run the venv's python against it; that path works on both
(`~/.squad/whisper/bin/python ~/.squad/whisper/transcribe.py` on a Mac,
`$HOME\.squad\whisper\Scripts\python $HOME\.squad\whisper\transcribe.py` on Windows). Delete
the temp file after. A
20-minute call takes 2 to 5 minutes on a laptop CPU; say so before it starts, then wait. The
install is done once; every later recording goes straight to this step.

**An install that fails** gets one line and no second attempt: "The install did not take.
Drop the file on MacWhisper (Mac, free, macwhisper.com) or Buzz (Windows, free,
github.com/chidiwilliams/buzz; the installer is unsigned, so Windows shows More info, then
Run anyway), set the language to the call's, export `.txt`, and drop it in
squad/interviews/." Then wait for the file. Both run on the laptop too.

## A 60-minute sales call (the-close quotes this)

Record on Zoom from the desktop app and hand the file to your squad the same way; the
transcriber above takes an hour of audio in a few more minutes. Free Zoom ends every meeting at
40 minutes, one-on-one included, so a 60-minute call needs Zoom Pro, which also writes the
transcript itself as a `.vtt` once cloud recording and the audio transcript are switched on,
one time. No Zoom Pro: take the call on Cal Video or Google Meet and record it on the phone
beside you, then hand that file over like any other.

## File types

Transcripts: `.txt`, `.md`, `.srt`, `.vtt`. Recordings: `.m4a`, `.mp3`, `.wav`, `.mp4`, `.mov`.
