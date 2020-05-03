# Precisely Prettier

> _Based on [prettier-setup](https://github.com/lipis/prettier-setup) by the amazing [@lipis](https://github.com/lipis)._ 🙏

This project sets up formatting tools to keep your code clean and consistent, so you never have to argue about style again:

- [Prettier](https://prettier.io) is an opinionated code formatter that enforces a consistent style by parsing your code and re-printing it with its own rules.
- [Husky](https://github.com/typicode/husky) uses Git hooks to ensure that **Prettier** runs on all staged changes to fix files before committing.

The setup described here will format DITA XML, JSON, Sass, Markdown, and YAML files, but you can adjust the settings to your own needs.

## Installing Prettier and the XML plugin

This step adds Prettier and the XML plugin to your project's dependencies so they're available locally regardless of the system configuration.

### Install with `yarn`

```bash
yarn add prettier @prettier/plugin-xml --dev --exact
```

<details>
<summary>Install with <code>npm</code></summary>

```bash
npm install prettier @prettier/plugin-xml --save-dev --save-exact
```

</details>

### Set up the scripts

Open the [`package.json`](/package.json) file in your project and add the following `scripts`\* entries (or copy them from here):

```json
"scripts": {
  "fix": "yarn prettier --write",
  "prettier": "prettier \"**/*.{dita,json,md,scss,yaml,yml}\"",
  "test": "yarn prettier --list-different"
}
```

\* If you are using `npm`, replace `yarn` with `npm run` in the above section.

## Installing Husky and commit hooks

Set up Husky and the `precise-commits` commit hooks to format changed files before each commit.

### Install with `yarn`

```bash
yarn add husky precise-commits --dev --exact
```

<details>
<summary>Install with <code>npm</code></summary>

```bash
npm install husky precise-commits --save-dev --save-exact
```

</details>

### Set up the rules

Add the `precise-commits` and `husky` rules to the [`package.json`](/package.json) file in your project:

```json
"precise-commits": {
  "*.{dita,json,md,scss,yaml,yml}": ["prettier --write"]
},
"husky": {
  "hooks": {
    "pre-commit": "precise-commits"
  }
},
```

---

<details>
<summary>Prettier rules</summary>

This project defines the following settings in the [`.prettierrc.json`](/.prettierrc.json) file. You can adjust these values according to your own preferences.

| Rule                                                                                                              | Value\*     |
| ----------------------------------------------------------------------------------------------------------------- | ----------- |
| [`arrowParens`](https://prettier.io/docs/en/options.html#arrow-function-parentheses)                              | `avoid`     |
| [`bracketSpacing`](https://prettier.io/docs/en/options.html#bracket-spacing)                                      | **`false`** |
| [`endOfLine`](https://prettier.io/docs/en/options.html#end-of-line)                                               | **`lf`**    |
| [`htmlWhitespaceSensitivity`](https://prettier.io/docs/en/options.html#html-whitespace-sensitivity)               | `css`       |
| [`jsxBracketSameLine`](https://prettier.io/docs/en/options.html#jsx-brackets)                                     | `false`     |
| [`printWidth`](https://prettier.io/docs/en/options.html#print-width)                                              | `80`        |
| [`proseWrap`](https://prettier.io/docs/en/options.html#prose-wrap)                                                | `preserve`  |
| [`requirePragma`](https://prettier.io/docs/en/options.html#require-pragma)                                        | `false`     |
| [`semi`](https://prettier.io/docs/en/options.html#semicolons)                                                     | `true`      |
| [`singleQuote`](https://prettier.io/docs/en/options.html#quotes)                                                  | **`true`**  |
| [`tabWidth`](https://prettier.io/docs/en/options.html#tab-width)                                                  | `2`         |
| [`trailingComma`](https://prettier.io/docs/en/options.html#trailing-commas)                                       | **`all`**   |
| [`useTabs`](https://prettier.io/docs/en/options.html#tabs)                                                        | `false`     |
| [`vueIndentScriptAndStyle`](https://prettier.io/docs/en/options.html#vue-files-script-and-style-tags-indentation) | **`true`**  |

\* Values in **bold** differ from the Prettier defaults.

</details>

<details>
<summary>Dependencies</summary>

- [husky](https://github.com/typicode/husky)
- [precise-commits](https://github.com/nrwl/precise-commits)
- [prettier](https://github.com/prettier/prettier)
- [@prettier/plugin-xml](https://github.com/prettier/plugin-xml)

</details>
