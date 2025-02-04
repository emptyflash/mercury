# 👩‍💻👨‍💻 Collaborative Coding

It is now possible to code together in Mercury using the amazing [**Flok**](https://flok.clic.cf/) live coding environment for the browser. 

There are 3 options for how you can use Flok with Mercury:
1. Use Flok to combine Mercury with Hydra visuals (or other languages like Tidal, Foxdot and SuperCollider) on a localhost
2. Collaborate together in the same room (only requires 1 computer to run Mercury)
3. Collaborate remotely over a network (all computers need to run Mercury)

Install NodeJS v.12 [for Mac](https://nodejs.org/dist/latest-v12.x/node-v12.20.1.pkg) or [for Windows](https://nodejs.org/dist/latest-v12.x/node-v12.20.1-x64.msi).

Install the latest version of Mercury via the [quick start quide](https://github.com/tmhglnd/mercury/blob/master/docs/quick-start.md).

Install Flok via the Terminal with `npm install -g flok-web flok-repl`

## Localhost

1. Run `flok-web` in the terminal
2. Open Google Chrome and go to `localhost:3000`
3. Setup Flok with target `mercury` (and optionally other targets like `hydra`) and click **Create session**.
4. Copy the `flok-repl -H xxx -s xxx -t mercury` command and run in the terminal.
5. **Join** the Flok with your nickname.

## Collaborate

Now follow these steps for a succesful setup.
1. Open Google Chrome and go to [https://flok.clic.cf/](https://flok.clic.cf/)
1. Setup Flok with target `mercury` and click **Create session**.
2. Copy the `flok-repl -H xxx -s xxx -t mercury` command and run in the terminal.
4. **Join** the Flok with your nickname.

Now start typing some code! 🎵

- `Ctrl/Alt + Return` to evaluate
- `Ctrl/Alt + .` to silence

Flok will send the entire code via OSC messaging to port 4880. Mercury should be listening to this port automatically. Bug reports are very much welcome in the issues!

## Combine Mercury with Hydra (Audioreactive Visuals)

Follow this guide if you like to let Hydra react to the sounds that you code with Mercury when using Flok. 

**for Mac**

1. Install [blackhole](https://existential.audio/blackhole/) for virtual audio routing
2. Open `Audio MIDI Setup` in your Applications
3. Click `+` in left-bottom corner and then `Create Multi-Output Device`
4. Select both `Built-in Output` and `Blackhole` (if blackhole is not listed restart the computer first)
5. Start Mercury and under `Settings` > `Audio Setup` change the output to the `Multi-Output Device`
6. Open Google Chrome and setup Flok as described under [Collaborate](#collaborate)
7. Click the `Microphone` icon and selecte `Manage`
8. Select `Blackhole (Virtual)` 

**for Windows**

1. Install [vbcables](https://vb-audio.com/Cable/index.htm) for virtual audio routing
2. More steps are needed but this has not been tested on Windows, please contribute to this documentation if you know the steps

**Both**

Now start coding some Mercury and Hydra code! 📟

To create audio reactive visuals with hydra use the FFT audio object accessible via the `a` object. Below is some example code for hydra that you can use.

```js
a.show() 
//=> show the FFT bins audio amplitude

a.setBins(6)
//=> set the amount of FFT bins to extract from the sound (low -> high frequencies)

osc(10, 0, () => a.fft[0]*4 ).out()
//=> choose a bin index and modulate a parameter with function return
```
