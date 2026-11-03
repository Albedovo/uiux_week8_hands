# Hand Lens

UI/UX Week 8: a web experience that changes based on what the camera sees.

Your hands become three different lenses for exploring a valley at dusk. Twelve secrets are hidden in the scene, and each one can only be found with the right lens. Hold your gaze on something for 2 seconds and it gets photographed and ticked off in your field journal.

| Gesture | Lens | What it reveals |
| --- | --- | --- |
| Both hands in front of your eyes | 🔭 Telescope (×6) | Far-away things: a goat on the peak, a balloon, a ship, the lighthouse keeper |
| Right hand in front of your eye | 🔍 Magnifier (×4.8) | Tiny things: a carving, a snail, a ladybug, a four-leaf clover |
| Left hand in front of your eye | 🌡️ Thermal | Hidden warm things: someone in the cabin, an owl, a fox, live embers |
| Hands down | Standby | The whole scene |

Move your head to aim the lens.

## How it works

- **Gesture recognition** combines two signals:
  - A [Teachable Machine](https://teachablemachine.withgoogle.com/models/vhw_JttfT/) image model trained on the four gestures.
  - MediaPipe Pose, which checks whether each hand is in front of the eyes. It is more reliable at telling the left hand from the right.
- **Head tracking** uses the same pose model. Head position is smoothed with a One Euro filter, so the lens is steady when you hold still and quick when you move.
- **Scene** is drawn live on a canvas: layered mountains with mist, sea glints, a lighthouse beam, fireflies, and a separate thermal palette for the infrared view.

## Run it

Open `index.html` in Chrome or Edge, click **Turn on camera**, and allow camera access. An internet connection is needed, because the models and libraries load from the web.

No camera? Click **Try with keyboard** and use the keys below.

| Key | Action |
| --- | --- |
| 1 / 2 / 3 / 4 | Standby / Telescope / Magnifier / Thermal |
| C | Set your current head position as center |
| J | Show or hide the field journal |
| D | Show or hide the recognition panel |

The recognition panel shows live confidence for each class, hand-position scores, frame rate, and controls for the threshold, sensitivity, and gesture source.
