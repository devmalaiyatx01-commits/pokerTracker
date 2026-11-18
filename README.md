# Heads Up: AI Poker Tracker

No-limit hold'em against up to 5 AI opponents, each with its own playing style, plus a live HUD
that tracks every opponent's tendencies the way poker-tracking software does.

Play it: https://devmalaiyatx01-commits.github.io/pokerTracker/

## How the opponents decide

Each bot chooses fold, call or raise with a small model. Its inputs are a hand-strength estimate
(the Chen formula before the flop, a Monte Carlo equity simulation after it), pot odds, position,
stack depth and the number of opponents. A weighted sum of these goes through a softmax to give
three probabilities.

The five personalities use the same model with different hand-tuned weights:

| Bot | Style |
|---|---|
| Ice | tight-aggressive |
| Blitz | loose-aggressive |
| The Wall | tight-passive |
| Sponge | loose-passive |
| GTO_9000 | balanced |

## The HUD

The side panel reads each opponent's tendencies from the hands played so far:

* **VPIP**: share of hands where they voluntarily put money in
* **PFR**: share of hands they raised before the flop
* **AF**: aggression factor, bets and raises divided by calls after the flop
* **WTSD**: share of hands they took to showdown

It also writes a plain-English read of each opponent's style.

## Run it

One self-contained HTML file with no build step and no dependencies: open `index.html` in a browser.
