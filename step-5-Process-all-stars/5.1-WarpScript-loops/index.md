---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
title: 'Step 5.1: Back to WarpScript bascis: the loop'
category: step-5
before: 'step-4-First-Exo-Detection/4.3-Threshold-test-and-display'
next: 'step-5-Process-all-stars/5.2-Optimize-global-analysis'
solution: 'step-5-Process-all-stars/5.1-WarpScript-loops/solutions'
---

Now that you completed your intial training as an exoplanet hunter, let's see how the loops are implemented in WarpScript to be able to generalize your analysis to all the available Kepler's stars.

## FOREACH

Let's admit that you want to compute an **addition** on WarpScript of all the elements inside a list.

The [`FOREACH`]({{ site.doc_url }}/reference/functions/function_FOREACH/) function can be used to implement it. Complete the skeleton below were the value 0 is the first element pushed in the stack. In WarpScript the `FOREACH` functions expect a `MACRO` on top of the stack and a list of element. To start a macro use the keyword `<%` and to end it use the keyword `%>`. 

What will do the `FOREACH` function? 

The list will be droped of the stack, so at the start of the `FOREACH` process only the value 0 is on top of the stack. Then during the process of the foreach, each element will be pushed on top of the stack one after an other. You will just have compute an addition inside the macro. The increasing value will stay on top of the stack until the end of the script.

<warp10-embeddable-quantum warpscript="
//
// FOREACH
//


// The initial sum count
0

// The list on which the count will be applied
[ 1 2 3 4 ]

// Write the MACRO




// Call FOREACH function
">
</warp10-embeddable-quantum>

## LMAP

The [`LMAP`]({{ site.doc_url }}/reference/functions/function_LMAP/) function will on the other side compute an operation on each elements of a list.

Let's say that for example, we would like to add 1 to each element of the previous list.

As the `FOREACH` function, `LMAP` takes two parameter: a list and a macro. `LMAP` will recompute as output a list. Inside the `LMAP` macro, you will get two elements pushed inside of the stack: the current element and then the index. In our case to correctly apply only our addition, we will need to delete the index of the stack. This means that the first element to be put inside the `LMAP` macro is the function `DROP` (used to delete the current element on top of the stack).

<warp10-embeddable-quantum warpscript="
//
// LMAP
//

// The list on which one will be added to each elements
[ 1 2 3 4 ]

// Write the MACRO

 
 
 

// Call LMAP function
">
</warp10-embeddable-quantum>

## To be continued

Now that you understand the theory about the WarpScript loops, let's now see in practice how we can use them to process all the stars!

