---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
title: 'Step 2.2: Exploring the available time-series'
category: step-2
before: 'step-2-Keplers-Data/2.1-Did-you-said-Time-Series'
next: 'step-2-Keplers-Data/2.3-Getting-Kepler-11-raw-data'
back: 'step-2-Keplers-Data/2.2-Exploring-known-time-series'
---
 
## Solutions

<warp10-embeddable-quantum warpscript="
// Storing the token into a variable
@HELLOEXOWORLD/GETREADTOKEN 'token' STORE 

// Start the find with the token as first parameter
[ $token '~.*' {} ] FIND

// Select only Kepler-11 series
[ $token '~.*' { 'KEPLERID' '6541920' } ] FIND
">
</warp10-embeddable-quantum>