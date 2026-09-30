# Fuel Relief Replies

Searchable library of standard customer responses for PM Fuel Relief complaints
registered on the BPO CMS. Built for L2 support: find the right reply by
complaint nature or keyword, and copy it straight into the ticket.

41 replies across four categories — Registration, Token Generation,
Token Redemption, and Status & Closing. Every reply is copied with the
agent's signature appended automatically.

## Setting your name

The signature name sits in the page header, next to "Every reply is copied
signed". Type your own name there and it saves immediately — each agent
sets it once on their own machine.

The name is held in `localStorage`, so it is per-browser: it survives
reloads and sign-outs, and never reaches anyone else. Clearing site data
resets it to the default. Leaving the field empty copies the reply with no
signature at all.

## Running it

It is a single static file with no build step and no dependencies.

- **Locally** — double-click `index.html`, or open it in any browser.
- **On a server** — copy `index.html` to any web root.

Only the web fonts load from the network. Without internet the page still
works; the typeface falls back to a system font.

## Changing the login

The credentials are two constants near the top of the `<script>` block in
`index.html`:

```js
const USERNAME = "admin";
const PASSWORD = "CHANGE_ME";
```

Edit both, save, commit.

> **This is not real security.** The check runs in the browser, so anyone who
> opens the page source — or who can read this repository — can see the
> password. It keeps casual visitors out and nothing more. Keep this
> repository private, and do not reuse a password from any other system.

The signed-in state is held in `sessionStorage`, so closing the tab signs
you out.

## Adding or editing a reply

All content lives in the `GROUPS` array in `index.html`. Each entry is:

```js
{ t:"Card title",
  b:"The reply text that gets copied. Ends with Thank you.",
  w:"When to use this one." }
```

Add the object to the right group (`reg`, `gen`, `red`, `gnl`) and reload.
The counter, the search index and the category filters all pick it up
automatically.

## Placeholder values

A few replies carry example vehicle numbers — `DGN-12-2074`, `LEZ-13-9639`,
`RIB-15626`, `ACT-6788`. Replace these with the real plate from the ticket
before sending. The "Use when" line on each card flags it.

## Deploying

The repository is private, so GitHub Pages needs a paid plan. Options:

- Keep it private and open `index.html` locally (no hosting needed).
- Host on any internal web server.
- Make the repository public to use free GitHub Pages — but then the
  password is world-readable, so remove the login first.
