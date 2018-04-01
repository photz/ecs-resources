# Resources Related to Entity Component Systems


## General discussions of the paradigm

* [Ramblings on Data Oriented Design by Richard Fabian][25]
* [Entity Systems are the future of MMOG development – Part 2][28]

## Migrating an existing codebase to ECS

* [Switching Win That War! to the Entity-Component-System Pattern][27]

## Dealing with Relationships between Entities

## Introducing workers

* [The Future of the Game Engine][17]
  Introduces an approach that the author terms a 'Entity-Component-Worker architecture'

## Critiques of an over-zealous application of the ECS pattern

* [Sane Usage of Components and Entity Systems][16]
  Offers a historical perspective that takes into account what led to the current popularity of ECS and Component Based Architecture in general.  

## Development of additional tools such as editors

* Creating an entity inspector that makes it possible to edit components while the simulation is running

## General introductions

* [Introduction written by the author of the Ash entity system framework][0]
* [L'Entity Component System - Qu'est ce que c'est et comment bien s'en servir ?][3]
* [Chapter devoted to ECS in the book Game Programming Patterns][4]

* [Wikipedia Article on Entity-component-systems][22]

## Using an events system to pass information between components

* [Answer to a question on forums.xkcd.com][13]
  Provides an example of a CollisionComponent that could emit a signal whenever two entities collide.

## Constructs to update multiple components at once

* [Answer to a question on forums.xkcd.com][14]
  Argues in favor of having a ComponentManager that updates multiple components at once to facilitate such things as collision detection or batching calls to one's rendering engine.
  Also takes into account parallelism.




## Integration with existing game-engines

* [ECS in Unity: Integration and Execution 1][12]

## Representing and Storing Entities

* Entities are represented as plain IDs in the Artemis framework.

## Specific frameworks

* Artemis for Java

* [A-Frame][18]

* [Lumberyard][19]
  An engine developed by Amazon that can be integrated with AWS and Twitch also relies on ECS.  Comes with an editor.

## How to handle player input

* [Question on StackOverflow][9]

## Architectural questions

* How to achieve that systems don't need to look at every component whenever the system is run?
  Does it make sense to apply the observer pattern here?

* How to deal with time?

* Should there be a clear distinction between physics-driven and non-physics-driven entities?


## Networking

* [Question on gamedev.net][11]

* [Article 'Networking Entities' on developer.valvesoftware.com][15]
  Differentiates between server-side only entities, client-side only entities as well as entities (the majority) that live on both the client and the server.  Discusses the engine's entity networking system as a distinct module which is responsible for such things as detecting changes, serializing them and deserializing them.
  Furthermore, a distinction is made between member variables of entities that are server-side only and those that must be transmitted to the client.  The latter are referred to as 'networked variables' and an events system is used to indicate that certain properties have been updated and need to be transmitted to the client again.


## Having an intermediate Intent System

* [Answer on StackOverflow that explains the purpose of an Intent System][10]
  The IntentSystem would be responsible for interfacing with the physical input devices and translate such things as button presses into intentions like running, jumping or reloading one's weapon.
  Also discusses an extension which the author terms 'Intent Context'.  Also suggests that different sets of times could be used, say one for the simulation itself and another one that keeps running even when simulation is paused.

## Setting up something like an EntityManager (container for entities)

* [Stackoverflow user who wrote a game engine based on ECS with an Entitymanager and 'processes' that act on groups of components][7]

## Case studies

* [How to Build an Entity Component System Game in Javascript][2]
  The author develops a simple game in Javascript based on an ECS.  

* [Better Tower Defense][20]
  Describes the challenges involved in the development of a new Tower Defense game built on top of an ECS.  The author attempts to refine ECS to better deal with the fact that the order in which systems update components matters.  The author views Systems in an ECS as state transformation functions.  After such a transformation has been applied, the difference between the new and the previous game state is computed.  This setup makes it possible for systems to subscribe to specific changes and receive notifications.

* [Description of the ECS inside the Bitsquid Engine][24]
  Introduces ComponentManagers.  For every component there exists a separate ComponentManager that decides how components are represented.  There is therefore no abstract component class.  Also uses entity ids whose upper bits are called the 'generation' part and whose lower 22 bits are called the 'index' part.

* [Building a Data-Oriented Entity System (Part 2: Components)][26]
  Describes how the components for entities are laid out in memory in a cache-friendly manner.  Uses a PointMassComponent that describes an entity's mass, velocity, acceleration and position in a single component.

* [Scott Bilas on the ECS in Dungeon Siege][23]
 
## Implementations in different languages

* [Implementing Component-Entity-Systems][5]
  A basic ECS is implemented from scratch in plain C.  Emphasizes laying out components and entities in memory to achieve a high degree of locality.

* [Entity Component Systems in Elixir][6]

* [Entity-component-system in Clojure][21]

* [Entitas - The Entity Component System Framework for C# and Unity][29]

## How to make an implementation more cache-friendly

## Questions regarding how to choose one's components

* Does it make sense to have separate components for things such as an entity's displacement and velocity or should those properties by bundled up in a single component?

## Components other people use 

* ColliderComponent
  A component that knows an entity's bounding box.

* StateComponent
  Why have something like a StateComponent?  Doesn't every component store some aspects of an entity's state?

* ControllerComponent



## What kinds of systems to use

* [Having separate sets of systems responsible for different aspects][1]

*
## Books

* SFML Game Development by Example by Raimondas Pupius


[0]: http://www.richardlord.net/blog/ecs/what-is-an-entity-framework.html
[1]: https://gamedev.stackexchange.com/questions/56519/movement-physics-in-an-entity-component-system
[2]: http://vasir.net/blog/game-development/how-to-build-entity-component-system-in-javascript
[3]: http://guillaume.belz.free.fr/doku.php?id=ecs
[4]: http://gameprogrammingpatterns.com/component.html
[5]: https://www.gamedev.net/resources/_/technical/game-programming/implementing-component-entity-systems-r3382
[6]: http://yos.io/2016/09/17/entity-component-systems/
[7]: https://gamedev.stackexchange.com/a/34097
[8]: https://gamedev.stackexchange.com/a/34078
[9]: https://gamedev.stackexchange.com/questions/49119/input-handling-in-component-based-design
[10]: https://gamedev.stackexchange.com/a/48399
[11]: https://www.gamedev.net/topic/654619-entity-component-system-and-networking/
[12]: http://t-machine.org/index.php/2016/11/11/ecs-in-unity-integration-and-execution-1/
[13]: http://forums.xkcd.com/viewtopic.php?t=81459#p2901481
[14]: http://forums.xkcd.com/viewtopic.php?t=81459#p2901947
[15]: https://developer.valvesoftware.com/wiki/Networking_Entities
[16]: http://www.randygaul.net/2014/06/10/sane-usage-of-components-and-entity-systems/
[17]: https://improbable.io/2016/04/21/future-game-engine
[18]: https://aframe.io/docs/0.5.0/core/
[19]: https://aws.amazon.com/documentation/lumberyard/
[20]: http://jacobdufault.github.io/seniordesign/uploads/jacobdufault_plan_9_4_2013_updated.pdf
[21]: http://blog.muhuk.com/2014/06/08/entity_component_system_in_clojure.html
[22]: https://en.wikipedia.org/wiki/Entity%E2%80%93component%E2%80%93system
[23]: http://scottbilas.com/games/dungeon-siege/
[24]: http://bitsquid.blogspot.de/2014/08/building-data-oriented-entity-system.html
[25]: http://www.dataorienteddesign.com/dodmain/node14.html
[26]: http://bitsquid.blogspot.de/2014/09/building-data-oriented-entity-system.html
[27]: http://www.insaneunity.com/blog/2016/10/28/winthatwar-entity-component-system/
[28]: http://t-machine.org/index.php/2007/11/11/entity-systems-are-the-future-of-mmog-development-part-2/
[29]: https://github.com/sschmid/Entitas-CSharp
