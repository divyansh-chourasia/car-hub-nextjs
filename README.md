# Car Hub

A Next.js page for browsing cars. One running copy is at https://cars-hub-next.netlify.app/.

`app/layout.tsx` wraps every page with the bar and the footer. The logo links home. Sign In does not open a page. The hero in `components/Hero.tsx` reads "Find, book and rent a car -- quickly and easily!" Explore Cars does not scroll or navigate.

The catalogue in `app/page.tsx` fetches in the browser from the cars-by-api-ninjas API. The RapidAPI key is written in `utils/index.ts`. The first request uses an empty make, model, and fuel, the year 2022, and a limit of 10.

The make field searches the list in `constants/index.ts`. Typing filters that list, and a row has to be picked before it is sent. The model field is free text, with the placeholder Tiaguan. Search runs on submit. Both fields empty shows the alert `Please fill in the search bar `. Fuel offers Gas and Electricity. Year offers 2015 through 2023. Changing fuel or year fetches immediately. The blank Year option still sends 2022, because an empty year is replaced with that default.

A card shows the make and model, a daily price, a picture, transmission, drive, and city MPG. `calculateCarRent` builds the price in the browser: 50, plus `0.1` times city MPG, plus `0.05` for each year of age, rounded to a whole number. Transmission `a` is labeled Automatic. Any other value is labeled Mannual. `generateCarImageUrl` asks the Imagin Studio image host for the picture. It sets the `customer` query parameter twice, first to `hrjavascript-mastery`, then to `NEXT_PUBLIC_IMAGIN_API_KEY` or an empty string. This repo has no env file. `next.config.js` allows images from that host.

View More opens a dialog with the main picture, three more angles, and every field on that car.

Show More adds 10 to the limit and fetches again. The button stays while the limit is less than or equal to the number of cars returned. When the response is empty or is not an array, the page says `Opps, no results` and prints the response under that heading.

Footer links for About, Company, and Socials, plus Privacy & Policy and Terms & Condition, all point at `/`.

## Run

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). `npm run build` writes the production build, and `npm start` serves it.

The scaffold text says this app loads Inter with `next/font`. `app/layout.tsx` does not.

This project was bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app). The references from that README:

- [Next.js](https://nextjs.org/)
- [next/font](https://nextjs.org/docs/basic-features/font-optimization)
- [Next.js documentation](https://nextjs.org/docs)
- [Learn Next.js](https://nextjs.org/learn)
- [Next.js on GitHub](https://github.com/vercel/next.js/)
- [Deploy on Vercel](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme)
- [Next.js deployment](https://nextjs.org/docs/deployment)
