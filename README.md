## redux-boilerplate  

Files structure:  
![redux_setup_structure](https://user-images.githubusercontent.com/29883334/120913128-4e981480-c6b2-11eb-9a1c-92d95361bd6c.PNG)


Step 1: create redux_store folder in src, create actions in redux_store/actions/
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

