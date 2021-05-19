# Story-lang
Used for storyboard-ing user experiences, Story-lang is a verbal and notation language with an addressing scheme. It is a JSON compatible. The language has been designed to bring more precision and clarity to interactions among people involved in UX, design, front-end and back-end work.

Inspiration to create this was drawn from music notations.<br>
![Story-lang notations](https://wildfiretech.co/theme/assets/img/bach-notes.png)<br>
<em>Above: Hand-written musical notation by J. S. Bach (1685–1750).</em>

<hr>

## storyboard
a single layout, with a single defined purpose. goes from 0% scroll to 100% (or infinite, in the case of endless scrolling pages). could also go to -100% or minus-infinity.
<br>
it's data is defined by a single model object.
<br>
there are 4 types of storyboards:
- single - a single object. naming scheme: &lt;content-type&gt;-&lt;url-slug.
- archive - listing objects within the same type. naming scheme: archive-&lt;content-type.
- search - single or multi-type listing of objects. naming scheme: search.
- index - an entirely customised experience, might have hard-coded components. usually home page or landing pages. naming scheme: index or index-&lt;url-slug&gt;.

## movement

### story-line
y-axis thumb movement. scrolling up or down can be:
- continuous type, that has a base scroll speed.
- can be snapped to fit one full frame per scroll up or down.
- it could have a custom transition on scroll up or down.

### swipe-line
x-axis thumb movement. swiping left or right can be:
- csnapped to fit one full frame per swipe, like a slideshow.
- continuous type, that has a base scroll speed.
- it could have a custom transition on swipe.

### line-angle
you can angle your story-line or swipe-line to experiment with user experience.

## address

### frame
whatever is in one viewport, 100% height and 100% width. in css terms - 100vh and 100vw.
<br>
addressing scheme: F0, F1, F2 and so on downwards. to go upwards, use rF1, rF2 and so on upwards. F0 and rF0 lead to the same central frame.

### thread
frames are placed one below the other, tied to a thread.<br>
you can place multiple threads one behind the other.<br>
when you scroll down, each thread can have a different scroll speed.<br>
<br>
addressing scheme: T0, T1, T2 and so on, going deeper into the Z axis. rT1, rT2 and so on, can be used for layering on top of the base thread T0.

### thread-speed
defined in number of times it should be faster or slower than base scroll speed of the story-line.<br>
addressing scheme: x1, x2, x1.3, x0.3 for faster scroll speed, and rx2, rx1.2 for slower scroll speed. relative to story-line base scroll speed. x0 will result in a thread fixed on it's first frame.

### components
elements within a frame. story-lang covers:
- placement of components
- transitions, how each component loads and unloads
- priority of display, which helps handling multiple screen sizes
<br>
<em><strong>note:</strong> story-lang does not have a vocabulary to define things inside components. typically that's something content brief and brand-guidelines have - things like heading text, description text, image, typography, letter-spacing and so on. we use bootstrap extensively, which gives a robust language for intra-component consistency.</em>

### timeline
immersive experience within a component, like watching a video or drawing on a canvas.

### navs
menus, navbars other navigation buttons are components. story-lang covers:
- how navs unroll and roll-back, their animation and transition.
- positioning them in the storyboard.

### cards
a component used to describe a unit that encapsulates a restricted content experience, something that can package a single content piece and it's metadata. like a post, a tweet card or a swipe-story.

### addressing scheme
parts of the addressing scheme have to be separated by hyphen.
- component address: thread-frame-component:(x,y)
- frame address: thread-frame.
- thread address: thread:&lt;thread-speed&gt; // examples: T1:x2, T0:rx1.1, T0, rT1.
- if thread is not defined, assume value T0.
- if frame is not defined, assume value F0.
- if thread-speed is not defined, assume value x1.
<em>addressing scheme example: a fixed to top navbar component would be on address rT1:x0-F0-C0:(0,0).</em>