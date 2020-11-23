# React With Typescript (cheatsheet)

* Prop Types
* function component
* conditional rendering
* styling
* storybook


## Prop Types


```javascript
Common prop Types 

type AppProps = {
  message: string;
  count: number;
  disabled: boolean;
  /** array of a type! */
  names: string[];
  /** string literals to specify exact string values, with a union type to join them together */
  status: "waiting" | "success";
  /** any object as long as you dont use its properties (NOT COMMON but useful as placeholder) */
  obj: object;
  obj2: {}; // almost the same as `object`, exactly the same as `Object`
  /** an object with any number of properties (PREFERRED) */
  obj3: {
    id: string;
    title: string;
  };
  /** array of objects! (common) */
  objArr: {
    id: string;
    title: string;
  }[];
  /** a dict object with any number of properties of the same type */
  dict1: {
    [key: string]: MyTypeHere;
  };
  dict2: Record<string, MyTypeHere>; // equivalent to dict1
  /** any function as long as you don't invoke it (not recommended) */
  onSomething: Function;
  /** function that doesn't take or return anything (VERY COMMON) */
  onClick: () => void;
  /** function with named prop (VERY COMMON) */
  onChange: (id: number) => void;
  /** alternative function type syntax that takes an event (VERY COMMON) */
  onClick(event: React.MouseEvent<HTMLButtonElement>): void;
  /** an optional prop (VERY COMMON!) */
  optional?: OptionalType;
};
```


JSX.Element -> Return value of React.createElement
React.ReactNode -> Return value of a component


## Function Component

### Message component

Without TS:

```javascript
type MessageProps = { message: string }; // can be an interface too
const Message = ({ message }: MessageProps) => <div>{message}</div>;
```

With TS 

```javascript
const Message: React.FC<{ message: string }> = ({ message }) => (
  <div>{message}</div>
);
```

### Title component With Children

```javascript
const Title: React.FunctionComponent<{ title: string }> = ({
  children,
  title,
}) => <div title={title}>{children}</div>;

```

## Children


## Conditional rendering



## Events

```javascript
onClick(event: React.MouseEvent<HTMLButtonElement>): void;
```

```javascript
onChange: React.ChangeEventHandler<HTMLInputElement> = (e) => {
this.setState({text: e.currentTarget.value})
}
```

## Styling component CSS


### Install Bulma CSS

```bash
yarn add bulma
// not yet compatible with 5, 
yarn add node-sass@4  
```

## react testing lib


## Storybook


```bash
// storybook with ts
npx sb@next init --story-format=csf-ts
```

// npx sb init not working for me...
npx -p @storybook/cli@next sb init