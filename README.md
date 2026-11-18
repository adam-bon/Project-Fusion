# Project Fusion

A personal Unity VR project that shows a different image to each eye in a headset.

## Why I built it

I have stereo blindness, meaning my brain doesn't combine the images from my two eyes into one 3D view. I wanted to see whether VR, which gives each eye its own separate picture, could be used to practise stereo vision. This project was my first step toward that.

## How it works

- **A camera for each eye.** The XR rig has two cameras, `LeftCamera` and `RightCamera`. Each one has its Target Eye set to render only to that eye.
- **Layer culling.** Two layers, `LeftCamera` and `RightCamera`, hold each eye's content. Each camera's culling mask hides the other eye's layer. A sprite on the `LeftCamera` layer (`LeftImage`) appears only in the left eye, and a sprite on the `RightCamera` layer (`RightImage`) appears only in the right eye.
- **Joystick movement.** `LeftJoystickMovement.cs` reads the left controller's thumbstick through `UnityEngine.XR` and moves an image horizontally and vertically, so the user can shift one eye's image relative to the other's. It's attached to `LeftImage` in the scene but is currently disabled. `Movement.cs` is an alternative version of the same idea that uses the legacy Input Manager axes; no scene uses it.

The main scene is `Assets/Scenes/SampleScene.unity`.

## Test images

`LeftImage` and `RightImage` use `eccentric circle left (first attempt).png` and `eccentric circle right (first attempt).png`. They're a stereo pair based on the eccentric circles exercise from vision therapy. Each image is a ring with an inner ring offset in opposite directions, so when the two are fused, the inner ring appears to float in depth.

Other stereo pairs can be used by swapping the sprites on `LeftImage` and `RightImage` (imported with Texture Type set to Sprite), with no code changes.

## Status

This is an early prototype. It demonstrates the per-eye rendering setup with a basic test image. It isn't a finished training tool, but using it did help improve my own stereo acuity.

## Built with

- Unity 2022.2.5f1
- XR Interaction Toolkit 2.2.0
- XR Plug-in Management with the OpenXR and Oculus loaders
