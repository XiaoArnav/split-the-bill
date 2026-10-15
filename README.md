# Baant

Split the bill. Keep every paisa.

Baant is a free page for a restaurant bill in rupees. The name means to divide or share. You enter the amount, pick a tip, and say how many people are paying. The shares add up to the total, including the leftover paisa.

![Baant showing a ₹10.10 bill, a 10% tip, and a three-way split](screenshot.png)

There is no account, no install, and no server. Open the file and it runs in the browser.

## Features

- Tip choices are none, 5%, 10%, and 15%. The page opens on 10%.
- The bill is stored as whole paise before any math, so a split does not drop a paisa.
- When the total does not divide evenly, one or more people pay one paisa more. The note under the total says who.
- Dark mode toggles from the button beside the name.
- An amount needs at most two decimal places. `10.999` is rejected.
- The number of people is a whole number from 1 to 99.

## Run it

```bash
git clone https://github.com/XiaoArnav/split-the-bill.git
cd split-the-bill
open index.html
```

On Linux, use `xdg-open index.html`. On Windows, double-click `index.html`.

The page starts with ₹10.10, a 10% tip, and 3 people.

| | |
| --- | --- |
| Tip | ₹1.01 |
| Total | ₹11.11 |
| Each pays | ₹3.70 |
| Adjustment | 1 person pays ₹3.71 |

`3.70 + 3.70 + 3.71 = 11.11`.

With no tip, the same bill is ₹3.36, ₹3.37, and ₹3.37, which still totals ₹10.10.

## How the math works

Rupees are converted to paise first. `10.10` is `1010` paise. A tip is `round(paise × percent / 100)`, so 10% of 1010 is 101 paise, or ₹1.01. The total is 1111 paise.

Each share is `floor(total / people)`. The remainder is handed out one paisa at a time. For 1111 paise and 3 people, the base share is 370 paise and one person pays 371.

## Project files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: markup, styles, and script |
| `screenshot.png` | The image at the top of this page |
| `LICENSE` | MIT license |

## Contributing

Open an issue or a pull request. The app is one file, so a behavior change belongs in `index.html`. Documentation changes belong in this README.

## License

[MIT](LICENSE). Free to use, copy, and change.

## Author

[Arnav Patel](https://github.com/XiaoArnav)
