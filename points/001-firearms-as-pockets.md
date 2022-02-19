# Firearms as Pockets

All firearms ought to be treated as pseudo-containers, for the purposes of modding, ammo management, and auxiliary uses of attachments.

In this way, each firearm would be represented by its lower receiver (which is what's considered to be the firearm itself in the US), to which there would by default be attached the standard parts of the final firearm: the upper receiver, the barrel, the sights... Ultimately, what the player ends up with is a collection of parts assembled in a way that makes the whole firearm work as intended.

This approach eliminates a number of problems and introduces an assortment of new possibilities with regards to firearms in general and certains parts of them specifically.


## Nonexistent base parts

Right now firearm attachments are treated as drop-in additions to the gun, with no exception – even if these additions are meant to replace an integral part of the gun. The latter case leaves questions like "Where did the original part go, then?". As it stands, the answer is "in the thin air" – which is also true for returning the original part back in its place by removing the replacement.

Many characteristics of the guns are assumed from a holistic model: that is, there exists an item with a given set of properties, like an apple or a metal ball, which has weight of X and damage value of Y. This is not, in fact, how most firearms work: the absolute majority of them has components which require initial assembly and may require replacement in the future, due to eventual wear.

Not rendering these parts in any manner whatsoever betrays the reality of the mechanical system that is a firearm. This is unacceptable in a game which seeks to render blood contents of a body, thermodynamics of a room, and carbon grades of steel.


## System of parts

The pseudo-container system would replace the holistic approach with providing firearms as sets of components, not unlike those of a vehicle, where each component performs a different function. Consequently, lacking a certain component may hinder or disrupt operations of a firearm, and so may employing a damaged component as part of the system.

These parts may then be replaced with jury-rigged ones (in case no genuine parts are available to replace a missing / broken one) or aftermarket ones (which may offer better performance).

These parts can also serve as sources of gun faults: it's impossible to experience a bolt jam without a semi-automatic bolt carrier. Different parts may than be graded on their performance against experiencing faults: parts made with better materials, or specifically engineered to be resistant to specific faults, are going to be more valuable. This may be reflected in rarity and / or price of a given firearm part, which would then be applied to trade price and spawn chance.

This also offers an automatic calculation of the resulting gun's physical dimensions: weight, volume, and length. 


## Parts of a system

With firearm components being synergetic in nature under the proposed system, attention could be given to common mechanics of real-world firearms.

One such mechanic is pressure of the gas feeding back into the system in semi-automatic guns. This gas is what drives the feeding mechanism: chambering the next round from the magazine, after ejecting the shell case of the round that's just been fired. The amount of gas produced is directly affected by the gunpowder used in the cartridge, which evaporates rapidly under the shock of ignition, producing expanding gases which drive the bullet down and out the barrel.

If the pressure is sufficient relative to the weight of the bolt carrier, the system operates with minimal errors, ejecting shells out and feeding cartridges in smoothly. If the system is underpressured, it may lead to failures to eject, whereby the shell gets stuck within the ejection system (usually between the bolt and the frame of the ejection port). This could be alleviated manually by forcing the ejection, but this risk of a sudden stoppage during combat may mean the difference between life and death.

Overpressure, on the other hand, may be useful. While overpressure of the gases leads to a more forceful bolt operation, leading to more recoil, this same pressure means the gas is able to push through more fouling, meaning the firearm becomes more reliable despite dirt inside it. Dirtying of the gun may occur from environmental factors as well as from operation: for example, dropping it in the mud or in the sand.


## Containers within containers

Because the proposed system relies entirely on the containers system, it would natively enable storing items inside parts of the firearm. This may serve several purposes.

One would be storing additional ammunition on an external part of the firearm. It's easy to find, for example, a shell holder that attaches to the frame of the shotgun and provides quicker access to spare ammo than a shell belt would. These configurations can be extended to high-powered rifles, crossbows, and even pistols and SMGs, which may allow storing spare magazines on the gun itself.

Another purpose could be to store miscellaneous items inside holding areas embedded in some parts of the gun. There exist, for example, a multitude of models of pistol grips for AR-15-platform rifles which have a small chamber inside them, allowing the user to store something small inside, like a pair of spare batteries for their electronic attachments, or a stack of bills.

Because batteries powering an item are technically simply stored inside a container, it would then be easy to justify requiring such attachments – which include reflex sights – requiring a power source to operate at capacity. (A reflex sight without a powered laser is just a plastic frame, as far as aiming is concerned. An optical sight with a highlit reticle would perform better than one with an unlit reticle, being more visible.)

The containerized nature of firearms also lends itself to adding the ability to "extend" a firearm via specialized frames. There exist a section of the pistol aftermarket dedicated to producing "carbine conversion kits". These kits allow inserting a pistol inside them, providing the shooter with the additional ergonomics surface: most often a full stock, and often a foregrip, both of which make controlling the pistol that much easier, without modifying the pistol itself.


## Interactive parts

Because it's trivial to interact with items set within containers in general, it would also be trivial to interact with parts of a firearm. This may take over some of the basic functions, like setting the firing mode, or raising / lowering iron sights on modern rifles.

The biggest beneficiaries, however, would be toggleable attachments, such as laser sights or flashlights. Because the system natively allows supplying such attachments with batteries – and power draw of an active eletronic device must be implemented regardless – turning these devices on and off may prolong battery life, as well as be crucial in near-combat situations where glare, noise, and other descriptive details are counterproductive to stealth.


## One in the chamber

Having firearms as containers naturally leads to providing a crucial part of any firearm: the chamber.

The chamber is where the round resides inside the firearm after being loaded and before being fired. If the magazine is ejected and the round has been loaded into the firearm, the round will remain inside the chamber and could then be fired or manually ejected. On reload, the loaded round also remains in the chamber, effectively adding a single round's capacity to any magazine-fed firearm.

The chamber mechanic could be used in conjunction with a new magazine management system (see below): the character could chamber a tracer round, then load a non-tracer ammo magazine in, and gain the benefit of the tracer round's bonus to accuracy while using cheaper ammo for most of the damage they're doing.


## Magazine management

While ordering of contents in a container would be a new mechanic for *Cataclysm*, it could be used to the player's benefit in a variety of ways.

One such way would be interspersing regular ammo with tracer rounds. Tracer rounds help shooters maintain accuracy by providing a clear trail: this allows one to visually estimate where their rounds are going at any given range and adjust their aim, thus gaining a short boost to accuracy, provided the non-tracer rounds in the feed have very similar ballistic characteristics.

Being able to load multiple magazines with predefined patterns of ammunition – e.g. 30-round STANAG magazine ← (4 FMJ + 1 tracer) × 6 stacks – while being prompted on lack of ammo for a complete pattern would be the ideal interface for such a system.


## Failure to feed

In modern semi-automatic firearms, the following round gets automatically loaded into the chamber as part of the response to firing the previous round. This mechanism could lead to magazine feed issues, where the following round could not be properly elevated from the magazine into the chamber. Such a fault could sometimes be blamed onto the feeding mechanism of the firearm, but it's more likely to occur due to the mechanics of the magazine feeding system.

In real life, the way larger magazines are constructed means they're far more likely to produce a feeding issue. It's the reason most armies strongly prefer standard-capacity box magazines (like the in-game 30-round STANAG magazine) and ammo belts to drum magazines and even large-capacity box magazines: reliability is paramount on the battlefield.

Failure to feed can occur on any spring-powered magazine; smaller magazines suffer significantly smaller chance thereof because of the smaller "surface of error". This could be modeled even in approximation, in order to provide additional balance-based choice between different sizes of magazines, beyond mere weight and volume, and whatever influence such magazines may have on ergonomics of the gun.


## Diversity in the world

Because of this modular nature of the firearms, any particular instance of a given model of firearms may spawn differently from its basic (factory, or otherwise in-working-order) configuration.

They may, for example, spawn with components in random condition, provided the spawn point justifies it (e.g. spawn in a bush, on a dead person, or in a trunk of a car). They may also spawn with some components missing entirely. This randomness means that there is no longer a guarantee that the gun you find will be in perfect working order or even usable for its immediate purpose, adding both to balance and to the sense of the living world around the player.

Other options include spawning with aftermarket components (e.g. in someone's home safe), or even in specific component configurations (e.g. M4A1 SOPMOD Accessory Kit in a military weapons cache).