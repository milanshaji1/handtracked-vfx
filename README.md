# Hand Filter

A hand-tracked visual effect in TouchDesigner, inspired by the "manual tracking" trend seen on Instagram/TikTok. A quad is corner-pinned between three finger-pairs on each hand (thumb–index, index–middle, middle–pinky), masking a filtered copy of the webcam feed with a white outline on top.

## How it works

- **MediaPipe-TouchDesigner** plugin provides real-time hand landmark tracking (21 points per hand, both hands).
- Fingertip positions (`thumb_tip`, `index_finger_tip`, `middle_finger_tip`, `pinky_tip`) drive three Corner Pin TOPs, each spanning one finger-pair across both hands.
- Each quad masks a differently-filtered copy of the video:
  - **Band 1** (thumb–index): RGB Contrast
  - **Band 2** (index–middle): Pixel Relocator → recolour
  - **Band 3** (middle–pinky): Solarize → recolour
- An Edge TOP outlines each quad; all layers composite over the live camera feed.

## Requirements

- [TouchDesigner](https://derivative.ca/) (2025.x)
- [MediaPipe for TouchDesigner](https://github.com/torinmb/mediapipe-touchdesigner) plugin, active and configured for hand + gesture detection
- A webcam

## Running it

Open `Hand Filter.toe`, confirm the webcam feed is live in the `video_in` node, and hold both hands up in frame with fingers spread. The Perform window (`out1`) shows the composited output.
