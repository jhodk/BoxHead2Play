# Waves
Waves of enemies are defined with various properties for each number.

When the number of devils and zombies left to be spawned is 0, and when the number of alive zombies and devils is 0, then the next wave will be started.

Zombies are spawned at an interval (which is decremented by 1 each ?frame?) until a maximum of 60 alive zombies is reached. This is reduced to 40 if low quality settings are selected in the flash player.

Devils are spawned at a separate interval, which is decremented by 1 if there are any zombies alive, or by 10 if there are not currently any living zombies. This can only happen if the player has killed the total number of zombies in the wave.

The speed of Zombies, and the speed, fire rate and attack speed of Devils are upgraded by constant multipliers as the wave number increases.

A formula determines the number of zombies and devils that will spawn in each wave.

## Zombies
The zombie spawn rate starts at the FPS count, which appears to be 25. For each wave after this, the rate is decremented by 1 until it reaches 1 (so a zombie is spawned each ?frame?).

The zombie count (max zombies alive at one time per wave) starts at 10, and increases by 5 each wave until a maximum of 60 is reached.

The total zombies spawned per wave starts at 10 and increases by 5 each wave thereafter.

The Zombie Speed Up property value is equal to the minimum of 5 or (1 + waveNumber/10). I am not sure how often this speed increase is applied.

## Devils
The Devil spawn rate starts at 10 * FPS (25). Each wave after this value is decremented by 1, and then set to the maximum of FPS (25) or the current value.

The Devil count (max devils alive at once) starts at 0. After wave 1, this value is set to 1. Each wave after this, the count is incremented by 0.3, and set to a minimum of 5 and the calculated value. The count for the wave is set to the floor (integer part) of the calculated value.

The total Devils spawned per wave starts at 0. After wave 1, this value is set to 1. Each wave after this, the total value is incremented by 0.25, and the floor value is taken to be the total number of devils. There is no limit imposed on this number.

The Devil Speed Up property is set the same as the Zombie Speed Up property, i.e. the minimum of 5 or (1 + waveNumber/10).
