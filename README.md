# Vue canvas captcha

## Documentation

The Captcha component (`src/components/Captcha.vue`) offers a simple way to implement a captcha into webpages.

The component expects automatically generates a passphrase and displays it via canvas. This ensures that the phrase cannot be found via simple DOM analysis. The component is given the user's input for the phrase, checks for equality and sends an event based on the result of the check.

Following parameters are available for selection:

| name        | type | required           | default  |
| --- | :---: |:---:| :---:|
| userInputForPassphrase | String | yes | - |
| phraseLength | String | no | 8 |
| alphabet | String | no | 'abcdefghijklmnopqrstuvwxyz0123456789+-*§$%&' |
| fontSize | String | no | '16px' |
| fontFamily | String | no | 'Verdana |
| canvasSize | Object | no | {width: 100, height: 24} |
| canvasPosition | Object | no | {x: 0, y: 16} |

## Contribute

### Project setup
```
npm install
```

#### Compiles and hot-reloads for development
```
npm run serve
```

#### Compiles and minifies for production
```
npm run build
```

#### Lints and fixes files
```
npm run lint
```

#### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
