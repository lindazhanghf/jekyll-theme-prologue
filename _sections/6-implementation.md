---
title: Implementation
icon: fa-code
order: 6
---

The gesture recognition system is implemented using an HTC Vive headset, two Valve Index controllers, SteamVR Unity Plugin v2.5 and Unity Engine. Unity made the implementation of the VR visualization itself relatively simple but the project had to solve a number of challenges to implement particularly the gesture recognition.

### First Stage: Arm Gesture Detection

The first prototype is a simple scene where the relative position of hands with other parts of the body is used to detect arm gestures. This stage served as an exploration of the technical design space.

  <div class="5u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter1_cross-body.png" alt="Multiple trigger zones was used to detect simple arm gestures" /></a>
      <header>
        <h3>Multiple trigger zones was used to detect simple arm gestures</h3>
      </header>
    </div>
  </div>

The relative position of hands (represented by the two small cubes in the middle) compared to the position of the head (represented by the sphere) and chest area (represented by the capsule) is used to detect simple gestures. The two outer boxes mark the areas for the left and right arm span, used to detect which side of the body.

### Second Stage: Gesture Recognition based on TraceMatch

Basic gestures like ***SELECT*** and ***ACTIVATE*** were implemented in this stage. The detection of hand gestures involved using the “finger curl” data from the Valve Index Controller, which can be retrieved via SteamVR Unity Plugin.

<div class="row">
  <div class="4u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter2_point_cropped.png" alt="SELECT gesture" /></a>
      <header>
        <h3><b><i>SELECT</i></b> gesture</h3>
      </header>
    </div>
  </div>
  <div class="6u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter2_activate_annotated.png" alt="ACTIVATE gesture" /></a>
      <header>
        <h3><b><i>ACTIVATE</i></b> gesture (red dot shows the center of the circle)</h3>
      </header>
    </div>
  </div>
</div>


***SELECT*** is detected when the player's hand is doing a pointing gesture. While the user is doing the ***SELECT*** gesture, the system uses Raycast from the Unity physics engine to detect where the user is pointing. If the Raycast hits an object that can be interacted by the user, it will start glowing blue to indicate that it is interactable. This responds again to Shneiderman’s principle of direct feedback.

For the ***ACTIVATE*** gesture, the system needs to detect when the player's hand is drawing circles. The algorithm is inspired by the motion matching process described in TraceMatch <sub>[clarke2016tracematch]</sub>. The earliest data point is marked as the start of the circle, which is used to calculate the angle of the curve.
Once the angle between the start of the circle and the latest data point has accumulated over 360◦, this means the hand has finished drawing a full circle, and thus the ***ACTIVATE*** gesture is fired.

## Final Prototype
As the design emerged and the technical gesture recognition fell into place, the VR world was developed and an animal companion was added into the project. This stage consisted of a gradual build up of a 3D world that would showcase the gesture-based interaction in a VR condition. It also required gradual adjustment of the gestures to the actual VR condition as it became functional.

<div class="row">
  <div class="5u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter3_activating.png" alt="Start ACTIVATE gesture" /></a>
      <header>
        <h3><b><i>ACTIVATE</i></b> Gesture Start: the player starts by drawing circles with open palm (purple dot shows the center of the circle)</h3>
      </header>
    </div>
  </div>
  <div class="5u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter3_activated_cropped.png" alt="After ACTIVATE gesture" /></a>
      <header>
        <h3><b><i>ACTIVATE</i></b> Gesture End: the companion starts flying to indicate that it is activated</h3>
      </header>
    </div>
  </div>
</div>


To better indicate that the gesture ***ACTIVATE*** is triggered and the companion is activated, the **animation** of the companion changes to a different state. In this case, the bird companion changed from a **standing pose** (left image) to a **flying pose** (right image), showing that it is ready to do the next action. Additionaly, the color of the outline is changed to bright green for better visibility.

<div class="row">
  <div class="5u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter3_action.png" alt="ACTION Gesture" /></a>
      <header>
        <h3><b><i>ACTION</i></b> Gesture</h3>
      </header>
    </div>
  </div>
  <div class="6u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/iter3_cancel.png" alt="CANCEL Gesture" /></a>
      <header>
        <h3><b><i>CANCEL</i></b> Gesture</h3>
      </header>
    </div>
  </div>
</div>

The ***ACTION*** is a throwing gesture. It was first implemented using the TraceMatch algorithm. Once the hand is detected as moving in a circular motion, the angle of the curve is calculated. Unlike ***ACTIVATE*** which requires a full circle, ***ACTION*** is detected when the angle of the curve has accumulated over 60◦.

However, through extensive testing, this version of the ***ACTION*** gesture detection turned out to not work very well. The throwing motion did not match a circle most of the time, as it might be a short curve in the shape of an ellipse or in a straight line. Therefore, in the final version the ***ACTION*** gesture is changed to: close the palm to indicate the start of the throwing gesture (to mimic the action of throwing items held in the hand), then open the palm afterwards to indicate the end of the gesture (the hand has released the items thrown), at both point the hand positions will be recorded. The direction of the ***ACTION*** gesture is then calculated using the vector bounded by the two positions.

The last gesture implemented is ***CANCEL***, which is a "stop" hand gesture--both palms open with the tip of the hands pointing upwards. This is implemented by calculating the rotation of both hands to see if they are both within the threshold of the upward angle.
