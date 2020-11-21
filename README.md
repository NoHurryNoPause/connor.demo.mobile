# React-Native-Demo-App

A mobile app that will allow me to publicly display my approach to mobile app developement

# Planned stack

## React Native

For this Mobile app, I plan to support iOS and Android using the latest version of React-Native

## Firebase

Depending on the client's needs, I'll usually opt for firebase due to it's ability to centralize support for:

> Auth

> Hosting

> Messaging

> Notifications

> Storage (photos)

> Other extensions and feature solutions

# Expo

I'm always sceptical of adding in dependencies (which may or may not be readily in line with the release schedule of core packages) that aren't strictly needed for a project. In an active work environment I've always strayed away from using Expo, despite the many benefits it brings, due to the fact I don't like being beholden to a package like Expo's release cycle for new features/ bug fixes if I don't strictly need to be. I'm willing to accept this for non-negotiable packages like `react` since there's more weight that offsets the risk of future version changes.

This being said, for a personal app where I am essentially the primary stakeholder for issues that may arise due to it's addition, I willing to possibly utilize expo for it's easy distribution and shareability.

## Firebase

While firebase has it's downsides, s
Being a demo app where feature scope isn't of primary concern or constriction, this app will go through many cycles of re-engineering and won't have any necessary order of operations for features
My goal is to have a mobile application that interested users can see to get a better feel for my work
Having it be public facing means people can get a direct look at my approach for:

    Patterns
    Git practices
    Feature development

# Getting started

1. Download the repo and clone a local copy of the /main branch
2. From the top level of the project /react-native-demo-app run `yarn install`
3. Then run `yarn start`
4. If you have issues ensure that you have the latest versions for:

   > yarn >=1.22.10

   > npm >= 6.13.4

   > node >= 10.18.1

# React folder structure

## /api

Where client side endpoints are brought together using express

    /auth - Authentication endpoints that speak to social auth or firebase auth

## /assets

Where assets like images and font files go

    /fonts - Holds files like .ttf for use in app. Normally injected in the main app's css
    /logos - Replace these logo files for the branding of the non-base app

## /components

Holds the components used for the app

    - Avoid having component files longer than 500 lines
    - Try to keep const / class components intuitively linked

## /constants

Where any constant files will go for use on the client side app

    /strings - Here we'll place any plain text values so that they will be easily accessible/ changeable from one location
    - If the strings file becomes too large we may want to split it into multiple files
    - These are only strings used client side. If a constant needs to be shared with the backend it should be placed in the shared constants file

# General code standards

## Prettier code formatter

    Through the years, I've found that using a code formatter with project scoped settings pays off time and again as a project grows and more devlopers are added to the project.

    Not only does it add an extra layer of code cleanliness, but it also ensures that when moving between branches or merging in changes, a project manager or fellow developer won't be bogged down with white space merge conflicts that can be mentally taxing over time

## Common bad practices

    Often when we have a quick stylistic change it can be tempting to use inline styles rather than creating a one off class. While it may be appropriate to use a style definition rather than defining an entire class it is almost always bad practice to have in line styles
    The reason being that the component's render cycle will become inherintely inefficient due to constantly re-creating that component as well as all it's children during each render cycle rather than leveraging the existing render cycle's unchanged branch

    Additionally, console.logs (used for debugging but not useful for other developers that may pull your commit), unused imports, terminal/ es ling warnings should be addressed where possible prior to committing.

### Example of in-line style bad practice

`<Example component style={{ width: '100px'}} > {...otherChildComponents} </Example>`

    In this example, regardless of the events that may or may not trigger re-renders of the child components, the entire tree would be re-created each time rather than dynamically re-creating the tree based on what cannot be re-used from the previous cycle

### Example of valid console.log() to commit

`console.error('Error during api request: ',requestName,' threw error: ',e);`

    This is a useful log for another developer who, for example, may want to use an endpoint and be alerted if something goes wrong. It also only shows this log if I, as another developer, am using the function is austensibly catching an error within. It won't fill up my console with messages unless they are relevant to what I'm doing.

### Example of invalid console.log() to commit

`console.log('list of items from backend: ');`

`console.log(state.items);`

    These set of logs aren't intuitively useful as something that I, as another developer on the project who may have a task on the same component that has no interation with state.items, would want my console to inform me of.

# 3rd party packages

Ideally, we try to keep our package number small unless a use case comes up where an external package with rigerous testing and recent updates would be more effective than making a stable component or other structure from scratch

When using external packages ensure that they aren't much larger than what we use them for. Lodash is a good example of this. If we only use a few functions from lodash it isn't worth the ~73KB it takes up when users first download our app.

Redux, however, would be a good example of a package that's worth the amount of space it takes up. We use it to handle our app state and I trust the robust usage/ testing that went into it's creation as well as the frequent updates it recieves more than a custom state management solution that we would make in house from scratch

## todo for readme and implementation

[ ] Add Redux
[ ] Setup auth
[ ] Setup firebase project
[ ] Navigation
[ ] Shared constants
[ ] Themes
[ ] Deploy scrips (minimum staging / production)
