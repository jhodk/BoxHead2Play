# Weapons

Weapons can be unlocked and upgraded when a kill combo level is reached for the first time.

Upgrades are applied in a formulaic way by some calculation on the original weapon stats.

| Upgrade Type | Effect | Comment |
| --- | --- | --- |
| Fast Fire | Auto is set to true (weapon continues to fire when key is pressed) ||
| Rapid Fire | Auto is set to true.<br />Rate of fire is set to the maximum of either (originalFireRate/4) or 2. ||
| Fatal Damage | Damage is set to original * 10. | This is not used in player weapon upgrades. | 
| Quad Damage | Damage is set to original * 4. ||
| Double Damage | Damage is set to original * 2. ||
| Bigger Bang | BiggerBang is set to 2. ||
| Big Bang | BiggerBang is set to 1. ||
| Cluster Explode | ClusterExplode is set to 1. ||
| Wider Shot | WideShot is set to 2. | Affects spread and number of bullets. See shotgun.md for more details. |
| Wide Shot | WideShot is set to 1. | See above comment. |
| Infinite Ammo | TotalAmmo is set to infinite. <br />CurrentAmmo is set to infinite. ||
| Quad Ammo | TotalAmmo is set to original * 4.<br />CurrentAmmo is set to original * 4. | Not sure if any weapons have a different initial current and max ammo value? |
| Double Ammo | TotalAmmo is set to original * 2.<br />CurrentAmmo is set to original * 2. | See above comment. |
| Homing Missiles | HomingMissiles set to true. | Not sure where this is used |
| Infinite Range | Range is set to 100. | I dislike having weapon ranges, and would instead prefer an 'effective range' beyond which damage is reduced, but I appreciate this affects the game balance for the shotgun in particular. |
| Long Shot | Range is set to original * 1.5 ||
