# Local npm package registry

### Host a local npm registry with [verdaccio](https://verdaccio.org/docs/en/installation)

#### Docker

1. Run the docker container 

   `````
   docker run -it --rm --name verdaccio -p 4873:4873 verdaccio/verdaccio
   `````

2. Login to the registry 

   ```
   npm login --registry=http://localhost:4873
   ```

3. Publish your package to the registry 

   ```
   npm publish  --registry=http://localhost:4873
   ```

4. Install your package from the registry

   ```
   npm install --registry=http://localhost:4873
   ```

#### Scoped packages

You can also set specific registries for scoped packages, for example `@scope` everything under this scope will be published to and installed from the specified registry after using the following command:

``` 
npm config set -g @scope:registry http://localhost:4873
```

Every package you install under this scope (Eg. `npm i @scope/cool-package`) will automatically come from the specified registry.