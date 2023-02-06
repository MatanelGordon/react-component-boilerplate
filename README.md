# React Storybook Boilerplate
A Boilerplate for building react components using typescript and storybook

Technologies:
- Storybook
- Typescript
- Vitest
- React
- SCSS (for Sass look [here](#Switching-to-sass))
- postCSS
- husky + lint-staged
- eslint + prettier

Features:
- Zero storybook-production mismatch
- Unit Tests (using `vitest`)
- Full control over each configuration
- CSS Preprocessors support
- CSS Modules support

## Usage

### Using `degit`

to get the boilerplate type the following:

```bash
npx degit https://github.com/MatanelGordon/react-storybook-boilerplate.git <directory name>
```

### Using git

to get the boilerplate type the following:

```bash
git clone --depth 0 https://github.com/MatanelGordon/react-storybook-boilerplate.git <directory name>
```

To run storybook type the following:

```bash
npm run storybook
```

> NOTE: You can also use yarn

## Monorepo Integration

### Using Turborepo
install the boilerplate inside `packages/`

refer to [Usage](#Usage)

### Using Nx

Goodluck :)

> There is currently no integration with Nx at the moment. hopfully in the future... 


## Preprocessors Integration
In order to add more rules - Modify `webpack.config.js` file, from there, it will sync all rules with storybook and allow you to enjoy it both in dev and production.

> Also, there might be cases where you need to change other configurations such as eslint, postcss and stylelint

### Switching to sass

By default, this boilerplate uses SCSS. To use Sass, do the following:
1. uninstall `postcss-scss` and install `postcss-sass`
2. change in `postcss.config.js`:
```javascript
const autoPrefixer = require('autoprefixer');
module.exports = {
	syntax: 'postcss-sass',
	plugins: [
		autoPrefixer
	]
}
```
3. (optional) If stylelint throws errors, be sure to uninstall `stylelint-config-standard-scss`


### Example: Switching to Less

First, uninstall `sass`, `sass-loader`, and `postcss-scss`.

```bash
npm un sass sass-loader postcss-scss
```

then, install `less`, `less-loader` and `postcss-less`

```bash
npm i -D less less-loader postcss-less
```

Then, modify css rule in `webpack.config.js` file to be the following:

```javascript
{
	test: /\.less$/,
	use: [
		'style-loader',
		{
			loader: "css-loader",
			options: {
				modules: {
					auto: true
				}
			}
		},
		{
			loader: 'postcss-loader',
			options: {
				implementation: require('postcss'),
			},
		},
		{
			loader: "less-loader",
			options: {
				implementation: require("less"),
			},
		},
	]
}
```

Then, uninstall `stylelint-config-standard-scss` and install `stylelint-config-recommended-less
`.

```bash
npm un stylelint-config-standard-scss
```

to install `stylelint-config-recommended-less`:

```bash
npm i -D stylelint-config-recommended-less
```
