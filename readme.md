# ask-me-parenting-line-bot


1. get video entites
by using selenium, please refence this to login youtube 
https://www.youtube.com/watch?v=FVumnHy5Tzo

chrome drive 
https://googlechromelabs.github.io/chrome-for-testing/#stable

```
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --remote-debugging-port=9222 --user-data-dir="your dir"
```

```
python3 video_crawler.py --channel-name=$channe_name
```

2. extract transcript and process, then save to text
```
python3 transcript_to_text.py
```

3. video to audio if no transcript
```
python3 video_to_audio.py --channel-name=$channe_name
```

4. use api to get transcript for videos without transcript
```
python3 audio_to_text.py --channel-name=$channe_name --limit=10
```
