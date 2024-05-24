# semantic-chunking-yt
A python notebook, which if added URL of a youtube video will return the transcript into semantically rich chunks time aligned with the video.


# Screenshots and Steps followed

1. Downloading the video from url using the `yt-dlp` library.
2. Extracting audio from the video using `Moviepy` library and writing the audio.wav file to the disk.
3. Downloading and initializing the OpenAI's Whisper model using `SpeechRecognition` library.
4. Listening to audio and producing a transcription.
5. Chunk text into semantically rich chunks of 15 words or so (assuming one speaks one word in a second) using `semchunk` and `tiktoken`.
6. Pass the semantically chunked `transcript`, `transcript_audio`, `syncmap_path` to `Aeneas` library's `Task`. This outputs chunks which have been forced align with the video.
7. Now rewrite the `syncmap` to match the format required and save it to the disk.

Final format of syncmap looks like this:
```python
sample_output_list = [
    {
        "chunk_id": 1,
        "chunk_length": 14.5,
        "text": "Here is an example of a semantic chunk from the video.",
        "start_time": 0.0,
        "end_time": 14.5,
    },
    # Additional chunks follow...
]

```
![2024-05-20_14-18](https://github.com/Lauel09/semantic-chunking-yt/assets/19989996/7b8e1bae-93d8-4e35-bfe4-d952762c604b)

![image](https://github.com/Lauel09/semantic-chunking-yt/assets/19989996/73b74688-df20-44e7-b728-33f368ae3b5e)

