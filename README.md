# Alien inv8sion

__Work in progress! 😉__

A fun project for [Octojam 8](https://itch.io/jam/octojam-8). Challenge: write a
game for the illustrious Chip-8 platform in the month of October.

To play:

  * Open this in a new tab: [Suggested soundtrack](https://www.youtube.com/watch?v=Pz1a9MM-Vn4&ab_channel=ThePrimeThanatos) 🎶😄
  * [Start the game in your browser!](https://timendus.github.io/alien-inv8sion/silicon8) (full colours)
  * Or: [run the game in the Octo interpreter](https://timendus.github.io/alien-inv8sion/octo), to prove it's still just a regular XO-CHIP game 😉 (reduced colours)

Controls:
  * Arrow keys or WASD to control your ship (or keys 5, 7, 8 and 9 on mobile / Cosmac VIP)
  * E or spacebar to fire lasers (or key 6 on mobile / Cosmac VIP)

(If you like this, you may also like my submission from last year, [3D Viper
Maze](https://github.com/Timendus/3d-viper-maze))

## The concept

Alien inv8sion is a nod to the endless stream of space shooters that popped up
in the late 70s and early 80s after the popularity of the game Space Invaders
from 1978. This is very much the exact same period in which CHIP-8 became
popular, and there are a lot of Space Invaders clones and other space shooters
for CHIP-8. Time to add my twist on the theme to the fray!

Having recently developed a WebAssembly CHIP-8, SCHIP and XO-CHIP interpreter
called [Silicon8](https://github.com/Timendus/silicon8) that supports the full
range of XO-CHIPs potential colour space [[1]](#notes) (a whole whopping 16
colours!) I figured it would be a shame not to make use of those colours in my
next game. So I did, and I bumped the virtual CPU speed to something absolutely
insane to bring CHIP-8 (or more specifically XO-CHIP) much closer to the coveted
arcade systems, or even systems like the NES from 1985.

Unfortunately I didn't have very much time to work on this game this year, and
the actual gameplay isn't what you may expect from an arcade or NES game. But
it's fun to play around with, and as a demo of what CHIP-8 can do if pushed: a
fully animated colourful parallax background with lots of masked sprites flying
across the screen!

### Notes

[1] See the [XO-CHIP
specification](https://github.com/JohnEarnest/Octo/blob/gh-pages/docs/XO-ChipSpecification.md#bitplanes),
specifically the last lines about bitplanes. I think Silicon8 is probably the
first interpreter to actually implement this "hidden feature"?

## Development notes

### Day one: Ambitious beginnings

Taking inspiration from the good old days, I thought it would be cool to do
something with [parallax
scrolling](https://en.wikipedia.org/wiki/Parallax_scrolling) this year, to
create the illusion of depth. Also, having kind-of finished my interpreter slash
emulator [Silicon8](https://github.com/Timendus/silicon8), I thought it would be
really neat to make something that could show off its 16 colour abilities.

My first idea was to make a cartoony side scrolling platform game, maybe
something with a spider wanting to get inside where its warm. Drawing
inspiration from the fact that this is the eighth installment of Octojam, I
thought something with an eight legged protagonist made sense 🕷

With these ideas in mind I started work on a couple of rendering routines that
operate on a display buffer in memory. Having multiple things on top of each
other (parallax layers, platforms, player and enemy sprites) required me to be
able to mask out parts of the existing image. The XOR sprite routine of CHIP-8
is not up to such a task. And I need to be able to operate on four separate
planes to use all 16 colours.

But it quickly became obvious that I basically had no time available for a
project of this size. Last year I had quite a bit of time on my hands because
everything fun in the world was cancelled due to the Corona virus. But this year
we had plans to go hiking for a week, and my date just moved in. So lots to do
and too little time to do it in, and day two just didn't come for three weeks.

### Day two: Running out of time already?!

With just five days left to participate in the jam, I needed to switch gears
pretty fast. A platform game with multiple levels and a storyline was clearly
out of the question. But the basic rendering stuff was there to do something
with overlapping sprites and I still really wanted to show off my 16 colours and
build something that had parallax scrolling. It just needed to be more simple
and less design intensive.

So I made a quick sketch and got to work on a quick and dirty side scrolling
space shooter. First, I finished the masking stuff and added more planes to be
able to use colour. A couple of ugly sprites and some maths later and I had
something that resembled a parallax scrolling background. Not being able to
render sprites partly off screen on the left side was an issue I didn't feel
like solving, so I hid the crime behind a status bar 😉 The spidery player sprite
changed into a spaceship that could shoot lasers, and we were off to the races.

### Day three: Give me something to shoot!

Shooting lasers is no fun without anything to shoot, so on day three I added the
enemy spaceships. An endless stream of enemy ships had to come in from the
right, with the player having to keep them at bay. A "fast paced version of
space invaders" seemed like a good place to start.

To accomplish this, I created a table in memory, 30 rows long, that holds the
properties of all the alien ships. Every so often the game triggers half of
those rows to become one of two types of enemy ships. When the ship gets shot,
its type changes to "explosion" (which is crudely animated) and then gets
another 50% chance to restart. The same goes for ships that reach the other side
of the screen, but without the explosions. All in all, this gives the player
a lot to shoot at, and it feels pretty dynamic, like waves of enemies attacking.

Of course shooting alien spaceships is very little fun without a counter keeping
track of how many baddies you have shot. So I added a score counter that counts
up to 255. When it overflows you go up a level, and the ships get faster. When
alien ships reach the left side of the screen, you lose ten points. So at some
point it gets pretty difficult to get to the next level.

I'm not sure where to go next. It's not really fun to get stuck on some level.
But it can be a competition with friends to see who gets the furthest, I guess.
Also, I feel like there should be some danger involved, like the enemies
shooting back or colliding in to you. I think I have to sleep on this 😄

### Day four: Pixel art

Still not entirely sure how I was going to fix the gameplay, I spent an evening
doing pixel art. The parallax background was really crude the first time around,
so I gave it a do-over. Same with the explosion animation and the alien UFO
ship. Looking a bit less bad this time 😜

## TODO LIST

* [ ] Make shooting aliens more accurate (bounding box)
* [ ] Fix exploding aliens
  * Move exploding aliens up a pixel
  * Don't blow up blown up aliens
* [ ] Make the game more dangerous
  * Make enemies shoot you?
  * Make collisions with enemies hurt?
  * Give player health?
* [ ] Work on the weapon system
  * Add a big bomb that you can trigger once in a while?
  * Lasers or bombs use up energy to shoot?
