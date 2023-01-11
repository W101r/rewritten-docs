# Welcome to the W101r Docs

This library is for all developmental documentations of the Wizard101Rewritten project.

Writings include technical explainations of game internals, as well as guided steps to how our emulator works in written form.

## Our Projects
### Imlight
Imlight is the endgoal of W101r. It's intended to be the successor to Ravenwood (see below). It's primary goal is continuing the reverse engineering hurdles while simultaneously creating a practical, robust
server. Each server is controlled by a series of nodes, each working in unison to emulate Kingsisle's backend service.

You can view an overview of the architecture [here](https://drive.google.com/file/d/17utqstWzrlxPp8cVjTZX4e_Hhy8ThKSn/view).
### Ravenwood
Ravenwood is the elder of W101r. This is the progress shown in the announcements [channel](https://discord.com/channels/868474951106183188/868474951185858583).

Ravenwood now primarily serves as a research project with no intention of being the actual implementation of our final server.

### Mythos
When a rewrite was called for Ravenwood, Mythos was the answer. Still under core development, Mythos is an emulator rewritten in JavaScript. Due to the functionalities of JavaScript, 
there was an obvious conflict between the dynamic nature of JS and the static types of C++, Wizard101's underlying language.

Mythos now primarily serves as a practical code example of emulating Wizard101's backend system in a language other than C#.

## Contributing
Contributions are welcome by Wizard101Rewritten developers _only_.

We ask that contributors follow the main staples of contributions. Development should happen on branches, which are requested to main to be reviewed and pulled.

Review proper branch naming conventions [here](https://codingsight.com/git-branching-naming-convention-best-practices/).