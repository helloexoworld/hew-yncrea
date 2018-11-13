---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
title: 'Step 2.2: Exploring the available time-series'
category: step-2
before: 'step-2-Keplers-Data/2.1-Did-you-said-Time-Series'
next: 'step-2-Keplers-Data/2.3-Getting-Kepler-11-raw-data'
solution: 'step-2-Keplers-Data/2.2-Exploring-known-time-series/solutions'
---

Now that you survive all the WarpScript needed knowledge, we would like to welcome warmly in our exoplanet quest! We can now observe more concretly what the NASA data looks like.

## Get a read token

Security in Warp10 instance are handled with crypto tokens. They can be pretty long, so to ease your workflow, we stored it in the platform! You can push the token into the stack using this:

<warp10-embeddable-quantum warpscript="
@HELLOEXOWORLD/GETREADTOKEN
">
</warp10-embeddable-quantum>

> You should store it as a variable using `STORE`.

## FIND

We preloaded our platform with some stars (around 30). Let's observe the series structures and find the one that we want! We are going to use a function called [`FIND`]({{ site.doc_url }}/reference/functions/function_FIND/).

How does the function `FIND` works? This function allows the user to retrieve specific meta-data of time series stored inside a Warp 10 backend. You will need to push on top of the stack a list of specific parameters. The function to work correcty will need a specific cryptographic token, remember, you saw it earlier. Let's resume how to load it. 

Before retrieving any data, you need to access data store in a specific application. To simplify the process, an existing token was stored in the platform. You can access it using the macro seen previously: `@HELLOEXOWORLD/GETREADTOKEN`. Macro corresponds to a custom user function or module in WarpScript. Starting from now, this token will be put in a variable called `token` on each script where a token is necessary to load data.

The FIND function finds Geo time seriesTM matching some criteria. To work correctly, it expects on top of the stack a LIST with 3 parameters: the previous stored Warp10 token, a classname selector and a MAP of label selectors.

The classname selector is a string which represents an exact match if it starts with an `=`, or a regular expression if it starts with `~`.

The label selectors are packed in a MAP whose keys are the label names and the values the associated selector. Those selectors can also be exact matches if they start with `=` or a regular expression if they start with `~`.

Here a preloaded WarpScript that you can use, find all the time series available!


<warp10-embeddable-quantum warpscript="
// Storing the token into a variable
@HELLOEXOWORLD/GETREADTOKEN 'token' STORE

// Start the FIND with the token as first parameter
[ 
    $token 
    // Here you must put the classname and label selectors...


] FIND
">
</warp10-embeddable-quantum>


Wow, a lot of data appeared in my quantum console. They represents all the existing series that are availble to test your exoplanet quest! Each time series have several meta-data. During this tutorial we are going to focus on the one called `sap.flux` as they represents the raw data of the lightcurve of each stars.

The one that we are looking for has a label `KEPLERID=6541920`, can you see it? Change the FIND to have only one result: `sap.flux` for Kepler-11! 

> To create a map, you can write something like this `{ 'key' 'value' }`

## To be continued

During this step you manipulated a sub-set of series extracted of the FITS data of the NASA. Now to really explore this set of data, let's obeserve what the lightcurve for the kepler-11 time series looks like. You will now learn how to extract raw data using Warp 10.
