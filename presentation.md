---
author: Sai and Drew,
date: November 25, 2024
paging: Slide %d / %d
theme: ./themes/dracula.json
---

# Feature Flagging with `Flagger`

RSS Dev Show & Tell

---

## Goals

After this hour, attendees will be able to

1. Use Flagger's local webapp and dev webapp to control local feature flag values, and 
2. Set up Flagger's `client-sdk` package in their project and use it to check flag values.

Additionally, attendees will eventually be able to (perhaps after some documentation consultation):

3. Set up Flagger's `server-sdk` package in their project, and
4. Use Flagger's `e2e-utils` package to control flags during their end-to-end tests.

---

## What is Flagger?

- A *wrapper* for LaunchDarkly's javascript SDKs, including:
  - a React provider/hook pair for client-side flag checks,
  - a service for server-side flag checks, and
  - utilities for controlling flags during test runs
<br>
- A *local webapp* to enable flag control both by hand and in end-to-end tests
<br>
- A *webapp* running in Dev that allows per-user feature flag control
  - (This will eventually be deployed to QA and Prod too)

---

## Why use Flagger?

- Flagger integrates *LaunchDarkly* into your app *with less boilerplate*
  - no need to initialize the client provider
  - encapsulates client-ids so you don't have to inject them
<br>
- Flagger gives you *control* over feature flags *during local development*
  - see the effect of changing flags on your app without deploying it
<br>
- Helps you write *better tests*
  - includes utilities that support both *isolated* and *end-to-end* tests
  - makes it easy to test your app with different flag configurations

---

## Demo

Let's see what Flagger's setup looks like in `forms`!

<!--
- walk through where all of the setup is 
  - docker-compose
  - setup-dotenv
  - vite config
  - index.tsx (for provider)
- live example of adding a flag to a component
  - `FormBuilderToolbar.tsx`
- do we want to show the isolated test setup? 
  - if so, have it written beforehand and just show it
-->

---

## Your Turn!

Everything you need is written out in the GitHub repo: 
[https://github.com/risk-and-safety/flagger](https://github.com/risk-and-safety/flagger)

### Directions

- Set up Flaggers' local Docker container
  - `.env` -- add port
  - `docker-compose.yaml` -- add container declaration
  - `vite.config.ts`-- add config 
<br>
- Add the Flagger to your client: `pnpm install @risk-and-safety/flagger-client-sdk`
<br>
- Include `FlaggerProvider` in your component tree in `index.tsx`
<br>
- Check a flag somewhere in your app:
```ts
  const flagger = useFlagger();
  const flag = flagger.check('flagger-test-flag');
```
- Toggle the flag from `/flagger` and reload to see the effect


---

## Note: Local vs Deployed Behavior

- During *local development*, the Flagger SDKs read flags from the *locally-running Flagger server*
  - The server, in turn, gets information about what flags exist from LaunchDarkly
<br>
- In a *deployed environment* (eg., Dev, QA, Prod), Flagger gets flag data *directly from LaunchDarkly*
<br>
(Flagger figures this out on its own, you don't have to pass any configuration)

---

## Now what? 

- Start using feature flags more! Live the continuous delivery dream
<br>
- You can remove LaunchDarkly from your imports and replace it with Flagger
<br>
- Check out the docs for `flagger-server-sdk` and `flagger-e2e-utils`, which 
  bring Flagger's features to your server applications and end-to-end tests, respectively

