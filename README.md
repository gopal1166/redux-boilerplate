## redux-boilerplate  

Files structure:  
![redux_setup_structure](https://user-images.githubusercontent.com/29883334/120913128-4e981480-c6b2-11eb-9a1c-92d95361bd6c.PNG)


Step 1: create `redux_store` folder in src, create actions in `redux_store/actions/counterActions.js`
```
export const incrementCount = () => {
  return {
    type: "INCREMENT_COUNT"
  }
}

export const decrementCount = () => {
  return {
    type: "DECREMENT_COUNT"
  }
}
```  

Step 2: create reduces in `redux_store/reducers/counterReducers.js`
```
let initialState = {
  count: 0
}

export const updateCount = (state=initialState, action) => {
  switch (action.type) {
    case 'INCREMENT_COUNT':
      return {
        ...state,
        count: state.count + 1 
      }
      break;
      case 'DECREMENT_COUNT':
        return {
          ...state,
          count: state.count - 1 
        }
        break;
    default:
      return {
        ...state
      }
      break;
  }
  return state
}
```  

Step 3: create a store.js file under redux-store folder  
```
import { combineReducers, createStore } from "redux";
import {updateCount} from './reducers/counterReducers'

export const store = createStore(
  updateCount,
  window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
)
```  

Step 4: in index.js file, wrap App with Provdier  
```
import React from 'react'
...
import {Provider} from 'react-redux'
import {store} from './redux_store/store'

ReactDOM.render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);
...
```

Step 5: use the store in componet, dispatch actions from component  
using `useSelector, useDispatch hooks`
```
import { useSelector, useDispatch } from 'react-redux';
import { incrementCount, 
  decrementCount } from './redux_store/actions/counterActions';


function App() {
  const count = useSelector(state => state.count)
  const dispatch = useDispatch()
  return (
    <div className="App">
      count: {count} <br></br>
      <button onClick={() => dispatch(decrementCount())} >-</button>
      <button onClick={() => dispatch(incrementCount())} >+</button>
    </div>
  );
}

export default App;
```



















