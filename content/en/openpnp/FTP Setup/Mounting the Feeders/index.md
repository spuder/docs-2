---
title: "Mounting the Feeders"
linkTitle: "Mounting the Feeders"
weight: 80
type: docs
description: >
  Mounting the Feeders
---

Next we'll load the tray feeders with the resisters and LEDs we'll be using to run the FTP.

## Physical Mounting

1. Use four M3x8mm screws and four M3 nuts to affix the tray feeder to the staging plate with the trays facing vertically (in the Y axis).
2. Peel off a little bit of the clear plastic tape on the surface of the component strips. Don't uncover any components yet or they'll fall out of the strip. This is to make it easier to pull on the tape later.
3. Slide the strips of Resistors and LEDs into the tray until the first component in each package reaches the edge of the tray.

## OpenPnP Definition

4. In OpenPnP, go to the Feeders tab.
5. Click on the "Add Feeder Button" and select `ReferenceTrayFeeder`.
6. Select the new feeder from the list and set the following settings:
   1. Y Tray Count: `30`
   2. Y Offsets: `4`
   3. Pick Location X: `xxx` (If using the pictured location) <!-- TODO: figure out good default X and Y Locations -->
   4. Pick Location Y: `xxx` (If using the pictured location)
   5. Pick Location Z: `12.2`
7. Repeat these steps for your second feeder, but change the Pick Location X to: `xxx`

## Fine-tuning Feeder Location

Feeders don't have fiducials, so we'll need to dial in their locations by hand. For successful picking of components, you will need a well-calibrated nozzle offset, and a tight motion system without backlash or loose belts, etc. If you're having trouble with consistently picking components, see the Troubleshooting section for more help.

8. Click the button to position the camera over the feeder position.
9. In the down camera view, drag the crosshair over the center of the slot for first component. This should be very exact.
10. Update the feeder's pick location with the camera's location
11. Double-check that you've set a Pick Location position for the Z axis (otherwise your toolhead will stab the component strip).
12. Position the nozzle over the feeder and check that the nozzle is located over the component. If not, double-check your nozzle offset and each axis' backlash settings.
13. When you're ready, try picking a component!
    1. If the nozzle is offset, double-check your nozzle offset and each axis' backlash settings
    2. If the nozzle didn't lower far enough to touch the component, adjust the Pick Location Z setting by subtracting 0.05mm at a time.
    3. Use the Special > Recycle button to replace the component if it was successfully picked up, or to reset the feed count.
14. Note: each time you pick up a component, the Feed Count will go up by one. The next time OpenPnP goes to pick up a component it will search for it in the next slot along in the tray. You can reset this back to the top of the

## How feeders work in OpenPnP

A feeder defines where OpenPnP will pick up components to place on your PCB. There are a few different kinds of feeders, but the one that we've validated for the LumenPnP for now is the `ReferenceTrayFeeder`. This is the simplest feeder, where there is just a strip of exposed components waiting to be picked up by the LumenPnP's toolhead. You'll define the location of the feeder, how many components are exposed and ready to be picked up, and how far they're spaced apart. It's typical just use one long strip of components, but you can also use ReferenceTrayFeeders for an array of components in the X and Y directions. After importing our job in OpenPnP later, we'll also mark which component is loaded into which feeder so OpenPnP knows where to pick up the correct component.

Every time a component is picked up from a feeder, the "Feed Count" goes up by one, and so OpenPnP will tell the machine to look in the next location for the next component. When you eventually run out of exposed components, OpenPnP will pause the job and tell you to advance the feeder by hand, reset the feed count, and then resume the picking operation.

## When a feeder is empty

15. Pull the strip of components through until a slot with a component in it is at the top of the tray.
16. Reset the Feed Count.
17. Peel back the plastic film to expose the components.
18. Follow the Fine-tuning Feeder Location steps again to double-check the starting location for the feeder.
