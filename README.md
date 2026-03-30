# kajastus-opastin

kajastus-opastin is a monorepo for a map-based collection system.

It contains two main applications:

- **Kajastus** — the frontend client for viewing and interacting with collection data on an interactive map
- **Opastin** — the backend domain system that serves collection data and later supports place lookup and resolution workflows

The project is built through small vertical slices. The first slice focuses on collection graph hydration and map rendering.

## What this repository is supposed to be

This repository is supposed to be the implementation home of the whole system.

Its purpose is to contain:

- the frontend application
- the backend application
- shared project structure
- evolving contracts between frontend and backend
- implementation slices that gradually grow the system

At the beginning, the repository is intentionally small. The goal is not to solve everything at once, but to establish a working foundation that can be extended safely.

## First slice

The first slice proves the basic hydration flow of the system:

- Opastin serves one collection graph
- Kajastus fetches that graph
- Kajastus stores the hydrated graph in frontend runtime state
- Kajastus renders the returned places on a real map
- Kajastus shows the collection structure in a simple sidebar

This slice is intentionally limited. It does not yet include editing, replay, search, provider-backed resolution, or persistence.

## System shape

The system is centered around a simple structure:

- **Collection** — a grouped set of places and related content
- **Memory** — a logical grouping within a collection
- **Item** — an individual place with coordinates and optional descriptive content

Over time:

- **Kajastus** becomes the user-facing map application
- **Opastin** becomes the backend for collection hydration and place resolution workflows

## Repository principles

This repository follows a few simple principles:

- build in small vertical slices
- prefer working end-to-end flows early
- keep contracts practical and easy to evolve
- keep frontend ownership clear after hydration
- avoid premature abstraction

## Early scope

Included early:

- one monorepo
- one frontend app
- one backend app
- one collection graph endpoint
- one frontend page with a real map
- one simple sidebar view of hydrated data

Not included in the early slices:

- production-grade persistence
- advanced search
- replay editing
- provider-backed place resolution

## Out of scope for now

- authentication
- multi-user workflows

## Expected structure

```text
apps/
  kajastus/
  opastin/
packages/
  shared-types/
docs/
````

The shared package can remain minimal until contracts begin to stabilize.

## Done for the first slice

The first slice is considered done when:

* the monorepo runs locally
* Opastin exposes a collection graph endpoint
* Kajastus fetches that graph successfully
* Kajastus renders returned places on a Leaflet map
* Kajastus shows the collection, memories, and items in a simple UI
* the frontend uses the hydrated graph locally for rendering

## Status

This repository is at the beginning of implementation.

The immediate goal is to establish a clean, working, end-to-end foundation for the system.
