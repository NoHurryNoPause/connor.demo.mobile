# Redux base imports

## compose

    Combines the reducers to talk to one another within the client side state tree

## createStore

    Creates the *store* or local state tree

## applyMiddleware

    Any injections that we want to have for our local state such as loggers, persistance, and analytics will be set within the middleware

# Redux-Persist

## This persists the local state between sessions

## Important note

If you have an issue where new additions to a particular reducer aren't being set properly this is likely redux-persist overwriting the state tree with what it previously was
If you want to clean out the reducers use `persistor.purge();` in ./redux/index.js to clear out any previous persisted reducers
