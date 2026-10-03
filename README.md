# ASCII T-Rex 🦖
**Live demo:** https://ascii.zelva.live/

![demo](/public/medias/demo.gif)


## How it works

1. A rigged, animated `.glb` model is loaded with `GLTFLoader`.
2. An `AnimationMixer` plays the model's built-in animation clip every frame.
3. Instead of drawing to the canvas normally, the scene is passed through `AsciiEffect`, which converts pixel brightness into characters (` *3&(8&)`).
4. `OrbitControls` lets you move the camera around the scene.

## Setup

Download [Node.js](https://nodejs.org/en/download/), then run:

```bash
# Install dependencies (only the first time)
npm install

# Run the local server at localhost:8080
npm run dev

# Build for production in the dist/ directory
npm run build
```

Put the model at `/models/animated_t-rex_dinosaur_biting_attack_loop.glb` (inside the static/public folder of your project).

## Things I learned (the hard way)

- **If your model doesn't show up, check its scale.** My imported model was tiny compared to the scene, and it cost me an hour of debugging. The fix was one line: `gltf.scene.scale.set(300, 300, 300)`.
- The animation won't play unless you create an `AnimationMixer` and call `mixer.update(clock.getDelta())` inside the render loop.
- Characters in `AsciiEffect` are ordered dark to light, so try `{ invert: true }` if your picture looks inverted.

## Tweak it

- **Characters:** change the string in `new AsciiEffect(renderer, ' *3&(8&)', ...)`.
- **Color:** `effect.domElement.style.color = 'red'`.
- **Model position/size:** `gltf.scene.scale` and `gltf.scene.position`.

## Credit

[Model](https://skfb.ly/o9oHC) by LasquetiSpice is licensed under Creative Commons Attribution ([CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)).
