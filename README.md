# Simple Temporal Anti-Aliasing
*STAA* is an image effect for Unity engine. It is an atempt to implement a temporal AA based just on a color data without trying to use any motion reprojection. It jitters the camera projection matrix and combines the rendered frame with a history frames.

![STAA and FXAA](https://raw.githubusercontent.com/AndrewSaraev/STAA/master/Images/STAA%20and%20FXAA.png)

### Setup
- Add the *STAA.cs* to a camera game object
- Assign the *STAA.shader* as a shader property of *STAA* component

### Settings
- *Pattern* – sub-pixel sampling pattern (2x Quincunx, 4x, 8x). More samples means better quality for static image but more noticeable (longer) jittering after any changes.
- *Rejection* – sensitivity of a fallback to a simply unjittered raw pixel. Prevents ghosting

### Combination with another anti-aliasing

###### Wrapping ("or")
Usually rejected pixels fall back to raw frame data. But that data can be altered with a help of *STAAResolve.cs* which will let different AA algorithms do their best. To make it work a components should go in this order:
- *STAA*
- any non-jittering anti-aliasing image effects
- *STAA Resolve*

For this case the pattern should be at least 4x (a lone 2x Quincunx usually look worse than FXAA).

###### Addition ("and")
If you're okay with a not very crisp output, you can try to combine *STAA* with another anti-aliasing image effect without using *STAAResolve*. The 2x Quincunx pattern works best for that purpose, since it needs only one extra frame to recreate all history data after image changes.

### Known Issues
- Orthographic camera projection is currently not supported

### License
Copyright (c) 2016 Andrey Saraev

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
