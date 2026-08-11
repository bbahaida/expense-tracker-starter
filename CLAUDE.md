# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Expense Tracker starter project for a Claude Code course. React SPA with intentional bugs, poor UI, and messy code meant to be improved throughout the course.

## Commands

- `npm run dev` — Start dev server (Vite, localhost:5173)
- `npm run build` — Production build
- `npm run lint` — ESLint
- `npm run preview` — Preview production build

No test framework is configured.

## Tech Stack

- React 19, Vite 7, plain JavaScript (JSX), CSS
- ES modules (`"type": "module"`)
- ESLint 9 flat config with react-hooks and react-refresh plugins

## Architecture

Flat component structure under `src/` (no folders, no barrel files). State is managed via `useState` hooks — no context or external state library.

- `App.jsx` — owns the `transactions` array (the single source of truth) and `addTransaction`. Renders the three children and nothing else.
- `Summary.jsx` — takes `transactions`, computes income/expenses/balance itself, renders the summary cards.
- `TransactionForm.jsx` — owns its own form state (description, amount, type, category), builds the new transaction (including `id` and `date`) and hands it up via the `onAdd` callback. Resets its fields after submit.
- `TransactionList.jsx` — owns its own filter state (`filterType`, `filterCategory`), does the filtering and renders the table.
- `categories.js` — shared `categories` array, imported by the form and the list.

Convention: state lives in the component that uses it; only `transactions` is lifted to `App`. Children receive data down as props and communicate up through callbacks. All styling stays in the global `App.css` (plain class names, no CSS modules).

Key known issues:
- Business logic (totals, filtering) still lives inline in the components rather than in separate helpers
- No delete or edit for transactions
- Filter state resets are not coordinated with the transaction list contents
