Ref: https://github.com/kstseng/ask-me-parenting-app (Most change on step 1, 2 and  4.)


1. get video entites
    by using selenium, please refence this to login youtube 
    https://www.youtube.com/watch?v=FVumnHy5Tzo

    chrome driver 
    https://googlechromelabs.github.io/chrome-for-testing/#stable

```
#for MAC
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
    Using faster-whisper to transcript audios
    suggest by using cuda, the audio to text will faster
    change the code in audio_to_text.py 
    ```
    model = WhisperModel(model_size, device="cuda", compute_type="float16")
    ```
    ```
    model = WhisperModel(model_size, device="cpu", compute_type="int8")
    ```

```
OMP_NUM_THREADS=14 python3 audio_to_text.py --channel-name=$channe_name --limit=10
```
```
python3 audio_to_text.py --channel-name=$channe_name --limit=10
```
5. install Anything LLM  
suggest by using Docker
https://github.com/Mintplex-Labs/anything-llm/blob/master/docker/HOW_TO_USE_DOCKER.md

MAC 
```
export STORAGE_LOCATION=$HOME/anythingllm && \
mkdir -p $STORAGE_LOCATION && \
touch "$STORAGE_LOCATION/.env" && \
docker run -d -p 3001:3001 \
--cap-add SYS_ADMIN \
-v ${STORAGE_LOCATION}:/app/server/storage \
-v ${STORAGE_LOCATION}/.env:/app/server/.env \
-e STORAGE_DIR="/app/server/storage" \
mintplexlabs/anythingllm
```

6. Chosse your llm and ref data as Rag
7. Some exapmle 

The question is I'm a data scientist and I have questions about my career

Result in following screenshot and here is the youtube video which the bot reference. 

https://www.youtube.com/watch?v=11B89hfa-xY

![image](https://github.com/user-attachments/assets/b9020e25-648f-4dbb-8ed8-0cd25bcbc1c1)


