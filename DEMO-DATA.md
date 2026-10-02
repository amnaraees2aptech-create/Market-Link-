# Demo Data — MarketLink

## How to load it

```bash
php artisan migrate:fresh --seed
```

This wipes and rebuilds the DB, then runs `DatabaseSeeder` → `DemoSeeder`. Safe to
re-run any time. If you only want to re-seed without touching migrations:

```bash
php artisan db:seed
```

Orders/reviews/favorites are only created once (the seeder skips them if any
orders already exist), so re-running `db:seed` alone won't duplicate them —
use `migrate:fresh --seed` if you want a totally clean slate.

## Login credentials

Every account uses the same password: **`Test@123`**

| Role     | Emails                                    |
| -------- | ----------------------------------------- |
| Admin    | `admin@gmail.com`                         |
| Farmer   | `farmer1@gmail.com` … `farmer8@gmail.com` |
| Customer | `user1@gmail.com` … `user10@gmail.com`    |

**Farmer stalls across 9 US Cities:**
| Email | Stall | Contact | Category | City / State | Markets |
|---|---|---|---|---|---|
| `farmer1@gmail.com` | Green Valley Farms | John Miller | Vegetables | Austin, TX | Downtown Farmers Market, Green City Market Chicago |
| `farmer2@gmail.com` | Sunny Orchard | Michael Davis | Fruits | Los Angeles, CA | Westside Weekend Market, Suncoast Artisans Market |
| `farmer3@gmail.com` | Pure Dairy Co. | Sarah Jenkins | Dairy | Portland, OR | Portland Saturday Market, Central Park Green Bazaar |
| `farmer4@gmail.com` | Homestead Bakery | Emily Wilson | Baked Goods | Seattle, WA | Pike Place Community Market, Downtown Farmers Market |
| `farmer5@gmail.com` | Lone Star Meat & Poultry | Robert Taylor | Meat | San Antonio, TX | Hill Country Harvest Hub, Green City Market Chicago |
| `farmer6@gmail.com` | Golden Hive Honey | Amanda Martinez | Other/Honey | Miami, FL | Suncoast Artisans Market, Bay Area Farmers Hub |
| `farmer7@gmail.com` | Pine State Greens | David Brown | Vegetables | New York, NY | Central Park Green Bazaar, Portland Saturday Market |
| `farmer8@gmail.com` | Orchard Fresh | Jessica White | Fruits | San Francisco, CA | Bay Area Farmers Hub, Pike Place Community Market |

**Customer accounts:**
| Email | Name | City / State | Address |
|---|---|---|---|
| `user1@gmail.com` | Sarah Johnson | Austin, TX | 124 Maple St, Austin, TX 78704 |
| `user2@gmail.com` | Alex Rivera | New York, NY | 850 Broadway, Apt 4B, New York, NY 10003 |
| `user3@gmail.com` | Hannah Smith | Miami, FL | 340 Ocean Dr, Miami, FL 33139 |
| `user4@gmail.com` | James Wilson | Los Angeles, CA | 512 Sunset Blvd, Los Angeles, CA 90028 |
| `user5@gmail.com` | Maria Garcia | San Antonio, TX | 720 Oak Ln, San Antonio, TX 78209 |
| `user6@gmail.com` | Daniel Lee | San Francisco, CA | 150 Market St, San Francisco, CA 94105 |
| `user7@gmail.com` | Rachel Green | Portland, OR | 450 NW 10th Ave, Portland, OR 97209 |
| `user8@gmail.com` | Chris Taylor | Seattle, WA | 1200 4th Ave, Seattle, WA 98101 |
| `user9@gmail.com` | Emily Davis | Chicago, IL | 600 N Michigan Ave, Chicago, IL 60611 |
| `user10@gmail.com` | Tyler Moore | Sacramento, CA | 800 J St, Sacramento, CA 95814 |

## What gets created

- **1 Admin, 8 Farmers, 10 Customers**
- **9 Markets across 9 distinct US cities** (Austin, Los Angeles, New York, Miami, San Antonio, San Francisco, Portland, Seattle, Chicago), each with real street addresses, operating hours, coordinates, and descriptions
- **58 Products across 6 categories** with USD pricing ($1.99 – $18.99) and US standard units (lb, oz, bunch, dozen, pack, pint, jar, gallon)
- **30 Orders** spread across all order statuses (Pending, Confirmed, Ready for Pickup, Completed, Cancelled)
- **8 Reviews** on completed orders with ratings and farmer responses
- **20 Favorites** linking customers to favorite products, stalls, and markets

## 9 Markets across the USA

| #   | Market                      | City          | State | Operating Days           | Operating Hours    | Address                                   |
| --- | --------------------------- | ------------- | ----- | ------------------------ | ------------------ | ----------------------------------------- |
| 1   | Downtown Farmers Market     | Austin        | TX    | Saturday, Sunday         | 8:00 AM – 2:00 PM  | 1100 Congress Ave, Austin, TX 78701       |
| 2   | Westside Weekend Market     | Los Angeles   | CA    | Saturday, Sunday         | 9:00 AM – 1:00 PM  | 1200 Wilshire Blvd, Los Angeles, CA 90025 |
| 3   | Central Park Green Bazaar   | New York      | NY    | Friday, Saturday, Sunday | 7:00 AM – 12:00 PM | 5th Ave & 72nd St, New York, NY 10021     |
| 4   | Suncoast Artisans Market    | Miami         | FL    | Saturday, Sunday         | 8:00 AM – 1:00 PM  | 300 Biscayne Blvd, Miami, FL 33132        |
| 5   | Hill Country Harvest Hub    | San Antonio   | TX    | Sunday                   | 8:00 AM – 3:00 PM  | 300 Alamo Plaza, San Antonio, TX 78205    |
| 6   | Bay Area Farmers Hub        | San Francisco | CA    | Friday, Saturday         | 9:00 AM – 2:00 PM  | 1 Ferry Building, San Francisco, CA 94111 |
| 7   | Portland Saturday Market    | Portland      | OR    | Saturday, Sunday         | 9:00 AM – 5:00 PM  | 100 SW Naito Pkwy, Portland, OR 97204     |
| 8   | Pike Place Community Market | Seattle       | WA    | Saturday, Sunday         | 9:00 AM – 3:00 PM  | 85 Pike St, Seattle, WA 98101             |
| 9   | Green City Market Chicago   | Chicago       | IL    | Saturday, Sunday         | 7:00 AM – 1:00 PM  | 1817 N Clark St, Chicago, IL 60614        |

## Adding real photos (optional)

**None of this is required** — every image field is optional, and the app
renders an automatic color-tile placeholder from the record's name if no
file is found. Drop photos in only if/when you want the real thing.

**Step 1 — link storage (one-time):**

```bash
php artisan storage:link
```

This creates `public/storage` → `storage/app/public`, which is where all
three folders below live.

**Step 2 — create these three folders** (if they don't already exist):

```
storage/app/public/avatars/
storage/app/public/markets/
storage/app/public/products/
```

**Step 3 — rename your photos to match exactly** (case-sensitive, `.jpg`)
and drop them in the matching folder. Nothing else needs to change — the
seeder already points every record at these exact paths.

### Farmer avatars → `storage/app/public/avatars/`

```
farmer1.jpg   Green Valley Farms       (John Miller — Austin, TX)
farmer2.jpg   Sunny Orchard            (Michael Davis — Los Angeles, CA)
farmer3.jpg   Pure Dairy Co.           (Sarah Jenkins — Portland, OR)
farmer4.jpg   Homestead Bakery         (Emily Wilson — Seattle, WA)
farmer5.jpg   Lone Star Meat & Poultry (Robert Taylor — San Antonio, TX)
farmer6.jpg   Golden Hive Honey        (Amanda Martinez — Miami, FL)
farmer7.jpg   Pine State Greens        (David Brown — New York, NY)
farmer8.jpg   Orchard Fresh            (Jessica White — San Francisco, CA)
```

### Market cover photos → `storage/app/public/markets/`

```
downtown-farmers-market.jpg      Downtown Farmers Market (Austin, TX)

westside-weekend-market.jpg      Westside
Weekend Market (Los Angeles, CA)

central-park-green-bazaar.jpg    Central Park Green Bazaar (New York, NY)

suncoast-artisans-market.jpg     Suncoast Artisans Market (Miami, FL)

hill-country-harvest-hub.jpg     Hill Country Harvest Hub (San Antonio, TX)

bay-area-farmers-hub.jpg         Bay Area Farmers Hub (San Francisco, CA)

portland-saturday-market.jpg     Portland Saturday Market (Portland, OR)

pike-place-community-market.jpg  Pike Place Community Market (Seattle, WA)

green-city-market-chicago.jpg    Green City Market Chicago (Chicago, IL)


### Product photos → `storage/app/public/products/` (42 files, shared across
stalls that sell the same item — e.g. both `farmer1` and `farmer7` sell
tomatoes and both use `tomatoes.jpg`)
```

tomatoes.jpg Fresh Red Tomatoes
onions.jpg Organic Onions
potatoes.jpg Farm Potatoes
carrots.jpg Fresh Carrots
spinach.jpg Fresh Spinach
green-chillies.jpg Green Peppers
cucumbers.jpg Cucumbers
bell-peppers.jpg Bell Peppers

apples.jpg Sweet Apples
bananas.jpg Ripe Bananas
mangoes.jpg Seasonal Peaches
oranges.jpg Juicy Oranges
grapes.jpg Fresh Grapes
pomegranates.jpg Fresh Strawberries
guavas.jpg Fresh Berries
watermelon.jpg Watermelon

milk.jpg Farm Fresh Milk
yogurt.jpg Homemade Yogurt
butter.jpg Artisanal Butter
ghee.jpg Farmhouse Cheese
paneer.jpg Fresh Cottage Cheese
cream.jpg Fresh Heavy Cream
eggs.jpg Free Range Eggs

wheat-bread.jpg Whole Wheat Bread
sourdough-loaf.jpg Sourdough Loaf
croissants.jpg Butter Croissants
banana-bread.jpg Banana Bread
chocolate-cookies.jpg Chocolate Chip Cookies
cinnamon-rolls.jpg Cinnamon Rolls
multigrain-buns.jpg Multigrain Buns

chicken-whole.jpg Whole Chicken
chicken-breast.jpg Chicken Breast
mutton-boneless.jpg Boneless Beef Ribeye
beef-mince.jpg Lean Ground Beef
chicken-drumsticks.jpg Chicken Drumsticks
mutton-chops.jpg Pork Chops

raw-honey.jpg Raw Honey
organic-honey.jpg Organic Wildflower Honey
honeycomb.jpg Honeycomb
mustard-oil.jpg Cold-Pressed Sunflower Oil
olive-oil.jpg Extra Virgin Olive Oil
dried-dates.jpg Organic Dried Dates

```

> **Note on product photo names:** Product image filenames map directly to standard items
> in the product catalog. The display title, USD price, and description are stored dynamically
> in the database.

That's it — no database edits, no controller changes. The `image`/`avatar`
columns already point at these exact relative paths; dropping a correctly
named file into the folder is enough for it to appear on the site immediately.

