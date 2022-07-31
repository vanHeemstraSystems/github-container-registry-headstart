# 200 - Publishing your package

1. Create a new repository on GitHub, adding the ```.gitignore``` for Node. For more information, see "[Creating a new repository.](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-new-repository)"

Our new repository is called "GitHub Packages Demo Repository" and is accessable at https://github.com/vanHeemstraSystems/github-packages-demo-repository

2. Clone the repository to your local machine.

where:

YOUR-USERNAME = vanHeemstraSystems
YOUR-REPOSITORY = github-packages-demo-repository

```
$ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
$ cd YOUR-REPOSITORY
```

3. Create an index.js file and add a basic alert to say "Hello world!"

```
$ touch index.js
```

```
console.log("Hello, World!");
```
index.js

4. Initialize an npm package with ```npm init```. In the package initialization wizard, enter your package with the name: ```@YOUR-USERNAME/YOUR-REPOSITORY``` (here: @vanHeemstraSystems/github-packages-demo-repository), and set the test script to ```exit 0```. This will generate a ```package.json``` file with information about your package.

```
$ npm init
```

```
{
  ...
  "name": "@YOUR-USERNAME/YOUR-REPOSITORY",
  ...
  "scripts": {
    "test": "exit 0"
  }
...
}
```
package.json

**NOTE**: ```npm init``` will complain whe using capitals in the package name, hence we have to use all lowercase for the package name instead (@vanheemstrasystems/github-packages-demo-repository).

5. Run ```npm install``` to generate the ```package-lock.json``` file, then ```commit``` and ``push``` your changes to GitHub.

```
$ npm install
$ git add index.js package.json package-lock.json
$ git commit -m "initialize npm package"
$ git push
```

6. Create a ```.github/workflows``` directory. In that directory, create a file named ```release-package.yml```.

```
$ mkdir .github
$ cd .github
$ mkdir workflows
$ cd workflows
$ touch release-package.yml
```

7. Copy the following YAML content into the ```release-package.yml``` file.

```
name: Node.js Package

on:
  release:
    types: [created]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 12
      - run: npm ci
      - run: npm test

  publish-gpr:
    needs: build
    runs-on: ubuntu-latest
    permissions:
      packages: write
      contents: read
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 12
          registry-url: https://npm.pkg.github.com/
      - run: npm ci
      - run: npm publish
        env:
          NODE_AUTH_TOKEN: ${{secrets.GITHUB_TOKEN}}
```
.github/workflows/release-package.json

8. Tel NPM whcih scope and registry to publish packages to using one of the following methods:

- Add an NPM configuration file for the repository by creating a ```.npmrc``` file in the root directory with the contents (where ```@YOUR-USERNAME``` is here ```@vanheemstrasystems```):

```
$ cd ../../
$ touch .npmrc
```

```
@YOUR-USERNAME: registry=https://npm.pkg.github.com
```
.npmrc

- Edit the ```package.json``` file and specify the ```publishConfig``` key (where ```@YOUR-USERNAME``` is here ```@vanheemstrasystems```):

```
"publishConfig": {
   "@YOUR-USERNAME:registry": "https://npm.pkg.github.com"
 }
```
package.json

9. Commit and push your changes to GitHub.

```
$ git add .github/workflows/release-package.yml
# Also add the file you created or edited in the previous step.
$ git add .npmrc package.json
$ git commit -m "workflow to publish package"
$ git push
```
10. The workflow that you created will run whenever a new release is created in your repository. If the tests pass, then the package will be published to GitHub Packages.

To test this out, navigate to the **Code** tab in your repository and create a new release. For more information , see "(Managing releases in a repository](https://docs.github.com/en/github/administering-a-repository/managing-releases-in-a-repository#creating-a-release)."



More ...


