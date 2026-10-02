# Burger Rush

A standalone 3D game about building a burger restaurant. Grill patties, assemble burgers, serve guests, unlock dine-in seating and a drive-thru, and hire a team to take over the work.

## Running

Run `npm ci` once in the sibling project `../RestaurantCommon`. Then, in this directory:

```powershell
npm run dev
```

The game runs at `http://localhost:4173`. On a phone on the same network, use the `Network` address printed by the server. WASD/arrow keys, finger drag, or a click on a station control the character; actions at stations are automatic.

## Build

```powershell
npm run build
npm run preview
```

The standalone deployable output is in `dist/`. PWA installation and the offline cache require HTTPS or localhost. A mobile app from a store is not needed to play.

`src/definition.ts` owns this game's economy, map, recipes, and unlocks. `public/` contains original icons and a dedicated PWA manifest. Shared code and tests are in `RestaurantCommon`. Saved progress uses its own key `restaurant.burger.v1`; the backup in the settings is portable JSON.

The game has a career with 9 branches. Each has 18 expansions, 4 recipes, and a team of up to 10 employees in 4 roles. Ads and real-money purchases are not part of this version.

The third expansion adds a deep fryer. Burgers and fries can be carried together, for example 2 burgers and 3 portions of fries with a capacity of 5. The tray indicator shows both counts; they share the space. The pickup counter and the drive-thru store both kinds separately; fries are unloaded first so the customer can get them with the burger for a surcharge from $4. Without fries, burger sales continue. Once the side is fully automated, the waiter restocks it. Older saved games are converted automatically.

The yellow "Free money" panel (Volné peníze) shows the current uninvested cash. The amount already put into an expansion is shown separately in its funding.


## Second chapter: expansions 13–18

Six more purchases follow the completed original restaurant, without resetting the saved game:

| Level | Expansion | Effect | Price |
| --- | --- | --- | --- |
| 13 | East dining room | new area and 4 tables; +5 tray slots | 3 500 |
| 14 | Garden terrace | walk-through terrace and 4 tables; team +35 % | 4 500 |
| 15 | North kitchen | kitchen wing with another work station; fourth recipe | 5 500 |
| 16 | Express wing | another pickup counter with its own queue; production +50 % | 6 500 |
| 17 | Premium lounge | two more tables and furnishings; revenue +20 % | 8 000 |
| 18 | Entrance garden | walk-through garden, lighting, and a golden award; offline +50 % | 10 000 |

The new recipe is BBQ burger / truffle pizza, depending on the game. The second chapter was verified by an automatic simulation of purchases made from regular revenue, with no cash injected.

Every expansion 1–18 has a physical presence on the map. The original four tables can be expanded up to 14. The new kitchen station and the express pickup counter work both manually and with staff. Old saved games get the new locked parts added automatically; levels already purchased open them without paying again.

## Restaurant empire

After completing level 18, open the map via "Leave the restaurant" (Odejít z restaurace) on desktop, "Empire" (Impérium) on mobile, or the button in the completion notice. You gradually build 3 city, 3 national, and 3 worldwide branches. The next branch requires the previous one to be completed and a one-time opening fee: $2 500, 5 000, 10 000, 18 000, 28 000, 42 000, 60 000, and 85 000.

A new branch starts at level 0, with no purchased upgrades and no staff. You keep the shared treasury balance after paying the opening fee. You can return to owned branches for free; each one keeps its own equipment, stock, team, and progress. Inactive automated branches contribute an estimated passive income after wages are deducted. Burger and Pizza have separate empires and treasuries. The backup contains the whole network, and an old saved game is converted into the first branch.

The team grows from 4 employees at level 11 to 10 at level 18. Each expansion 13–18 adds another person. A full team costs $23 per minute; you can find the rate and any debt in "Upgrades & team" (Vylepšení & tým). Wages are paid automatically. When the treasury is empty, the team keeps working on credit and the owed wages are deducted from future income.

Technical details: [empire model and saving](https://github.com/zcloudcz/RestaurantCommon/blob/main/docs/EMPIRE.md).
