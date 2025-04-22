# Content Driven Web Application Foundations by Sanity

Follow the [course](https://www.sanity.io/learn/course/content-driven-web-application-foundations)

## Sanity and Next.js

This is a [Sanity.io](https://sanity.io) and [Next.js](https://nextjs.org) project created following a Course on [Sanity Learn](https://sanity.io/learn).

## Getting Started

First, run the development server:

```bash
npm run dev
```

- Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.
- Open [http://localhost:3000/studio](http://localhost:3000/studio) to edit content.

## Managing Types

Run the following command:

```bash
npx sanity@latest schema extract --path=./src/sanity/extract.json
```

<br>

Create a new file at the root of your project: _sanity-typegen.json_

```bash
{
  "path": "./src/**/*.{ts,tsx,js,jsx}",
  "schema": "./src/sanity/extract.json",
  "generates": "./src/sanity/types.ts"
}
```

<br>
Run the following command:

```bash
npx sanity@latest typegen generate
```

The extract.json file will need to be updated every time you update your Sanity Studio schema types and TypeGen every time you do or update your GROQ queries.

Instead of doing these steps separately, you can include scripts in your package.json file to make running these automatic and more convenient.

Update _package.json_ scripts:

```bash
"scripts": {
  // ...all your other scripts
  "predev": "npm run typegen",
  "prebuild": "npm run typegen",
  "typegen": "sanity schema extract --path=./src/sanity/extract.json && sanity typegen generate"
},
```

_You can now run both the schema extraction and TypeGen commands with one line:_

```bash
npm run typegen
```
