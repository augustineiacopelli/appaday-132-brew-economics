# 132 - Brew Economics

**Live:** https://augustineiacopelli.github.io/appaday-132-brew-economics/

**Category:** Data Viz | **Shipped:** 2026-09-16 | **Part of** [AppADay](https://augustineiacopelli.github.io/appaday/)

Price a homebrew batch honestly. List the ingredients, set the volume and the loss you expect to trub and transfer, and it derives drinkable pints, bottles, and six packs, then stacks your cost per six pack against the shelf and projects a year of savings. Consumables and equipment fold in on request.

## What it does

The ingredients panel takes as many named line items as the batch needs and totals them live. The yield panel converts batch volume in gallons or pints into drinkable pints after a loss percentage, then into 12 ounce bottles and six packs. The benchmark panel sets the shelf price you are comparing against, with one tap presets at nine, twelve, and sixteen dollars.

From there the comparison panel draws two bars on a shared track, homebrew against store, labeled with cost per six pack and annotated with cost per pint underneath. The savings panel reports the dollar and percentage gap for a single batch and multiplies it by the batches you brew in a year.

An expanded costs section folds in the things brewers forget: caps, sanitizer, and priming sugar as consumables, propane and water and power as utilities, and equipment amortized over the number of batches you expect it to last. With an equipment cost entered, it also reports how many batches it takes to break even.

The app opens seeded with a real five gallon batch so the numbers tell a story before anything is typed.

## How it is built

One self-contained `index.html` file. Vanilla HTML, CSS, and JavaScript with no build step, no framework, and no external requests apart from Google Fonts. No AI and no API.

Every input runs through a single `recalculate()` function so there is exactly one calculation path, reached by a delegated listener on the form container. Numbers are clamped to non-negative finite values on read, and every division that could reach zero returns a placeholder instead of `NaN` or `Infinity`, which covers a zero volume batch, total loss, a zero benchmark, and a break even with no savings to divide into.

State persists to `localStorage` under `appaday-132-brew-economics`, with both the write and the read wrapped in try and catch and the stored ingredient list validated as an array before it is adopted. Anything malformed falls back to a single empty row.

The layout is single column from 375 pixels, with one breakpoint near 720 pixels that sets the ingredients and yield panels side by side. Every control clears a 44 pixel tap target.

## The rules

Part of AppADay, a daily discipline project: one complete, functional, mobile-friendly, visually polished web app designed and shipped every single day. Scope is cut to fit the time; quality never is.

---

*Ship something every day. It compounds.*
