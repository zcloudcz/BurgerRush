# Burger Rush

Samostatná 3D hra o budování burger restaurace. Griluj placky, sestavuj burgery, obsluhuj hosty, odemykej posezení i drive-thru a najmi tým, který převezme práci.

## Spuštění

Jednou spusť `npm ci` v sousedním projektu `../RestaurantCommon`. Potom v tomto adresáři:

```powershell
npm run dev
```

Hra běží na `http://localhost:4173`. Na telefonu ve stejné síti použij adresu `Network` vypsanou serverem. WASD/šipky, tažení prstem nebo kliknutí na stanici ovládají postavu; činnosti u stanic jsou automatické.

## Build

```powershell
npm run build
npm run preview
```

Samostatně nasaditelný výsledek je v `dist/`. Instalace PWA a offline cache vyžadují HTTPS nebo localhost. Mobilní aplikace z obchodu není pro hraní potřeba.

`src/definition.ts` vlastní ekonomiku, mapu, recepty a odemykání této hry. `public/` obsahuje originální ikony a vlastní PWA manifest. Sdílený kód a testy jsou v `RestaurantCommon`. Uložený postup má vlastní klíč `restaurant.burger.v1`; záloha v nastavení je přenositelný JSON.

Hra má kariéru s 9 pobočkami. Každá má 18 rozšíření, 4 recepty a tým až 10 zaměstnanců ve 4 rolích. Reklamy a nákupy za skutečné peníze nejsou součástí této verze.

Třetí rozšíření přidává fritézu. Burgery a hranolky lze nést společně, například 2 burgery a 3 porce hranolků při kapacitě 5. Ukazatel tácu uvádí oba počty, prostor sdílejí. Výdej a drive-thru ukládají oba druhy zvlášť; hranolky se vyloží první, aby je zákazník mohl dostat k burgeru za příplatek od 4 $. Bez hranolků prodej burgerů pokračuje. Po plné automatizaci přílohy doplňuje číšník. Starší uložené pozice se převedou automaticky.

Žlutý panel „Volné peníze“ ukazuje aktuální neinvestovanou hotovost. Částka již vložená do rozšíření se zobrazuje zvlášť v jeho financování.


## Druhá kapitola: rozšíření 13–18

Na dokončený původní podnik navazuje šest dalších nákupů bez resetu uložené hry:

| Úroveň | Rozšíření | Efekt | Cena |
| --- | --- | --- | --- |
| 13 | Východní jídelna | nová plocha a 4 stoly; +5 míst na tácu | 3 500 |
| 14 | Zahradní terasa | průchozí terasa a 4 stoly; tým +35 % | 4 500 |
| 15 | Severní kuchyň | kuchyňské křídlo s další pracovní stanicí; čtvrtý recept | 5 500 |
| 16 | Expresní křídlo | další výdej s vlastní frontou; výroba +50 % | 6 500 |
| 17 | Prémiový salonek | dva další stoly a vybavení; tržby +20 % | 8 000 |
| 18 | Vstupní zahrada | průchozí zahrada, osvětlení a zlaté ocenění; offline +50 % | 10 000 |

Nový recept je BBQ burger / lanýžová pizza podle hry. Druhá kapitola je ověřená automatickou simulací nákupů z běžných tržeb bez dodané hotovosti.

Každé rozšíření 1–18 má fyzický projev v mapě. Původní čtyři stoly lze rozšířit až na 14. Nová kuchyňská stanice i expresní výdej fungují ručně i s personálem. Staré pozice doplní nové zamčené části automaticky; již zakoupené úrovně je otevřou bez opakovaného placení.

## Restaurační impérium

Po dokončení úrovně 18 otevři mapu přes „Odejít z restaurace“ na počítači, „Impérium“ na mobilu nebo tlačítko v oznámení dokončení. Postupně vybuduješ 3 městské, 3 celostátní a 3 světové pobočky. Další pobočka vyžaduje dokončenou předchozí a jednorázovou cenu otevření: 2 500, 5 000, 10 000, 18 000, 28 000, 42 000, 60 000 a 85 000 $.

Nová pobočka začíná na úrovni 0, bez zakoupených vylepšení a personálu. Zůstatek společné pokladny po zaplacení otevření si ponecháš. Do vlastněných poboček se můžeš zdarma vracet; každá si uchovává vlastní vybavení, zásoby, tým a postup. Neaktivní automatizované pobočky přispívají odhadovaným pasivním příjmem po odečtení mezd. Burger a Pizza mají oddělená impéria i pokladny. Záloha obsahuje celou síť a stará pozice se převede na první pobočku.

Tým se ze 4 zaměstnanců na úrovni 11 rozroste na 10 na úrovni 18. Každé rozšíření 13–18 přidá dalšího člověka. Plný tým stojí 23 $ za minutu; sazbu a případný dluh najdeš ve „Vylepšení & tým“. Mzdy se platí automaticky. Při prázdné pokladně tým pokračuje na dluh a dlužné mzdy se odečtou z budoucích příjmů.

Technické podrobnosti: [model impéria a ukládání](https://github.com/zcloudcz/RestaurantCommon/blob/main/docs/EMPIRE.md).
