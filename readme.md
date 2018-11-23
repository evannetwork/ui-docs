# UI Documentation
This project handles the full rts documentation for angular-core, angular-sass, dapp-browser and the blockchain-core frontend bundle.

Be sure that you have installed the required "read the docs" dependencies: https://docs.readthedocs.io/en/latest/intro/getting-started-with-sphinx.html#quick-start

## Build
- open the "fe-docs/docs" folder and run:
```sh
npm run build
```
```sh
make html
```

## Watch
- open the "fe-docs/docs" folder and run:
```sh
npm run serve
```

```sh
sphinx-autobuild . _build/html
```
