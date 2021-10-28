# Untitled space shooter

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

## TODO LIST

* [ ] Add moving enemies
* [ ] Allow shooting enemies
* [ ] Make enemies shoot you
* [ ] Make collisions with enemies hurt
* [ ] Keep score of health and points
* [ ] Something resembling levels?
* [ ] More pretty background pixel art
