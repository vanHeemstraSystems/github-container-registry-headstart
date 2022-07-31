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



More ...


