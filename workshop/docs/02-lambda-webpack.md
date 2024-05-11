Building a lambda project with webpack
======================================

Let's create a folder for the project:

```sh
mkdir workshop
```

Then access to this new folder:

```sh
cd workshop
```

And let's create a yarn project running:

```sh
yarn init -py
```

Now, we will going to create the set up to manage a monorepo. This approach is useful if we are building a library that is used by several project, or, if there is dependency between project of the same product. To accomplish this, we are gonna use **yarn workspaces** and **lerna**

Let's add the `"workspaces"` properties in the root of the `package.json` file:

```json
{
    "name": "workshop",
    "license": "MIT",
    "private": true,
    "workspaces": [
        "packages/*"
    ]
}
```

