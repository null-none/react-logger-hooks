# react-logger-hooks

## Usage

```jsx
import { useReducer } from 'react-logger-hooks';

function reducer(state, action) {
  switch (action.type) {
    case 'count-up':
      return { count: state.count + action.payload.count }

    case 'count-down':
      return { count: state.count - action.payload.count }
  }
}
const initialState = { count: 0 };

const Demo = () => {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <button
        onClick={() =>
          dispatch({
            type: "count-up",
            payload: { count: 1 }
          })
        }
      >
        +
      </button>
      <button
        onClick={() =>
          dispatch({
            type: "count-down",
            payload: { count: 1 }
          })
        }
      >
        -
      </button>
      count: {state.count}
    </div>
  );
};
```

## Dev Environment
Create custom hooks.
```jsx
import { useReducer as _useReducer } from 'react';
import { useReducer as useReducerWithLog } from ''react-logger-hooks';

export const useMyReducer = 
  process.env.NODE_ENV === 'development' ? useReducerWithLog : _useReducer;
```