# Redux/Redux Toolkit: Best Practices
#### author: Abraham Lawson

[![](https://redux.js.org/img/redux-logo-landscape.png)](https://redux.js.org/style-guide/style-guide)

## Overview

* After a while with redux as well as redux-toolkit, I realize that using redux is simple, but using redux in the most efficient way is a different story. So I think I need to take note of what I have learned from my experience as well as read from other documents. 
* On the other hand, that will help me improve myself. It is important to me not simply whether your application works or not, but rather that the application must be highly maintainable.
 
````
Both the Redux core library and most of the Redux documentation are unopinionated. There are many ways to use Redux, and much of the time there is no single "right" way to do things.
````

> If you feel something is not going well here, please let me know.

## Redux Style Guide


## Redux-Toolkit Best Practices

**``createEntityAdapter``  (Strong recommend)**

A function that generates a set of prebuilt reducers and selectors for performing CRUD operations on a normalized state structure containing instances of a particular type of data object.

**Example**

````javascript
import {
    createEntityAdapter,
    createSlice,
    configureStore,
} from '@reduxjs/toolkit'

const booksAdapter = createEntityAdapter({
    // Assume IDs are stored in a field other than `book.id`
    selectId: (book) => book.bookId,
    // Keep the "all IDs" array sorted based on book titles
    sortComparer: (a, b) => a.title.localeCompare(b.title),
})

const initField = {
    isLoading: false,
    error: null,
}

const initialState = booksAdapter.getInitialState(initField)

const booksSlice = createSlice({
    name: 'books',
    initialState,
    reducers: {},
    extraReducers: (builder) => {}
})

const { actions, reducer } = booksSlice

export const {} = actions

export default reducer

// Selector Function
const booksSelectors = booksAdapter.getSelectors((state) => state.books)
const allBooks = booksSelectors.selectAll(store.getState())
export 
````
**CRUD functions**

* addMany: ````bookAdater.addMany(state, data)```` .
````javascript
data  
````
