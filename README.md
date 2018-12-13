npm install @material-ui/core

https://JSONplaceholder.typicode.com

REDUX
npm i redux react-redux redux-thunk

1.
write in App.js:

import { Provider } from 'react-redux'
import store from './store
class App extends Component {
  render() {
    return (
			<Provider store={ store }>
				<div>
					<NavBar />

					<Postform />
					<hr />
					<Posts />
				</div>
			</Provider>	
    );
  }
}

2.
write in store.js:

import { createStore, applyMiddleware } from 'redux'
import thunk from 'redux-thunk'
import rootReducer from './reducers' 
const initialState = {}
const middleware = [thunk]
const store = createStore(rootReducer, initialState, applyMiddleware(...middleware))
export default store

3.
add folder 'reducers'
write in index.js:

import { combineReducers } from 'redux'
import postReducer from './postReducer'
export default combineReducers({posts: postReducer})

4.
add folder actions
write in types.js

export const FETCH_POSTS = 'FETCH_POSTS';
export const NEW_POSTS = 'NEW_POSTS';

5.
write in postReducer:

import { FETCH_POSTS, NEW_POSTS } from '../actions/types'
const initialState = { items: [], item: {} }

export default function( state = initialState, action ) {
...
}

6.
write in postActions.js
delete state in Posts.js

7.
write in Posts.js
add { connect } from 'react-redux'
import { fetchPosts } from '../actions/postActions

8.
write in Posts.js
add mapStateToProps

9.
write in store.js
add devtools Redux extension
import compose

change createStore
const store = createStore( 
	rootReducer, 
	initialState,
	compose( 
		applyMiddleware(...middleware),
		window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
	)	 
)

10.
write in postActions
add const createPost

11. 
write in postReducer
add case NEW_POST

12.
write in Postform
connect store