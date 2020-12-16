---
title: Design
icon: fa-drafting-compass
order: 5
---
The design of the gesture interface went through several iterations before settling down on human-animal interactions the final prototype version.


### Gestures inspired by Eagle Hunters

The first design of the gesture interface was inspired by eagle hunters. Through analyzing documentaries on Mongolian eagle hunters, the body languages used by eagle hunters to communicate with the eagles were identified.
<!-- \cite{eaglehuntress2016} \cite{mongoliaeaglehunter2017}. -->
Shown in the sketches below, the main gestures to interact with the bird companion are:
- **Direct**: direct the bird companion to interact with a target. Similar to the way eagle hunters kept their eagles on their arms, the bird companion starts off on the player's arm. Once the player raises an arm, the bird will fly upwards, awaiting further directions. The player then uses the point gesture to **direct** the bird to fly over and interact, or in this case, attack the target.
- **Return**: instruct the bird companion to return after (or during) the interaction. Once the bird has finished interacting with the target, the player can instruct it to **return** by swinging the arm in a backwards motion. Once the bird starts to fly back, the player can raise the arm for the bird to stand on.

<div class="row">
  <div class="5u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/design1-eagle-attack.png" alt="Gesture for Direct" /></a>
      <header>
        <h3>Gesture for <b>Direct</b></h3>
      </header>
    </div>
  </div>
  <div class="6u 12u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/design1-eagle-return.png" alt="Gesture for Return" /></a>
      <header>
        <h3>Gesture for <b>Return</b></h3>
      </header>
    </div>
  </div>
</div>

### Sign language Inspired Gesture Design
Through learning basic American sign languages, I was especially drawn to the concept of Spatial Grammar. As sign languages are not used in a linear sense, the subject and object of a verb cannot be derived from word order, hence the usage of spatial grammar. Usually, before signers describe an event, they establish the spatial relationship of the entities by "putting" each entity on an imaginary plane in front of them.

Inspired by this concept, I designed two interaction scheme that make use of spatial grammar to define entities. Once the entities are defined, the players can perform gestures that describe the interaction between the entities, and informs the direction of the action if necessary.

<!-- Two different interaction schemes based on the function of dominant vs. non-dominant hand:
- Different Functionality: While the dominant hand is pointing at a target, the non-dominant hand does the gesture to perform actions on the target. After the gesture is performed, the dominant hand then points at another target to indicate the object of the action.
- Same Functionality: The left and right hand each point at the target objects to interact (the player can be one of the objects). After selecting the objects, both hands perform the gesture to show the intended action between the two objects. -->

### User-defined Gestures with Reward-based Behavior Modification

The idea is to incorporate the process of defining gestures into the gameplay. This is inspired by reward-based behavior modification which is used by both dog trainers and eagle hunters.

During the process of raising and bonding with the animal companion, the player uses food as rewards to teach the companion gestures for the following commands:
- **Focus**: get the attention of the companion.
- **Direction**: instruct the companion to face the target.
- **Action**: instruct the companion to go to the target and interact with the target.

However, since the implementation of user-defined gesture recognition is not feasible within the time constraint, this design was eventually changed to pre-designed gestures based on human-animal interaction.

### Final Design: Gestures based on Human-animal Interaction

<!-- Another human-animal condition is that between humans and dogs.  -->
The final design was inspired by how I interact with my dog at home. Here, the user-defined gestures emerge in a kind of shared condition between the dog and the owner. In my case: the rotation of my hand leads to the dog to roll over on the floor.

<div class="row">
  <div class="5u 8u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/AlongRolling.gif" alt="Dog rolling over responding to the gesture of rotating hand" /></a>
      <header>
        <h3>Directing my dog to roll over using the circle gesture</h3>
      </header>
    </div>
  </div>
  <div class="5u 8u$(mobile)">
    <div class="item">
      <a class="image fit"><img src="assets/images/project/DogPlayingFetch.gif" alt="A dog playing fetch" /></a>
      <header>
        <h3>A dog playing fetch</h3>
      </header>
    </div>
  </div>
</div>
The design targets for the gesture interface are defined in the table below:

| Interaction | Pet Gesture | Hand Gesture |
| --- | ----------- | --- |
| SELECT| Call name to get its attention | Point
| ACTIVATE| Draw circles to make it roll over | Circle
| ACTION| Throw sticks for it to fetch | Throw
| CANCEL| Call name while clapping Hand | Stop

