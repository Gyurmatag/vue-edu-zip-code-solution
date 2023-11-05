# Zip Code challenge

A feladat célja azt megoldani, hogyha a felhasználó a ZipCode input mezőbe karaktereket ír,
vagy beilleszt, akkor az alkalmazásnak be kell hívnia egy végpontra, amely visszaadja az irányítószámhoz
tartozó várost / települést és ezt az értéket a City input mezőbe betölti. A végpont több találatot is visszaadhat, az
egyszerűség kedvéért elég csak az első találatot visszaadni.
Pl.: 3300 -> Eger

A következő végpontot célszerű használni:

```GET https://hur.webmania.cc/zips/3300.json```

Bővebb információ itt: https://hur.webmania.cc/

A következő kis package hasznos lesz a HTTP kérések indításában:
- [Axios](https://axios-http.com/docs/intro)

A projekt elő van készítve.
Először ```npm install``` majd ```npm run dev``` és már megy is!

