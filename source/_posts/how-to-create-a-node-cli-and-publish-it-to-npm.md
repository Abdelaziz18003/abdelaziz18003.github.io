---
title: How to create a node.js CLI an publish it to NPM
description: In this article, we will see together how to create a basic node.js CLI and share it with the world using NPM.
photos:
  - /img/node-cli.jpg
---

![node-cli](/img/node-cli.jpg)

The toy programming language that [Brendan Eich](https://en.wikipedia.org/wiki/Brendan_Eich) created back in the 90s, has became recently one of the most powerful and popular programming languages in the world. One of the big reasons that led to that progress is the invention of Node.js in 2009 by [Ryan Dahl](https://en.wikipedia.org/wiki/Ryan_Dahl). Node.js and its large package management system NPM took Javascript from just being a simple scripting language for web browsers to be a full featured language that runs everywhere and helps building all kinds of cool pieces of software.

In this article, we will see together how to create a basic node.js CLI and share it with the world using NPM.

## Let it be simple

The CLI that we are going to build is the simplest CLI that could ever exist. We don't need to spend our energy building a complex one, because we have more important things to discuss. All what our CLI will do is taking a `name` and printing `Hello {name}, welcome to node.js!` to the console, as shown below.

```bash
$ hello Mohammed
Hello Mohammed, welcome to node.js!
```

## Let's make it

First, let's make a folder called `hello`. Inside it, let's create a `cli.js` file that will contain all our code. Yes of course! you can name it as you want as long as you stay consistent with the name you chose. Here is all the code we need to be written to `cli.js`.

```js
// cli.js
let name = process.argv[2];
console.log(`Hello ${name}, welcome to node.js!`);
```

let's now run the script by typing `node cli.js Mohammed` and there you go. You should get `Hello Mohammed, welcome to node.js!` printed to the console.

```bash
$ node cli.js Mohammed
Hello Mohammed, welcome to node.js!
```

In case you are wondering what `process.argv` means, it is simply an array that contains all the options that are passed in the command line when excuting the script. The first element of the array `argv[0]` is the path to the `node` command in the filesystem, the second `argv[1]` is the path to the script file `path/to/cli.js` that we want to execute while the third `argv[2]` is the `name` that we want to print.

Great, the script now is printing the message that we are expecting. But, Didn't we say above that the usage should be `hello {name}` not `node cli.js {name}`? Yes, we did. And this is what we are going to do together right now.

## It is just Shebang not Magic

Have you ever seen this comment `#!/usr/bin/env node` at the very top of a Javascript file and wondered what this is for? We all were in the same situation. This is called the [Shebang](https://en.wikipedia.org/wiki/Shebang_&#40;Unix&#41;). It is a comment that tells the Operating System what interpreter to use for this file if it is ran as an executable. We need to add it to the very top of our `cli.js`.

```js
#!/usr/bin/env node
let name = process.argv[2];
console.log(`Hello ${name}, welcome to node.js!`);
```

This means for the OS that this file should be executed using the default node.js version installed on your system (the version that you get by typing `node` in your terminal).

## Please give it a name

At this moment it is time to turn our CLI to an NPM package. All we need is creating a `package.json` file that will contain information about the package. You can create it manually or automatically using `npm init -y` command (feel free to modify the default properties as you want).

The last step is telling NPM the command's name that we want to use. As we said before we want to replace `node cli.js {name}` by `hello {name}`. To achieve this, we simply add a `bin` property to `package.json` that contains the command's name and the corresponding file to execute.

```js
//package.json
"bin": {
  "hello": "cli.js"
}
```

By reaching this point, our CLI is finished and it is ready to be published on NPM. But first let's test it locally to see if everything is working as expected.

## Test it locally first

To test the CLI locally we need it to be installed globally, so the `hello` command will be available everywhere. But we haven't publish it yet, how can it be installed globally? Here we need to run the `npm link` command.

```bash
cd hello
npm link
```

when you run this command inside a package folder, it will make it available in the global scope as if it was installed with the `-g` flag.

Now, let's test the CLI by typing `hello {name}`. Note that you can run `hello` from any location on your system, you are not limited to the package folder.

```bash
hello Mohammed
Hello Mohammed, welcome to node.js!
```

*Congratulations!!* You've made your first node.js CLI. If you want to publish it to NPM and show it to the world, you're almost there.

## Publish it to NPM

This is the easiest part as you may not expected. First, you need to create an account on [npmjs.com](https://www.npmjs.com). Then login to it from you terminal using `npm login`.

```bash
$ npm login
Username: npmuser
Password:
Email: (this IS public) npmuser@gmail.com
Logged in as npmuser on https://registry.npmjs.org/.
```

It will ask you for your `username`, `password` & `email` and you should provide the correct credentials. Once you are logged in successfully, you will be able to publish your CLI and share with the world by running `npm publish` from the package folder.

```bash
cd hello
npm publish
```

If there is no NPM package already published which have the same name as yours, after some second you can see your package live. Otherwise, you have to change the `name` property in `package.json` to an available value.

Now, everyone on planet earth with access to internet can install your package using `npm i -g {yourPackageName}` and execute it on there own machines. Thus, you've made your first contribution to a big and awesome community. Finally, don't forget to share your code for good.
