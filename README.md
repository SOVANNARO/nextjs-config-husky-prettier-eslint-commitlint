## Config Husky Prettier Eslint and Commitlint

### Install Husky

```
pnpm add --save-dev husky
```

### Init Husky Folder

```
pnpm exec husky init
```

### Create File `pre-commit` With script below

```
npm run lint

```

### Create File `pre-push` With Script below

```
npm run test
```

### Install Conventional Commits

```
pnpm install @commitlint/cli @commitlint/config-conventional -- save-dev
```

### Create File `commitlint.config.js` with script below

```
module.exports = { extends: ["@commitlint/config-conventional"] };
```

### Create File `commit-msg` With Script below

```
npx --no-install commitlint --edit "$1"

```

### If Push branch to git error with message `fix npm error Missing script: "test"`

```
{
  "scripts": {
    "test": "echo \"No test specified\" && exit 0"
  }
}
```

## Config Prettier

### Install Prettier:

```
npm install --save-dev prettier
```

### Create a `.prettierrc` file in the root of your project.

```
{
  "singleQuote": false,
  "trailingComma": "all",
  "tabWidth": 2,
  "semi": true
}
```

### Create a `.prettierignore` File in the root of your project

```
node_modules
build
dist
```

### Format Your Code:

```
npx prettier --write "src/**/*.{js,jsx,ts,tsx}"
```

### Run the script for format

```
npm run format
```

### Integrate Prettier with ESLint (Optional but Recommended):

```
pnpm install --save-dev eslint-config-prettier eslint-plugin-prettier
```

### Config file `eslint.config.mjs`

```jsx
import { dirname } from "path";
import { fileURLToPath } from "url";
import { FlatCompat } from "@eslint/eslintrc";
import prettierPlugin from "eslint-plugin-prettier";

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);

const compat = new FlatCompat({
  baseDirectory: __dirname,
});

const eslintConfig = [
  ...compat.extends("next/core-web-vitals", "next/typescript"),
  ...compat.extends("plugin:prettier/recommended"),
  {
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      "prettier/prettier": "error",
    },
  },
];

export default eslintConfig;

```

### After config file `eslint.config.mjs` have error need two git resolve problem

### Using Git:

You can configure Git to handle line endings automatically:

```
git config --global core.autocrlf input
```

Then, re-checkout the file:

```
git checkout -- commitlint.config.js
```
