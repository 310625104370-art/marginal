# Marginal — Blog Platform with Comments

A self-contained blogging platform demo: auth, post CRUD, and threaded comments.

## How to use
Open `index.html` in any modern browser — no build step, no server, no dependencies.

Browse right away with **demo / demo1234** (comes with 3 seeded posts and comments), or register your own account.

## What's inside
- **Auth** — register/sign in with a display name, username and password
- **Post CRUD** — write, publish, edit, and delete your own posts (title, tags, body); word count + estimated reading time shown while writing
- **Feed** — reverse-chronological index of all posts, searchable by title/body/tags, with a "My posts" view scoped to the signed-in user
- **Comments** — threaded comment list under each post; any signed-in user can comment, and can delete their own comments
- **Ownership rules** — edit/delete controls for a post only appear to its author (enforced in the UI, same caveat as below)

## Architecture note
Everything runs client-side. An `api` object in the JS stands in for what would normally be REST endpoints (`loadPosts`, `saveComments`, etc.) — right now those read/write the browser's localStorage instead of calling a server, and there's no real database.

To make this a genuine full-stack app per the assessment's requirements:
- Build backend REST APIs (e.g. Node/Express) for users, posts, and comments, backed by MySQL, PostgreSQL, or MongoDB
- Swap each `api.*` function body for a `fetch()` call to the matching endpoint
- Replace the local password hash with real authentication (bcrypt + sessions/JWT)
- Enforce "only the author can edit/delete" server-side — right now that check only lives in the UI
