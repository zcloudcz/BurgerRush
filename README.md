# Burger Rush

Idle arcade game about growing a burger restaurant: grill patties, assemble burgers and fries, serve guests, expand the place and hire staff. Career with 9 branches.

Offline 3D game for browser and mobile (PWA), 20 languages, no ads or in-app purchases. Depends on: RestaurantCommon.

## Running

```bash
npm run dev      # http://localhost:4173
npm run build    # output in dist/
npm run preview
```

## Mobile apps (Android / iOS)

Native shells via [Capacitor](https://capacitorjs.com): `android/` and `ios/` wrap the same `dist/` build. App ID `cz.zcloud.burgerrush`.

```bash
npm ci
npm run sync      # build web + copy into android/ and ios/
npm run android   # sync and open in Android Studio
```

Icons and splash are generated from `assets/logo.png` (made by `RestaurantCommon/scripts/icons.mjs`) with `npx @capacitor/assets generate`. iOS builds require macOS/Xcode (CI).

Detailed game description: [docs/DETAILS.md](docs/DETAILS.md)

## Repository family

The games share code through relative paths, so all repositories must be cloned **side by side into one folder** (keep the folder names unchanged):

```bash
for r in RestaurantCommon CommonAdvanced BurgerRush PizzaPiazza GasStation RestaurantWorld; do git clone https://github.com/zcloudcz/$r.git; done
cd RestaurantCommon && npm ci
```

| Repo | Contents |
|---|---|
| [RestaurantCommon](https://github.com/zcloudcz/RestaurantCommon) | shared engine, UI, build tooling and tests |
| [CommonAdvanced](https://github.com/zcloudcz/CommonAdvanced) | operations simulation used by Restaurant World |
| [BurgerRush](https://github.com/zcloudcz/BurgerRush) · [PizzaPiazza](https://github.com/zcloudcz/PizzaPiazza) · [GasStation](https://github.com/zcloudcz/GasStation) · [RestaurantWorld](https://github.com/zcloudcz/RestaurantWorld) | games |

Stack: TypeScript, Three.js, Vite, Vitest, Playwright. Requires Node.js 22.12+ and a browser with WebGL 2.

## License

[MIT](LICENSE) © 2026 Martin Zahálka
