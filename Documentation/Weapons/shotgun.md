# Shotgun

- NameID: shotgun
- Name: Shotgun
- ShortName: Shotgun
- FireRate: 12
- TotalAmmo: 20
- Damage: 51
- Auto: false
- Range: 7
- WideShot: 0. Becomes 1 with Wide Shot upgrade, 2 with Wider Shot upgrade

There is an initial shot in the target direction.

Then two more shots are added in the target direction of fire, ± 1.25 * (WideShot + 1) degrees.

| Shotgun Type | WideShot value | Spread in degrees of 2nd and 3rd shots |
| --- | --- | --- |
| Default | 0 | 2.5 degrees (±1.25) |
| Wide Shot | 1 | 5 degrees (±2.5) |
| Wider Shot | 2 | 7.5 degrees (±3.75) |

If the shotgun has been upgraded above the default level, then another two shots are added with a doubled spread. A "delay" argument is also set to true for this volley of two bullets.

| Shotgun Type | WideShot value | Spread in degrees of 4th and 5th shots |
| --- | --- | --- |
| Default | 0 | N/A |
| Wide Shot | 1 | 10 degrees (±5) |
| Wider Shot | 2 | 15 degrees (±7.5) |
