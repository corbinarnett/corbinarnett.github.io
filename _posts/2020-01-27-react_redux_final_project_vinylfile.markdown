---
layout: post
title:      "React/Redux Final Project: vinylFile"
date:       2020-01-28 00:23:42 +0000
permalink:  react_redux_final_project_vinylfile
---


The final modual in the Flatiron School Curriculm in my experience was the most difficult but also the most rewarding. 

Redux is a beast, it brings with it new vocabulary, extensive wiring from file to file, and a flow that must be understood. But once these are learned I saw how fascinating Redux really is and the benefits of having a global object to maintain state of the application.

Redux has three main parts: 
1. Store
2. Actions
3. Reducers

### Store
The store is what holds the applications state, but what is state? State is a single javascript object that contains everything that changes in an application this includes dat and the UI.

Store lets you dispatch actions and when you create the store you need to specify the reducer that tells how state is updated with actions. 

### Actions 

An Action in Redux is a plain JavaScript object, these action are "dispatched" or sent to the store whenever we want to update the state of the application.  The only requirement for this action object is that it has a "type" key, this describes that action that we are dispatching. 
In line with Actions we also have 'Action Creators' which allow us to abstract more complex data and logic in our Actions.

```
export function fetchAlbums() {
  return (dispatch) => {
    fetch('http://localhost:3000/api/v1/albums')
    .then(resp => resp.json())
    .then(albums => dispatch({
      type: 'FETCH_ALBUMS',
      payload: albums
    }))
  }
}
```
Above is an example of an Action Creator within my application, its purpose is to send an asynchronous request to the backend and update the store with all the albums in the database, this Action Creator is dispatched like so:
```
componentDidMount() {
    this.props.fetchAlbums();
  }
```

### Reducers
Reducers are functions that describe how the appication state will change.  We dispatch an action object to our reducer and our reducer is responsible for taking in that action and deciding based on its type field what we want to update about our current store.  A reducer takes in the previous state as its first argument and an action object as it's second. Inside the reducer we will update the state according to the action type. Here is an example of a reducer in my application:
```
export default function rootReducer(state = { albums: [] }, action) {
 
  switch (action.type) {
    case "FETCH_ALBUMS":
      return { albums: action.payload };
  }
```
I like to to think of reducers as the middle-man between my store and actions. If we dispatched the action called fetchAlbums defined previously, the action would be passed to the reducer and based on the action type update the store accordingly, here we would update the store with all the albums from the async request.


### Final Thoughts

At first this project was daunting, but was a tipping point in cementing my understanding of Redux. I look forward to building bigger and better applications in the near future with it as well as adding more features to the current iteration of my final application.
