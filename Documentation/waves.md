# Waves
Waves of enemies are defined with various properties for each number.

When the number of devils and zombies left to be spawned is 0, and when the number of alive zombies and devils is 0, then the next wave will be started.

Zombies are spawned at an interval (which is decremented by 1 each ?frame?) until a maximum of 60 alive zombies is reached. This is reduced to 40 if low quality settings are selected in the flash player.

Devils are spawned at a separate interval, which is decremented by 1 if there are any zombies alive, or by 10 if there are not currently any living zombies. This can only happen if the player has killed the total number of zombies in the wave.

The speed of Zombies, and the speed, fire rate and attack speed of Devils are upgraded by constant multipliers as the wave number increases.

A formula determines the number of zombies and devils that will spawn in each wave.

The zombie spawn rate starts at the FPS count, which appears to be 25. For each wave after this, the rate is decremented by 1 until it reaches 1 (so a zombie is spawned each ?frame?).

The zombie count (max zombies alive at one time per wave) starts at 10, and increases by 5 each wave until a maximum of 60 is reached.

The total zombies spawned per wave starts at 10 and increases by 5 each wave thereafter.

The Zombie Speed Up property value is equal to the minimum of 5 or (1 + waveNumber/10). I am not sure how often this speed increase is applied.
