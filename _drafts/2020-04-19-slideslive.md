---
layout: single
title:  "How to Record a Slideslive Talk Without Slideslive"
date:   2020-08-26 01:00:47 -0400
categories: howto
tags: academia, productivity  
mathjax: false
toc: true
excerpt: "Yes, it is possible to record and edit a slideslive talk with open-source tools in reasonable time."
twitter_thread: 
header:
    og_image: /assets/images/toolbox.png
---

[Slideslive](https://slideslive.com) is a presentation service that many conferences started using since they had to go online. The cool feature of it is that it actually shows two video streams: the speaker view and the slidesview. And it is possible to use those slides for navigation, finding the slide you need and then playing the talk back to that slide.

The disadvantage is that, obviously, you have to record *two* videos instead of one, and keep them in sync. Most recorders can't do that. There must be some professional software that movie directors use to manage multiple cameras, but most of us have not majored in filmmaking. 

At the moment, Slideslive provides two options:

- record it in the browser (which probably won't make the best use of your camera and microphone)
- use their "slideslive editor" software which is essentially a standard single-view screen recorder that will capture the slides, AND simultaneously record yourself talking with your phone or something else (presumably using a tripod positioned behind the laptop screen). And then pray that (a) this looks decent, (b) they can sync it up.

The chief problem with either of those solutions is that you have to record the whole talk in one go. With the web solution, you can pause and resume recording, but that's it. The reality is that when things are pre-recorded, and likely to be viewed many more times than a offline conference talk, we'd rather have them a bit more polished. That is achieved either through spending a week to learn the talk by heart until it sounds like a TED talk, or through some simple video editing: just to be able to cut out the "uhs" and any mistakes, maybe be able to reorder video segments. Without that, even a regular short talk could take forever to record.

According to Slideslive representatives, they are developing a new version of their web editor that will be made public in a couple of weeks. They even kindly let me play with a pre-release version, and it is definitely a huge improvement over the current solution: it is possible to split videos in segments, remove and reorder them. The con is that it is still browser-based and won't give you much control over your mike and camera. At the moment the editor is also less keyboard-friendly than I like.  

At any rate, here's my DYI setup, which works for now and will also work in the future if you like to have more control over your recording. It *is* possible to maintain sanity and record a talk that slideslive would accept, using open-source software and in reasonable time. 

## Step 0: equipment

**Minimal setup:** you need a camera and a microphone, and obviously a computer where the presentation will run. The built-in webcam and microphone *might* do, depending on what they are and how picky you are. Your headphones might also have a built-in mike (although I was severely disappointed with my Sony WH-1000XM3).

**My fancy setup:** I used to be a musician in my previous life, so I'm quite picky about sound. The bottom line with mikes is that you want them to be reasonable quality, in a quiet environment, close to the source of sound (your mouth) and not moving around (as that will create different volume levels). The latter can be achieved either by fixing the mike on yourself (lavalier mikes, headset mikes), or fixing both the mike and yourself (having the mike on the desk or a stand, and not moving).

Caveat: most laptops do *not* even have a dedicated mike input, even if you have a good mike. So you probably need a USB mike, which essentially works as an external sound card.

In my case, luckily, I already was in possession of [Zoom H1](https://www.zoom.co.jp/products/handy-recorder/h1-handy-recorder) recorder which does also work as an external sound card. I could use just the mikes on that recorder, but it also has a separate mike input, which I used for my [Røde lavalier Go](https://www.rode.com/microphones/lavaliergo) (which I love dearly).

<figure>
	<img src="/assets/images/recording_equipment.jpg">
</figure>

As for the video equipment, I'm really not an expert, but it seems that what matters even more than the camera is the lighting: you need the light on your face to be bright enough and uniform enough, or you'll get a video that is dark and with unflattering shadows. Depending on your environment, you might be able to just use daylight. The professional setups seem to involve at least two directed lights shining on the face from both sides, which seems hard on the eyes.

I have a high-res webcam with autofocus (Logitech HD 1080p), and I thought I could trust it to stay on my face. I put the laptop directly on the window sill (with two more windows on either side providing side lighting). I was wrong: the daylight afforded by a cloudy day in Copenhagen does not suffice, so my video ended up looking blurry. 

## Step 1: Creating a two-screen recording

**Software you'll need:** [OBS Studio](https://obsproject.com/) (Windows, Linux, Mac)

This is a free, open source, and extremely feature-rich recorder which can do a lot more than we need. I feel quite intimidated by all the settings it has, but luckily we don't need all of them.

Our main problem is that for slideslive we need TWO synced-up videos (each of them 1920x1080 in size): the speaker and the slides recording. Recording them individually would take forever and be a pain to sync. So, we need to record them simultaneously, but OBS Studio, like any other recorder I tried, cannot record two things at a time.

Solution: we create an extra-wide video that contains both sources: the speaker view and the slides. We'll then edit this single video, which will enable us to not worry about syncing problems. And then we'll just split it in two for slideslive.

Here's how to achieve that.

If you run OBS Studio for the first time, it may ask you whether you want to optimize for streaming or recording (choose recording), and for the video settings. Choose 30 FPS and 1920x1080 resolution, if available.

1. Go to Settings > Video and set the base canvas resolution to 3840 x 1080. That will give us room for two 1920x1080 views side-by-side.
2. In the main window, click on "+" button under "Sources". You will need 3 sources: Audio Input Capture (mike), Video Input Capture (webcam), and Window Capture (slides). Set your input devices and slides window in the properties for these inputs.
3. Move and resize the webcam view and slides view on the canvas until they are perfectly side-by-side. 
4. Optional: add any filters on your sources that you like and know how to use (context menu on an input > Filters > "+" button in the bottom left corner). I used two:
	- Noise suppression filter on the Audio Input (with RNNoise setting): decreases the background noise caught by the mike
	- Chroma key filter on the Video Input: if you have a solid color backdrop screen, you can use this to place yourself in some virtual environment. Place the backdrop behind you, select the key color type and play with the "similarity" slider until it removes the background and nothing else. If you do this, you need to also add one more source of the "Image" type, which will serve as your virtual background.
5. Check the Settings > Hotkeys for the actions of "recording" and "stop recording". I have them both at Ctrl+R. 
6. Test the whole workflow: start the recording, switch to your slides, do a test slide, stop the recording. OBS Studio simply saves the video file to the location specified in Settings > Output. I save in mp4 format, at "high quality, medium file size" setting. You should get a single extra-wide video with slides and speaker view side-by-side.
7. Record the talk.

## Step 2: Editing the recording

*Minimalist setup*: All we need is a video editor with three barebone functions: cut, paste, and crop. I used Adobe Premiere, but [Shotcut](https://shotcut.org/download/) is open-source and cross-platform (Windows, Linux, Mac). 

If you use Shortcut:

1. Import your video file (with `Open File` in the panel) and add it to the timeline using the `+` button. 
2. Do any editing you need. `Space` will play the video, `S` or the `][` button will create a split point. If there's a part of video you'd like to remove, create split points in its beginning and its end and remove it from the context menu on the undesirable part of the video (or use  the `X` shortcut). You can also cut a part of the video this way and paste it to some other split point.

*Delux setup*. I am absolutely in love with [Descript](https://descript.com). It is also a video/audio editor, but it is aimed at people producing podcasts and vlogs, i.e. the use case where the primary concern is not just the visuals, but what is being said.

What Descript does is magic. It makes a transcription of the talk, and then lets you edit the video based on that transcript. Which means - no more rewinding several times to try to find the exact moment of the split. This is lightning fast. You read the transcript, you see the part you don't like, you select the text corresponding to that part and you delete it, just like in a text processor. And the video is adjusted and re-synced automatically. It even has the handy feature of automatically detecting and removing all the "uhs"! And it can normalize the volume of the audio, in case it turned out to be uneven.

The con is that it is not free, but (at least in my case) it definitely saves more time then it costs. The mid-tier version costs $12 a month and lets you transcribe 10 hours of video. The $24 top-tier version gives you 30 hours. There is a free tier with 3 hours of transcription, but it caps the resolution at 720p and adds a watermark.

If you use Descript:

1. Create a project
2. Add your ultra-wide video file
3. Auto-transcribe it (will take a couple of minutes)
4. Edit the text as desired. The deleted parts of video will be auto-removed accordingly.
5. Export the video.

Side note: Descript has an interesting security solution. The pro version has the uncanny ability to train a model of your voice, and overdub the parts you wish you said differently (audio only at this point). Which is great for the presenters, but obviously is a security risk, because with enough recordings people could deepfake somebody else's voice. Well, in Descript they can't do that: to train the model, you have to record a fairly long specific text, so the victim would have to be tricked into reading it aloud. 

## Step 3: Splitting the recording

However you did the editing, the result is a cleaned-up version of the original video file. Now we need to make *two* files that slideslive can import.

Using Shotcut, add a crop filter: 

1. click on `Filters` in the top panel
2. Filter panel will appear on the left. Click `+`, open the `Video` tab, and select `Crop rectangle`.
3. Set the crop filter so as to remove the right part of your video. At this point we have a 3840 x 1080 video, and we need two 1920 x 1080 videos. Set the dimensions of crop for 1920x1080, and the position to 0,0. This will remove the right-hand side of the video.
4. Export the edited video (`File > Export Video`). 
5. Repeat steps 3 and 4 to export the right-hand side of the video (with the same crop dimensions, but position 1920,0).

## Step 4: Subtitles & uploading to slideslive

Slideslive subtitles editor has been cursed a lot, but there are other options. Their editor can import subtitles in `.vtt` format: there is no upload link immediately when you upload the videos, but once they generate their own version of the subtitles, they will send you a link to the subtitle editor. There will be an "import" button. 

If you don't like the editor that slideslive provides, you're in luck: you have the source video saved, and you can download their .vtt subtitles from their editor, and use some other subtitles editor that can work with this format. A quick search for open-source tools, locates [Subtitle Edit](https://nikse.dk/SubtitleEdit/) (Windows, Linux) and [its online version that works with local video files](https://nikse.dk/SubtitleEdit/Online).

In my case, since I used Descript for editing my video, I already subtitles ready to be exported to .vtt. Since in Descript the whole editing process is based on text, you can not only remove any bits you don't like, but also fix any auto-transcription errors as you go. And then *you get both the video and the subtitles at the same time*! So - full accessibility with as little work as I can imagine. One caveat is that the file exported by Descript has extra metadata not conforming to the vtt format (lines 3-5). Once those lines are removed, the subtitles can be imported to slideslive. I was told that the editor will be improved to handle this automatically.

## Step 5: That's it!

Hopefully all this worked, and you have a reasonably nice talk recorded in reasonable time. If you've got any suggestions for alternatives for the software I used, please share in the comments.