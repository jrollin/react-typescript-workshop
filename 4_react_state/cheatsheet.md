# React State (cheatsheet)

## states vs props

* props : color
* state : time


## Class Component

```javascript
type MyProps = {
  // using `interface` is also ok
  message: string;
};
type MyState = {
  count: number; // like this
};
class App extends React.Component<MyProps, MyState> {
  state: MyState = {
    // optional second annotation for better type inference
    count: 0,
  };
  render() {
    return (
      <div>
        {this.props.message} {this.state.count}
      </div>
    );
  }
}

```

## Hooks 

### UseState

```javascript
const [article, setArticle] = React.useState<IArticle | null>(null);

// later
setArticle(newArticle);

```

### UseEffect


```javascript
const App = () => {
  const [isOn, setIsOn] = useState(false);
  const [timer, setTimer] = useState(0);
  useEffect(
    () => {
      let interval;
      if (isOn) {
        interval = setInterval(() => setTimer(timer => timer + 1), 1000);
      }
      return () => clearInterval(interval);
    },
    [isOn]
  );
  const onReset = () => {
    setIsOn(false);
    setTimer(0);
  };
  return (
    <>
      Timer: {timer}
      {!isOn && (<button onClick={() => setIsOn(true)}>Start</button>)}
      {isOn && (<button onClick={() => setIsOn(false)}>Stop</button>)}
      <button disabled={timer === 0} onClick={onReset}>Reset</button>
    </>
  );
};

```

Note:  Typescript screams when await.async in useEffect

```javascript
const MyFunctionnalComponent: React.FC = props => {
  useEffect(() => {
    // Create an scoped async function in the hook
    async function anyNameFunction() {
      await loadContent();
    }    // Execute the created function directly
    anyNameFunction();
  }, []);
  
  return <div></div>;
};


```
### UseReducer


Beware : different types for `payload` in this example

```javascript
const initialState = { count: 0 };

type ACTIONTYPE =
  | { type: "increment", payload: number }
  | { type: "decrement", payload: string };

function reducer(state: typeof initialState, action: ACTIONTYPE) {
  switch (action.type) {
    case "increment":
      return { count: state.count + action.payload };
    case "decrement":
      return { count: state.count - Number(action.payload) };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = React.useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: "decrement", payload: "5" })}>
        -
      </button>
      <button onClick={() => dispatch({ type: "increment", payload: 5 })}>
        +
      </button>
    </>
  );
}
```

