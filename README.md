## aframe-audio-visualizer-components

Audio visualizer components for [A-Frame](https://aframe.io) using
[dancer.js](https://github.com/jsantell/dancer.js/).

### Properties

#### audio-visualizer

Creates a `dancer.js` instance.

| Property | Description                                                          | Default Value |
| -------- | -----------                                                          | ------------- |
| src      | Path to audio file `url(song.mp3)` or selector to audio element.     | null          |
| unique   | Whether to share the audio instance with other visualizing entities. | false         |

Access the `dancer.js` instance to get all the audio data you need:

```
el.components['audio-visualizer'].dancer.getSpectrum();
```

#### audio-visualizer-kick

Adds kick with `audio-visualizer` component as a dependency.

Kicks are detected when the amplitude (normalized values between 0 and 1) of a
specified frequency, or the max amplitude over a range, is greater than the
minimum threshold, as well as greater than the previously registered kick's
amplitude, which is decreased by the decay rate per frame.

| Property  | Description                                                                    | Default Value |
| --------  | -----------                                                                    | ------------- |
| frequency | Range of frequencies of spectrum to check.                                     | 127, 129      |
| threshold | Threshold of amplitude to go over to fire a kick.                              | 0.00001       |
| decay     | Rate that previously registered kick's amplitude is reduced by on every frame. | 0             |

| Event Name                  | Description                                   |
| --------                    | -----------                                   |
| audio-visualizer-kick-start | Kick start. Went from not kicking to kicking. |
| audio-visualizer-kick-end   | Kick end. Went from kicking to not kicking.   |

### Usage

#### Browser Installation

Install and use by directly including the [browser files](dist):

```html
<head>
  <title>Audio Visualizer</title>
  <script src="https://aframe.io/releases/0.2.0/aframe.min.js"></script>
  <script src="https://rawgit.com/ngokevin/aframe-audio-visualizer-components/master/dist/aframe-audio-visualizer-components.min.js"></script>
</head>

<body>
  <a-scene>
    <a-entity audio-visualizer="src: url(rickroll.mp3)" audio-visualizer-kick></a-entity>
  </a-scene>
</body>
```

#### NPM Installation

Install via NPM:

```bash
npm install aframe-audio-visualizer-components
```

Then register and use.

```js
require('aframe');
require('aframe-audio-visualizer-components');
```
