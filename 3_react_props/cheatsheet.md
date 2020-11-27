# React With Typescript (cheatsheet)

* Prop Types
* function component
* conditional rendering
* event
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
const Title: React.FC<{ title: string }> = ({
  children,
  title,
}) => <div title={title}>{children}</div>;

```

## Conditional rendering

```javascript
const Mailbox: React.FC<{unreadMessages: Message[]> = ({unreadMessages}) => {
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}

```

## Events

```javascript
onClick(event: React.MouseEvent<HTMLButtonElement>): void => {
  //code
}
```

```javascript
onChange: React.ChangeEventHandler<HTMLInputElement> = (e) => {
  //code
}
```

## loop need key

```javascript
{items.map(item => (
  <li key={item.id}>
  </li>
))}

```

```javascript
{items.map((item, index) => (
  <li key={index}>
  <li/>
))}
```

## Styling component CSS


### Install Bulma CSS

```bash
yarn add bulma
```

```javascript
import 'bulma/css/bulma.css'
```

if you need to customize, use node sass version

```javascript
// not yet compatible with 5, 
yarn add node-sass@4  
```

Customization with sass example

```javascript
//app.tsx (for example)
import './mybulma.sass'
```

```javascript
//mybulma.sass

@charset "utf-8";

// Import a Google Font
@import url('https://fonts.googleapis.com/css?family=Nunito:400,700');

// Set your brand colors
$purple: #8A4D76;
$pink: #FA7C91;
$brown: #757763;
$beige-light: #D0D1CD;
$beige-lighter: #EFF0EB;

// Update Bulma's global variables
$family-sans-serif: "Nunito", sans-serif;
$grey-dark: $brown;
$grey-light: $beige-light;
$primary: $purple;
$link: $pink;
$widescreen-enabled: false;
$fullhd-enabled: false;

// Update some of Bulma's component variables
$body-background-color: $beige-lighter;
$control-border-width: 2px;
$input-border-color: transparent;
$input-shadow: none;

// Import only what you need from Bulma
@import "../node_modules/bulma/sass/utilities/_all.sass";
@import "../node_modules/bulma/sass/base/_all.sass";
@import "../node_modules/bulma/sass/elements/button.sass";
@import "../node_modules/bulma/sass/elements/container.sass";
@import "../node_modules/bulma/sass/elements/title.sass";
@import "../node_modules/bulma/sass/form/_all.sass";
@import "../node_modules/bulma/sass/components/navbar.sass";
@import "../node_modules/bulma/sass/layout/hero.sass";
@import "../node_modules/bulma/sass/layout/section.sass";
```

## Storybook

```
npx sb init
```

or 

```bash
npx -p @storybook/cli@next sb init
```


Error with babel 8.1 required by react vs 8.2 storybook

```bash
yarn add babel-loader@8.1
```

