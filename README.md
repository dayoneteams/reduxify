# reduxify
Makes useReducer hooks to be cooler with thunk, middleware, ... just as Redux, without having to use react-redux
IMPORTANT: Development is STILL EARLY-STAGE ON-GOING. Suggestions are all always welcomed!

# Usage
Assuming that you're gonna use useReducer + Context API to replace Redux, global state is stored in ValueContainer.
Then your code will looks like below (my opinionated idea):
```js
const reducer = ({type, payload}) => {
  switch case LOGIN_SUCCESS / LOGOUT
}
const Container = () => {
  const [loginUser, defaultDispatch] = useReducer(reducer, null);
  const dispatch = reduxify(counter, defaultDispatch, [redux middlewares (e.g: thunk)]);
  
  const login = ({email, password}) => async (dispatch, getState) => {
    const loginUser = await authService.login(email, password);
    dispatch({type: 'LOGIN_SUCCESS', payload: loginUser});
    return loginUser;
  }
  
  return (
    <div>
      // Login form ...
      <button onClick={() => dispatch(login({email: ..., password: ...}))}>Login</button>
    </div>
  );
}
```
