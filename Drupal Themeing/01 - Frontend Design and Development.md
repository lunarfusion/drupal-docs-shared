

In our introduction to theme development, I introduced some concepts that are not Drupal-specific, but rather they are tools that are used in general frontend development:

- node
- npm
- package.json
- postCSS
- vite

## Node.js
This is a library we use to build web applications. It is used very widely in development of software intended to work in web browsers (websites and cloud software).

## NPM (Node Package Manager)
This is how we ask node to install or update the front-end tools we are using on our project.

https://docs.npmjs.com/
## Package.json
This is the file that tells node what we want to install and what scripts we want to run.

In the package.json file, you will see:
### Dependencies
These are tiny pieces of software I want to use on my project. I might list as "dependencies" anything that helps clean my code or structure my code in a way that is easier to read. I might list something that automates some part of my work. 
### Scripts
Then, in "scripts", I tell node whwat commands I want (like npm run xxxx) and what I want those commands to do. 

For the dependencies in my package.json to work, I install them like this:
`npm i`

After installing my dependencies, I can use them by  calling my scripts with something like:
`npm run start`

or 

`npm run dev`

## PostCSS
I use PostCSS for the nesting behavior. It allows me to use an "&" symbol in my classes to build component classes with child element classes and variant classes specific to that component.

This postCSS:

```
.component {
  margin-block: 2rem;
  
  &__element {
    padding-block: 0.5rem;
    padding-inline: 1rem;
  }
}
```

Gives me this CSS:

```
.component {
  margin-block: 2rem;
}

.component__element {
  padding-block: 0.5rem;
  padding-inline: 1rem;
}
```

When we manage our postCSS using node, we search to see what packages we need to install using npm. For example, here is the NPM docs page about postCSS:

https://www.npmjs.com/package/postcss

## Vite
I am using Vite in combination with node to watch my postCSS files. When I save a change to one of my pcss files, it compiles my postCSS into CSS and saves that into a css file for me.

The script which runs this process can be see in my package.json file, under scripts.