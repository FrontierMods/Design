# Item States

Currently, separate states of items – like on vs. off flashlight – have to be defined and treated as separate items, with the `transform` action used to surreptitiously switch one item for another. This leads to bloat, and creates a larger surface area for errors: for example, making changes to the item's dimensions in one case but not the rest of them.

Using *states* allows avoiding the these problems by managing their properties within the frame of the same item. A state would be part of the item definition, under the `state_data` key.

Each state defines a set of properties that differentiate it from the item's default state, which is defined in the item object's root.


## Exclusive and Complementary States

States could be structurally defined as exclusive or complementary in `state_data`.

Only one state from each exclusive group can be on at any given time. Switching to a different state in an exclusive group turns the previous state off automatically. Examples include flashlights with multiple brightness settings, firearms with fire mode switches, and mechanical tools which may operate from different configurations.

Complementary states may operate independently of other state groups. Smartphones may act as music players and flashlights at the same time, and control panels for security systems may be used to toggle any number of switches on the panel at any given moment.

`state_data` of an item must be able to define both kinds of states, and switching between the states cannot be a one-at-a-time action – where players are required to activate the item multiple times to toggle multiple states, the repetitiveness of which quickly becomes unpleasant – unless there's only one other state to switch to.


### Example `state_data` Definition

```
  {
    "name": "SUPERSHOCK self-defence flashlight",
    "//": "...the rest of the item definition...",
    "state_data": [
      {
        "category_name": "Flashlight",
        "states": [
          {
            "name": "off",
            "default": true,
            
            "luminance": 0,
            "power_draw": 0
          },
          {
            "name": "on, regular",
            "description_suffix": "The flashlight is on.",
          
            "luminance": 400,
            "power_draw": "10.7 Wh",
            "power_min": "5 J"
          },
          {
            "name": "on, bright",
            "description_suffix": "The flashlight is on, operating at increased brightness.",
          
            "luminance": 1200,
            "power_draw": "32.1 Wh",
            "power_min": "15 J"
          }
        ]
      },
      {
        "category_name": "Shocker",
        "states": [
          {
            "name": "active",
            "description_suffix": "The flashlight's self-defense module is currently on. Any attack made using the flashlight will inflict electrical damage on the target, potentially stunning them. Each attack drains a bit of power from the embedded battery.",
            "extend": {
              "damage": {
                "damage_type": "electric",
                "amount": 45,
                "range": 1
              },
              
              "power_draw_per_attack": "10 W",
              "power_min": "50 J"
            }
          }
        ]
      }
    ]
  }
```

*Note*: values are given for the purposes of demonstration and are not necessarily correct.

*Note*: in the example above, `"luminance"` is the scaling parameter for the perceived power of light, in lumens. `"power_draw_per_attack"` is an *ad hoc* parameter meant to indicate power draw similar to `"ups_per_charge"`, but in a more generic power-supply framework.

`state_data` is given in the form of array, itself containing any number of objects. Each object represents a set of complementary states. Each object must have at least the `"name"` and `"states"` keys, and may have any number of other permitted keys.

One example of such keys is `"description_suffix"`, which adds a separate (double returns) line at the end of the item's description in order to clarify the item's current state. Multiple "suffixes" from complementary states combine, each starting on a separate line. The order of the suffixed lines is determined by the order of the state groups in the item's JSON definition.

In this example, the item is a flashlight with a shocker self-defense function. According to `state_data`, it has two complementary states: the "Flashlight" function and the "Shocker" function.


#### Exclusive States

"Flashlight" has several states, with a defined "off" state because there are multiple states available.

The "off" state may not be required, with the game potentially assuming there is one where no states-based changes apply unless stated otherwise. However, this may cause issues defining objects where there is no real "off" state.

A good example of this are tools which may be extended or compressed, with no default state obvious to the game. In this case, the item itself is an abstract, where some of its key qualities – such as tool qualities, volume, and length – would be defined in each given state.

If an exclusive state requires power to function and there isn't enough power for that in the item, it would revert to the default state (see below).


#### Complementary States

"Shocker" has one state, which implies that the category is togglable between positions "on" and "off", where "on" is the explicitly defined state.

"Shocker" and "Flashlight" state groups may be active at the same time, as long as both satisfy their own requirements. In this case, the item would be emitting light *and* producing electical damage on each attack.


#### Conditional States

It must be possible to define states which would be activated only if conditions are met.

For example, radiation badges would have states of "green" and "red", the latter activating if the square the badge is in emits radiation.

Another example would be a tracking device, which lights a different color – green, yellow, or red – depending on the distance between it and the target. This may be useful in tracking bounties as a bounty hunter, or tracking a horde by attaching a tracking device onto one of the zombies surreptitiously.

The changes in conditional states may be reflected via log entries: "Your radiation badge turns red", or "The tracking device light is now yellow".


#### Default States

States may be marked as `"default"`, with the value being either `true` or `false`. There may be no more than one default state in an exclusive group.

Items with states spawn with each complementary state set to its default value.

For single-state entries, the default state is assumed to be "off". Adding `"default": true` to the single state indicates that the item must be "on" be default, whatever "on" means in each specific case.

States, the conditions for which are no longer met, automatically revert to the default sibling state instead, notifying the player about the change.


#### State Inheritance

`state_data` may be inherited from item to item. This would enable creating classes of items with similar functionality, such as different types of flashlights.

`state_data` must be affected by the `"extend"` property where such is indicated. This would allow using inheritance to create distinct individual states: for example, adding a "disorienting" mode which causes confusion in intelligent enemies.


### Naming via States

Items with non-default states active gain parentheses-marked suffixes. Suffixes follow one another in the same set of brackets, their order defined by the order of the state groups in the item's JSON definition: e.g. `flashlight (on, regular, shocker on)`.

Options to directly change the name of the item itself should be considered for more abstract entities which may alter their very nature, such as artifacts or magical / sci-fi items.


## Examples of Use

**Apparel**. Manipulating scarves between "tight", "loose" (default), and "hanging" states, which affects the degree to which they help you retain heat. Changing the degree to which the clothes you wear are open, allowing you to manually control heat exchange between you and the environment. For advanced apparel and armor, changing operating modes:

**Equipment**. Bags, backpacks etc. may be folded to save room or unfolded to make them useful as containers. Cords may be tied loosely, making them useful in crafting and as improvised slings, or tightly to save space or even as improvised armor. Glasses may be moved away from your eyes, but not off your head, to enable a different visual processing – for example, moving shades enables one to see clearer.

**Devices**. Switching between available FM stations on a radio to find the right automated music for the atmosphere. Changing intensity of an emitter in order to attract a larger group of enemies to the source, thus distracting them without putting yourself at risk. Switching the signal on your radio device to control a different target, enabling manipulation of multiple personal mobile devices, such as drones. Explosive charges may be set to a timer or turned off.

**Environment**. Room heaters may be controlled as to their temperature output, in situations where you have to manage your available electrical power against your needs. Ovens may be turned on for preheating towards baking. Power stations and UPS may be disabled, to prevent them from sharing charge with relevant devices automatically upon contact.