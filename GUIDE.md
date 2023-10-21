# Guide

We will create authentication system in Nuxt 3 from scratch.

## Preparation:

- [ ] Create a new nuxt project
- [ ] Install `@sidebase/nuxt-auth` module
- [ ] Configure `@sidebase/nuxt-auth` module

```ts
export default defineNuxtConfig({
  modules: ["@sidebase/nuxt-auth"],
  auth: {
    provider: {
      type: "authjs",
    },
  },
});
```

- [ ] Create the server side file

```ts
// file: ~/server/api/auth/[...].ts
import { NuxtAuthHandler } from "#auth";
import CredentialsProvider from "next-auth/providers/credentials";
export default NuxtAuthHandler({
  secret: "your-secret-here",
  providers: [
    // @ts-expect-error You need to use .default here for it to work during SSR. May be fixed via Vite at some point
    CredentialsProvider.default({}),
  ],
});
```

- [ ] Create the client side file

```ts
pages: {
  // Change the default behavior to use `/login` as the path for the sign-in page
  signIn: "/login";
}
```

- [ ] Authenticate the user
- [ ] Serverside middleware
- [ ] Clientside middleware
