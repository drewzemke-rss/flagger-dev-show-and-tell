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

1. Use Flagger's local webapp and dev webapp to control feature flags, and 
2. Set up Flagger's `client-sdk` or `server-sdk` package in their project and use it to check flag values.

Additionally, attendees will eventually be able to (perhaps after some documentation consultation):

3. Use Flagger's `e2e-utils` package to control flags during their end-to-end tests.

---

## Outline

- what is Flagger?
  - wrapper for LaunchDarkly's APIs and javascript sdks
  - local webapp to enable flag control both by hand and in e2e tests
  - webapp running in dev that allows per-user feature flag control
    - eventually will run in qa and prod too and give the same control to QAs

- why use Flagger?
  - integrates LD into your app with less overhead
  - gives you control over feature flags during local development
  - lets you write better tests (e2e and isolated) that test your app with both the flag on and off

- how to set it up
  - docker, vite, client-sdk
  - or... just link to the readme?
  - put folks in breakout rooms for this? so they can work on their team's projects

- conclusion: what to do next?
  - start using feature flags more!
  - can remove LD from imports, replace with flagger
  - write isolated tests and e2e's that control flags
