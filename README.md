# Scoped Bootstrap 

Scoped Bootstrap is a modified version of bootstrap that solves the styling issue of boostrap where it covers the entire html file and therefore colliding with you own styles. It does it by demanding that any bootstrap component should be used inside a root component that has a class '.scoped-bootstrap'. It may contain issues and bugs it's not been extensively tested.   


```bash
npm install scoped-bootstrap
```

## Usage
```html
<div class="scoped-bootstrap">
<!-- Boostrap components goes inside here -->
 <div>
<!-- Other styling outside of the root bootstrap component will not be affected by bootstrap styling. -->
```

## Custom Build 
1. Modify the postcss.config.js file, by adding the class prefix for the root component. Default is `.scoped-bootstrap`

```javascript
'use strict'

module.exports = {
  map: true,
  plugins: {
    "postcss-prefix-selector": {
      exclude: [
        ':root'
      ],
      prefix: "<<put-your prefix here. Should start with dot(.) e.g. .ampath-fe>>"
    }
  }
}
```
2. Build the project to produce the dist and deploy it as a tag, or publish to npm.
```bash
npm run build
```

## Releasing
Modify package.json with <<version>>
```bash
npm run build

git add -f dist

git commit -a -m 'releasing <<version>>'

git tag <<version>>

git reset --hard HEAD~
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)