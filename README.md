# Kitstarter

My personal starter repo, created through an integration of the [Turborepo + Next.js (with-tailwind) template](https://github.com/vercel/turbo/tree/main/examples/with-tailwind) and Steven Tey's [Precedent starter](https://github.com/steven-tey/precedent).

This starter assumes use of:

- [pnpm](https://pnpm.io/) as a package manager
- [Turborepo](https://turbo.build/repo) as a build system
- [Next.js](https://nextjs.org/) as a React framework
- [Vercel](https://vercel.com/) for automated deployment & hosting


## Contents & Tech Stack

### Monorepo apps

- `web`: a [Next.js](https://nextjs.org/) app with [Tailwind CSS](https://tailwindcss.com/)
- `docs`: another [Next.js](https://nextjs.org/) app (currently identical to the above)

### Local packages (for now, sourced from Turborepo)

- `ui`: a stub React component library with [Tailwind CSS](https://tailwindcss.com/), shared by both `web` and `docs` applications
- `eslint-config-custom`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `tsconfig`: `tsconfig.json`s used throughout the monorepo

### NPM packages

#### Code Quality

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting

#### Database

- (coming soon) [Prisma ORM](https://vercel.com/templates/next.js/postgres-prisma)- Typescript-first ORM
- (coming soon) [Vercel Postgres](https://vercel.com/storage/postgres) - serverless Postgres at the Edge

#### UI

- [Tailwind CSS](https://tailwindcss.com/) for styles
- (coming soon) [Radix](https://www.radix-ui.com/) - React component libary  
- (coming soon) [Lucide Icons](https://lucide.dev/) - open-source icon library
- (coming soon) [`next/font`](https://nextjs.org/docs/pages/building-your-application/optimizing/fonts) - font optimization
- (coming soon) [`ImageResponse`](https://nextjs.org/docs/app/api-reference/functions/image-response) - dynamic OG images at the edge
- (coming soon) one or more of the following animation libraries:
  - [Framer Motion](https://www.framer.com/motion/) - motion library for React
  - [React Spring](https://github.com/pmndrs/react-spring) - spring-physics React animation library
  - [Renature](https://formidable.com/open-source/renature/gallery/) - archived project that I may still want to pull from; see [gallery](https://formidable.com/open-source/renature/gallery/)

### Hooks & helper functions (most by Steven Tey, descriptions copied from the [Precedent README](https://github.com/steven-tey/precedent/blob/main/README.md))

- all coming soon:
  - `useIntersectionObserver` –  React hook to observe when an element enters or leaves the viewport
  - `useLocalStorage` – Persist data in the browser's local storage
  - `useScroll` – React hook to observe scroll position (example)
  - `nFormatter` – Format numbers with suffixes like 1.2k or 1.2M
  - `capitalize` – Capitalize the first letter of a string
  - `truncate` – Truncate a string to a specified length
  - [`use-debounce`](https://www.npmjs.com/package/use-debounce) – Debounce a function call / state update



## Other templates and resources to keep in mind
- [WebGL gradient](https://whatamesh.vercel.app/)
- [On-demand ISR](https://vercel.com/templates/next.js/on-demand-incremental-static-regeneration)
- [Vercel Analytics](https://vercel.com/analytics)
- select features & config from the [Next.js Enterprise Boilerplate template](https://vercel.com/templates/next.js/nextjs-enterprise-boilerplate)



## A note on building `packages/ui` (adapted from the Turborepo [with-tailwind starter](https://github.com/vercel/turbo/blob/main/examples/with-tailwind/README.md)) README
This example is setup to build `packages/ui` and output the transpiled source and compiled styles to `dist/`. This was chosen to make sharing one `tailwind.config.ts` as easy as possible, and to ensure only the CSS that is used by the current application and its dependencies is generated.

Another option is to consume `packages/ui` directly from source without building. If using this option, you will need to update your `tailwind.config.ts` to be aware of your package locations, so it can find all usages of the `tailwindcss` class names.

For example, in `packages/tailwind-config/tailwind.config.ts`:

```js
  content: [
    // app content
    "src/**/*.{js,ts,jsx,tsx,mdx}",
    // include packages if not transpiling
    "../../packages/**/*.{js,ts,jsx,tsx,mdx}",
  ],
```


## More on Turborepo (adapted from the Turborepo [basic starter](https://github.com/vercel/turbo/tree/main/examples/basic/README.md) README)

### Remote Caching

Turborepo can use a technique known as [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. Assuming you have an account, run `pnpm dlx turbo login` from the root of your reposity to authenticate the Turborepo CLI with your Vercel account.

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

```sh
pnpm dlx turbo link
```

### Useful Turborepo Links

- [Tasks](https://turbo.build/repo/docs/core-concepts/monorepos/running-tasks)
- [Caching](https://turbo.build/repo/docs/core-concepts/caching)
- [Filtering](https://turbo.build/repo/docs/core-concepts/monorepos/filtering)
- [Configuration Options](https://turbo.build/repo/docs/reference/configuration)
- [CLI Usage](https://turbo.build/repo/docs/reference/command-line-reference)
