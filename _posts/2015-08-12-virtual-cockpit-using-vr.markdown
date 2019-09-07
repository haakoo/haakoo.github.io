---
layout: post
title: Virtual cockpit using VR
date: '2015-08-12 07:30:00'
tags:
- oculus-rift
- vr
- virtual-reality
- situational-awareness
- unmanned-vehicles
- command-and-control
---

On Friday I had the pleasure of trying Oculus Rift in a setting where it finally _made sense_ to me. I've been disappointed when trying Oculus Rift on previous occasions and had the same feeling as Jeff Atwood (Codinghorror): 

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">VR, in its current form, might be a tad overhyped. <a href="http://t.co/M9uU3F4W8e">http://t.co/M9uU3F4W8e</a> <a href="http://t.co/TaZkzSHHVp">pic.twitter.com/TaZkzSHHVp</a></p>&mdash; Jeff Atwood (@codinghorror) <a href="https://twitter.com/codinghorror/status/629390603957088256">August 6, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I've leaned a bit more towards _"meh"_ than _OK_, but my general feeling has been that <dfn><abbr title="Virtual reality">VR</abbr></dfn> is over-hyped. Jeff comes at it from a different angle than me though, him being a gamer and general _consumer_ of VR. My perspective is through my work with unmanned vehicles and situational awareness. Reading his [blog post](http://blog.codinghorror.com/i-tried-vr-and-it-was-just-ok/) the same day I experienced VR that _just works_, I realised I should write down my thoughts about VR for situational awareness in unmanned systems or other remote operated systems.



## Why situational awareness and not automation?
For unmanned vehicles the goal is to make them autonomous enough so that we don't need a human to control each individual vehicle. I think this is still several years into the future for larger more complex systems, especially if you want to benefit from data gathered in (close to) real time.

Therefore I believe that there is a need for an interim solution for <dfn><abbr title="Unmanned x (aerial / ground / surface / under water) vehicle">UxV</abbr></dfn> control systems that help the operator obtain and maintain situational awareness.



## Situational awareness for unmanned vehicles
One of the main challenges when controlling a remote operated vehicle is local situational awareness. You basically want to know what's going on around your vehicle and if it will limit your freedom of movement. I've seen several solutions trying to solve this problem, from cramming all the information into a couple of vertically stacked displays to using large, curved, multi-display set-ups that surround the operator. These solutions require fairly large rooms, lots of expensive screens and then they end up not working all that well.

This is where my experience from Friday changed my view on virtual reality. When I put on the Oculus Rift (I think it was the DK2 model) I could turn my head to look around the small unmanned ground vehicle (<dfn><abbr title="Unmanned ground vehicle">UGV</abbr></dfn>) I controlled. What made this implementation different from other earlier solutions I've seen, was that there were no moving parts that twisted a camera around, but ten fixed cameras. All the cameras streamed video to a computer which then created a virtual _cinema_ / _control room_ / _cockpit_ with a screen for each video feed. The cameras and screens were rotated 90 degrees, into portrait format, to give a better vertical field of view (<dfn><abbr title="Field of view">FOV</abbr></dfn>). The user was then placed inside this virtual cockpit where she could look around the circle of screens surrounding her.

This solved one of the main problems I've seen with earlier demonstrations. There was no head tracking jitter / lag! The virtual cockpit ran with ~75 Hz refresh rate, so my head movement felt natural and jitter free. This means that even though the video feeds were only 30 fps, placing them on virtual screens made this a very comfortable user experience.

When driving the vehicle around, there was a small but noticeable delay in the video feed. This made it slightly awkward driving close to other objects, but had no effect on me and how I felt when wearing VR-goggles. This is the same problem all remote controlled systems have when there is a delay between user input and feedback and usually results in small, jerky movements with short pauses between.



## Problems and possible improvements
This was a very rough first implementation with lots of problems. One of the first issues I noticed was that the cameras had different exposures. The cameras were left on auto exposure so two adjoining cameras could have quite different colour and brightness. This should be easy to fix by taking control over the cameras' exposures.

The next problem I noticed was with the FOV. The ten cameras were not perfectly aligned and thus had varying degrees of overlap. Combine that with no correction for lens distortion and the edge between cameras didn't match very well.

Another problem with this technology demonstrator was that they streamed all ten video feeds through wifi to a computer. That was a whopping ~240 Mbit/s of data just for the camera feeds! This and the previous issue can be corrected by preprocessing the images before they are sent from the vehicle. By adjusting the camera exposure and stitching the videos together before transmitting only the _needed_ video, the amount of data to transfer is reduced and the video will look better. This might introduce some latency, but only to the picture displayed on the virtual screens, and it shouldn't affect how the user experiences head movement. One challenge with this approach is to figure out what part of the stitched video is _needed_. Ideally the system will transfer the main FOV in high resolution and the rest of the FOV with lower resolution to allow the user rapid head movement without seeing blank virtual screens. When the user moves her head the system should automatically increase the resolution for the new FOV, while reducing it for the now out of view video.

I also had a bit of trouble figuring out my viewpoint in relation to the vehicle. There was a compass rose that went around me in the virtual cockpit, but it was fixed related to the vehicle rather than giving an actual bearing. When I turned the vehicle around while holding my head still the compass direction in my view did not change. This was a bit confusing at first, but when I figured out that north-east (NE) on the compass was straight forward relative to the UGV it worked OK. It would have been better having two different graphical elements, one for actual compass direction and one for vehicle orientation.

Being used to having a map as one of the main views during operations, I realised that the virtual cockpit could easily contain that and more. It has always felt natural to look down at a map for me, so placing a map view in my virtual lap seems like a brilliant idea. I would still have an unobstructed view of the surroundings and quick access to a map with the overview of the situation.



## Last thoughts
This post ended up a bit longer than I first intended, but I think it turned out well. It's in no way a comprehensive discussion of VR and unmanned systems, but it summarises most of my (present) thoughts around VR and its usage regarding remote operated vehicles and systems. I didn't touch on the subject of immersion here, and I plan to write more about that in a future post.

I'm pretty sure the market for VR-glasses by professionals, where they control remote systems and need to look around, ends up being larger than that for private entertainment.


--- 

Cover photo "[Full Flight Simulator](https://www.flickr.com/photos/superjetinternational/5573438825/)" by [SuperJet International
](https://www.flickr.com/photos/superjetinternational/) is licensed under [CC-BY-SA-2.0](https://creativecommons.org/licenses/by-sa/2.0/)