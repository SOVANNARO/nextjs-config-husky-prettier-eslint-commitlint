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

### Create File `.commmitlintrc.cjs` with script below

```
module.exports = {
  extends: ["@commitlint/config-conventional"],
};

```

### Create File `commit-msg` With Script below

```
npx --no-install commitlint --edit $1
```
