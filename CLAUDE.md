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

Single-component monolith in `src/App.jsx` — all state, logic, and rendering live in one component. State is managed via `useState` hooks (no context/external state library).

Key known issues:
- Transaction amounts stored as strings instead of numbers (causes calculation bugs)
- No component decomposition
- Business logic mixed with rendering
