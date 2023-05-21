---
title: Create a Public Site
position: 3
layout: "@docs"
---

Although Space is optimized for running single-user full-stack apps, you can also use it to host public static websites. This is useful if you want to host a personal website or a landing page for your app.

## Making a Micro public

Every app on Space can contain up to 5 [Micros](/docs/en/build/fundamentals/the-space-runtime/micros), which are private by default. You can make individual Micros public using the app's [`Spacefile`](/docs/en/build/fundamentals/the-space-runtime/about#the-spacefile). Just set the `public` flag to `true` for each Micro you want to publicize.

Example:

```yaml
micros:
  - name: frontend
    src: .
    engine: svelte
    primary: true
    public: true
```

Only the Micro with the `primary` flag set to `true` will be served on the root domain. The other Micros will be served on their respective paths under the root domain. For example, if a Micro is named `api` (or has the `path` property set to `api`), it will be served on `https://app-name.deta.app/api`. Read more about Micro routing [here](/docs/en/build/fundamentals/micros#micro-routing).


> __Note:__ `public: true` is just a shorthand for `public_routes: ["/*"]`. We recommend using [`public_routes`](/docs/en/reference/spacefile#public_routes) instead if you need more customization.

## Connecting a custom domain

You can set up a custom domain by clicking on the three dots (__…__) at the bottom right of your app's icon and select **Settings**. Then, switch to the **Domains** tab and click **Add Custom Domain** and follow the instructions.

For now, you can only set one domain per app, and the root of that domain will be connected to the primary Micro. The other Micros will resolve to their respective paths under the root domain, as defined in the `Spacefile`.

> We're working on greatly improving the custom domain experience in the future. We will also allow the customization of subdomains (e.g. `customtext.deta.dev`). Stay tuned!