# Heads Up — AI Poker Tracker

A no-limit hold'em game against up to 5 AI opponents, each with a distinct playing style, plus a live strategy-tracking HUD (VPIP, PFR, aggression factor, showdown rate) like real poker-tracking software.

**[Play it live →](#)** *https://devmalaiyatx01-commits.github.io/pokerTracker/*

## How the opponents work

Each bot decides fold/call/raise through a small neural network: a hand-strength estimate (Chen formula preflop, Monte Carlo equity simulation postflop), pot odds, position, stack depth, and opponent count are combined through a weighted sum and squashed into three probabilities. The five personalities — Ice (tight-aggressive), Blitz (loose-aggressive), The Wall (tight-passive), Sponge (loose-passive), and GTO_9000 (balanced) — are the same network architecture with different hand-tuned weights.

## Strategy tracker

The right-hand panel reads back each opponent's tendencies the way tools like PokerTracker or Hold'em Manager do:
- **VPIP** — % of hands voluntarily played
- **PFR** — % of hands raised preflop
- **AF** — aggression factor (bets/raises vs. calls postflop)
- **WTSD** — % of hands taken to showdown
- A plain-English auto-generated read on each opponent's style

## Tech

Single self-contained HTML/CSS/JS file, no build step, no dependencies. Hand evaluation and side-pot math are covered by a small test suite (see commit history / ask for `test.js`).

## Run locally

Just open `index.html` in a browser.
