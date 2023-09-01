# embroider-css-malformed-css-omptimization

Minimal reproduction of css optimizations malforming styles in production builds

### Dev build

![image](https://github.com/C0rydoras/embroider-css-malformed-in-prod-build/assets/110528300/ed428f2f-e4a2-4095-87a1-a139fcb6d362)

### Prod build

![image](https://github.com/C0rydoras/embroider-css-malformed-in-prod-build/assets/110528300/c44ad2c2-55ca-4918-a942-8c0c1f19ef9f)

```bash
yarn start # starts live server
docker compose up # starts prod build at localhost:8080
```

In this case the problem seems to be caused by wrongly ordered rules:

```css
.uk-button {
  padding: 0 30px;
  font-size: 0.875rem;
  line-height: 38px;
}

.uk-button,
ul.button-nav li a {
  margin: 0;
  border: 0;
  overflow: visible;
  font: inherit; /* this overrides font-size and line-height with inherit */
  color: inherit;
  -webkit-appearance: none;
  border-radius: 0;
  display: inline-block;
  box-sizing: border-box;
  vertical-align: middle;
  text-align: center;
  text-decoration: none;
  text-transform: uppercase;
  transition: 0.1s ease-in-out;
  transition-property: color, background-color, border-color;
}
```

Probably related to https://github.com/css/csso/issues/429

## Prerequisites

You will need the following things properly installed on your computer.

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/)
- [Yarn](https://yarnpkg.com/)
- [Ember CLI](https://cli.emberjs.com/release/)
- [Google Chrome](https://google.com/chrome/)

## Installation

- `git clone <repository-url>` this repository
- `cd embroider-css-malformed-css-omptimization`
- `yarn install`

## Running / Development

- `ember serve`
- Visit your app at [http://localhost:4200](http://localhost:4200).
- Visit your tests at [http://localhost:4200/tests](http://localhost:4200/tests).

### Code Generators

Make use of the many generators for code, try `ember help generate` for more details

### Running Tests

- `ember test`
- `ember test --server`

### Linting

- `yarn lint`
- `yarn lint:fix`

### Building

- `ember build` (development)
- `ember build --environment production` (production)

### Deploying

Specify what it takes to deploy your app.

## Further Reading / Useful Links

- [ember.js](https://emberjs.com/)
- [ember-cli](https://cli.emberjs.com/release/)
- Development Browser Extensions
  - [ember inspector for chrome](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi)
  - [ember inspector for firefox](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)
