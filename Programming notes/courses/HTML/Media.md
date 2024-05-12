# Audio
- `<audio>` element is used to put audio file in a web page.
- The browser will create a audio player in place of `<audio>` tag.
- audio element has closing tag unlike image tag.
- `<audio controls src="audio.mp3"></audio>`
- The `controls` attribute is used to tell the browser to show play/pause button etc to the user.
- If we don't specify the `control`  attribute then the audio element will not be visible to browser.
- `loop` attribute will make the file loop when it gets to the end.
- `autoplay` will make the file autoplay as soon as the page loads.
##### Why do we have opening and closing tag ?
- It is because we can use  `source` element to specify more than 1 audio file.
```html
<audio controls>
<source src="audio1.ogg" type="audio/ogg">
<source src="audio2.mp3" type="audio/mpeg">
</audio>
```
- `mp3` is supported in most modern browsers today.
- The browser will use the first file in the list which it understands.
- You can also provide some alt text, if the browser is unable to understand any of the audio files.
```html
<audio controls>
<source src="audio1.ogg" type="audio/ogg">
<source src="audio2.mp3" type="audio/mpeg">
Alt text
</audio>
```

# Video
- Works just like `audio` element.
- `<video src="video.mp3" controls></video>`
- `controls` attributes tells the browser to create a video player for us.
- Like audio element we can put multiple video sources inside `video` tag. And the browser will use the first source who's format it understands.
```html
<video controls>
   <source src="video.webm" type="video/webm">
   <source src="video.mp4" type="video/mp4">
</video>
```
- In general `video` tag is not used in real life. Because using `video` tag you cant dynamically change video resolution based on network speed.
- For video streaming code snippet from backend server is used.
# Captions
- `track` element is used inside `video` element to point to a caption file.
```html
<video controls>
   <source src="video.webm" type="video/webm">
   <source src="video.mp4" type="video/mp4">
   <track src="track.vtt" kind="captions" label="english" seclang="en" default></track>
</video>
```
- `vtt` files are used to subtitles in the web.
- `label` will show up in the player as a list of options to choose subtitle.  
- `srclang` is used to specify language of the subtitle.
- `default` attribute tells the browser that this attribute you want to use by default when user turns on captions.
- `kind="Descriptions"` `=>` the `vtt` file describes the video. Useful for blind people.
- `kind=chapters` `=>` the `vtt` file lists the chapters of the video. Similar to you tube chapters.
- 