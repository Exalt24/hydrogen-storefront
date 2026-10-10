# hydrogen-storefront

A headless Shopify storefront on [Hydrogen](https://shopify.dev/custom-storefronts/hydrogen) (React Router, Vite), connected to a Shopify **development store** through the Storefront API.

**What this is, plainly:** Shopify's own Hydrogen "Skeleton" starter with the store connection done. The pages and components are the stock template (home, collections, product pages, search, cart, blogs, policy pages, customer account), not a custom design. The work in this repo is the wiring: a development store, a Storefront access token, the environment settings, and a read query against the live store that returns its products. Nothing here is hosted, and there is no screenshot of a running site yet.

## Run it

Requirements: Node.js 22 or 24 and your own Shopify development store.

```bash
npm install
cp .env.example .env     # fill in the store domain, the Storefront token and a session secret
npm run dev              # Shopify CLI starts the storefront on http://localhost:3000
```

`.env.example` explains the one non-obvious step: the Storefront token is minted through the Admin API with `storefrontAccessTokenCreate`, which is denied unless the app already holds the `unauthenticated_*` scopes, and the denial does not say so. `PUBLIC_CHECKOUT_DOMAIN` is also required, because the analytics provider throws on every render without it.

## Stack

React Router, Hydrogen, Vite, the Shopify CLI, the Storefront API (version set in `.env`), GraphQL code generation, ESLint and Prettier.

## Limits

- The UI is the starter's, unmodified; the store is a development store with sample products.
- No tests beyond the starter's lint setup, and no hosted copy.
