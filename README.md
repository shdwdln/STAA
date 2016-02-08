# Simple Temporal Anti-Aliasing
*STAA* is an image effect for Unity engine. It is an atempt to implement a temporal AA based just on color data without trying to use any motion reprojection. It jitters the camera projection matrix and combine the rendered frame with history frames.

### Setup
- Add *STAA.cs* to a camera game object
- Assign *STAA.shader* as a shader property of STAA component

### Settings
- *Pattern* – sub-pixel sample count (2x Quincunx, 4x, 8x)
- *Rejection* – sensitivity of a processed pixel fallback to an unjittered raw pixel. Prevents ghosting

### Wrapping around another anti-aliasing
Usually rejected pixels fall back to raw frame data, but that data can be altered with the help of *STAAResolve.cs* to get the best of different types of anti-aliasing.

Components should go in this order:
- *STAA*
- any non-jittering anti-aliasing image effect
- *STAA Resolve*

### License
Copyright (c) 2016 Andrey Saraev

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
