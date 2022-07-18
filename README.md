# Typescript Code Style Guide✨

<aside>
💡 프로그래머는 평균 80%의 시간을 유지보수에 사용합니다. 
그러므로 코드를 쓰는 것 보다 코드를 읽는 것에 더 많은 비용이 소모됩니다.
결론적으로 코드를 모두 같은 스타일로 통일하여 가독성을 끌어 올려야한다는 결정을 하게되었습니다.

</aside>

## 가이드에 앞서..

최고의 코드 스타일은 우리가 사용하기 편하고 우리의 프로젝트에 최적화된 스타일입니다.

우리 모두가 사용하기 때문에 언제든 스타일을 **제안**할 수 있지만 모두의 **합의**가 **필수적**입니다.

합의없는 코드 스타일 적용은 권력 싸움에 지나지 않습니다.

제안과 합의 그리고 통일된 코드를 통해 즐거움을 찾아보세요 !!! 😇

---

## Table of Contents

1. [Typescript Code Style Guide](#typescript-code-style-guide)
   1.1 [Variables](#variables)
   1.2 [If-else](#if-else)
   1.3 [Padding lines](#padding-lines)
   1.4 [Types](#types)
   1.5 [Function](#function)
2. [React/TSX Code Style Guide](#react/tsx-code-style-guide)
   2.1 [Project structure](#project-structure)
   2.2 [Folder naming](#folder-naming)
   2.3 [File naming](#file-naming)
   2.4 [Component definition](#component-definition)
   2.5 [Component layout](#component-layout)
   2.6 [Destructuring assignment](#destructuring-assignment)

---

## Typescript Code Style Guide

### Variables

- React Component, Class, interface는 `PascalCase` 로 적습니다.

  ```jsx
  //React Component
  export function WidgetButton() {...}

  //Class
  class Thing
  ```

- constants 의 상수들은 `UPPER_CASE`로 적습니다.

  ```tsx
  //constants/mipInfo.ts

  // BAD 👎
  export const MIP_INFO = {
    KEY: "value",
  };

  // GOOD 👍
  export const MIP_INFO = {
    key: "value",
    camelCase: true,
  };
  ```

- 이 외 모든 변수는 `camelCase` 로 적습니다.

  ```tsx
  // BAD 👎
  const UserInfo = {...}

  // GOOD 👍
  const userInfo = {...}
  ```

- 축약어는 대문자로 적습니다.

  ```tsx
  // BAD 👎
  const isEoCamera = true;
  const apiUrl = "https://...";

  // GOOD 👍
  const isEOCamera = true;
  const apiURL = "https://...";
  ```

- `boolean` 타입의 변수는 되도록 `is, has, can` 접두사를 붙입니다.

  ```tsx
  // BAD 👎
  const enable = true;
  const loading = true;
  const nextItemCheck = true;

  // GOOD 👍
  const isEnabled = true;
  const isLoading = true;
  const hasNextItem = true;
  const canSubmit = true;
  ```

### If-else

- 가독성을 위해 코드가 1줄이더라도 `{}` curly braces 를 생략하지 않습니다. 단, early return의 경우에 한해서만 `{}` 을 생략할 수 있습니다.

  ```jsx
  // BAD 👎
  if (condition) doSomething();

  // GOOD 👍
  if (condition) return;

  if (condition) {
    doSomething();
  }
  ```

- 중첩 `if`문의 경우 `Guard Clause` 를 적용합니다.
  `Guard Clause` 를 적용하여 코드를 평탄화 시킵니다.

  ```tsx
  // BAD 👎
  if (condition1) {
    if (condition2) {
      if (condition3) {
        return "꽝";
      }
    }
  }

  // GOOD 👍
  if (!condition1) {
    return;
  } //condition1이 true임이 보장됨
  if (!condition2) {
    return;
  } //condition2이 true임이 보장됨
  if (!condition3) {
    return;
  } //condition3이 true임이 보장됨
  return "꽝";
  ```

- `else`문을 사용하지 않습니다.
  `else`문을 사용하지 않고 예외 경우를 보장시킵니다.

  ```tsx
  // BAD 👎
  if (isReady) {
    return "let's go";
  } else {
    return "stop";
  }

  // GOOD 👍
  if (isReady) {
    return "let's go";
  }
  return "stop";
  ```

### Padding lines

- 함수 return문 이전에 content가 있다면 `blank line`을 1줄 넣습니다.

  ```tsx
  // BAD 👎
  function numberOneMaker() {
    const one = 1;
    return one;
  }

  // GOOD 👍
  function numberOneMaker() {
    const one = 1;

    return one;
  }

  function numberOneMaker() {
    return 1;
  }
  ```

### Types

- `enum` 대신 `union`을 사용합니다.

  ```tsx
  // BAD 👎
  enum CAMERA {
    eo = "EO",
    ir = "IR",
  }

  // GOOD 👍
  const CAMERA = {
    eo: "EO",
    ir: "IR",
  } as const;

  type Camera = typeof CAMERA[keyof typeof CAMERA]; // 'EO' | 'IR'
  ```

### Function

- 함수는 function 선언식 대신 Arrow Function을 사용합니다.

  ```tsx
  // BAD 👎
  function doSomething() {...}
  export function Button() {...}

  // GOOD 👍
  const doSomething = () => {...}
  export const Button = () => {...}
  ```

---

## React / TSX Code Style Guide

<aside>
💡 TSX는 Class Component 대신 반드시 Function Component로 작성합니다.

</aside>

### **Project Structure**

- _example_
  ```
  <project>
  	├─ .husky
  	├─ cypress
  	│   ├── fixtures
  	│   ├── integration
  	│   ├── plugins
  	│   └── support
  	├─ public
  	│   └── favicons
  	│       └── favicon.ico
  	├─ src
  	│   ├── components          # components는 React Atomic Design 에 따릅니다.
  	│       ├── icons
  	│ 	  	├── atoms
  	│	    ├── molecules
  	│	    ├── organisms
  	│		└── templates
  	│	├── pages
  	│	├── styles
  	│		└── theme.ts
  	│   ├── apis
  	│	├── contexts             # (alternatively `store`)
  	│	├── hooks               # Custom hooks
  	│       └── useScript.ts
  	│	├── utils
  	│       └── makeQueryString.ts  #한가지 기능만 수행하는 순수 함수
  	│	└── libs
  	│	    └── sentry
  ```

### **Folder Naming**

- src/components 하위 폴더는 `PascalCase` 로 적습니다. (단, atomic design system folder 제외)

  ```jsx
  // BAD 👎
  components / Atoms / Button / Button.tsx;
  components / atoms / button / Button.tsx;
  components / atoms / button / button.tsx;

  // GOOD 👍
  components / atoms / Button / Button.tsx;
  ```

### **File Naming**

- React Component를 정의한 파일은 `PascalCase` 로 적습니다.

  ```jsx
  // BAD 👎
  button.tsx;

  // GOOD 👍
  Button.tsx;
  ```

- React Component를 포함하고 있지 않다면 `.ts`를 파일 확장자로 적습니다.

  ```jsx
  // BAD 👎
  theme.tsx;
  useScript.tsx;
  makeQueryString.tsx;

  // GOOD 👍
  theme.ts;
  useScript.ts;
  makeQueryString.ts;
  ```

- React Component를 정의한 파일과 Hook을 사용한 파일을 제외한 모든 파일은 `kebab-case`로 적습니다.

  ```tsx
  // BAD 👎
  makeQueryString.ts;

  // GOOD 👍
  make - query - string.ts;
  ```

  이유: macOS에서 파일 이름의 대소문자를 바꾸게되면 git 추적에 문제가 생기고, CI 과정에서 실패할 수 있기 때문입니다.

### Props Naming

- Props를 넘길 때 `props` 를 이름으로 하지 않습니다.

  ```tsx
  // BAD 👎
  <Button
    props={{
      name: "confirm",
      onClick: onClickButton ,
    }}
  />

  // GOOD 👍
  <Button
    name="confirm"
    onClick={onClickButton}
  />

  // BAD 👎
  [...].map((item) => {
    return (
      <ListItem props={item} />
    )
  }

  // GOOD 👍
  [...].map((item) => {
    return (
      <ListItem item={item} />
    )
  }

  ```

- Props type 은 `컴포넌트 이름 + Props` 로 정의합니다.
  복잡한 연산이 없다면 `type` 대신 `interface` 를 사용합니다.

  ```tsx
  // BAD 👎
  interface Props {...}

  // GOOD 👍
  interface ButtonProps {...}
  ```

- Chakra-UI props는 축약어를 쓰지 않습니다.

  ```tsx
  // BAD 👎
  <Box
    w="10px"
    h="10px"
    mx="1px"
    pb="10px"
  />

  // GOOD 👍
  <Box
    width="10px"
    height="10px"
    marginX="1px"
    paddingBottom="10px"
  />

  ```

### Component Definition

- `index.ts` 파일에는 컴포넌트 를 정의하지 않습니다.
  index.ts 에서는 import, export 만 정의합니다.

  ```tsx
  // Button/index.ts

  import { Button } from "./Button.tsx";

  export { Button } from "./Button.tsx";
  ```

- 한 파일에는 하나의 컴포넌트 만 정의합니다.

  ```tsx
  // Button.tsx

  // BAD 👎
  export const Button = () => {...}
  export const ButtonWrapper = () => {...}

  // GOOD 👍
  export const Button = () => {...}
  ```

### Component Layout

- 컴포넌트의 최상위 요소는 `margin, padding, position` 을 가지지 않습니다.
  _단, 테두리가 있다면 `padding` 을 가질 수도 있습니다._
  _또한 자식 요소의 `positioning` 의 이유로 `position` 을 가질 수도 있습니다._
  사용하는 곳에서 래핑 후 래핑 요소에 `margin, position` 을 적용합니다.

  ```tsx
  // BAD 👎
  export const LoginButton = () => {
    return (
      <Button margin="0 auto" position="absolute">
        {...}
      </Button>
    )
  }

  // NOT BAD 👏  # 불가피한 경우에만 허용!
  // 예시)
  export const LoginForm = () => {
    return (
      <Form>
        <LoginButton margin="0 2px"/>
      </Form>
    )
  }

  // GOOD 👍
  export const LoginForm = () => {
    return (
      <Box margin="0 auto" position="absolute">
        <LoginButton />
      </Box>
    )
  }
  ```

### Destructuring assignment

- 가독성을 위해 `Destructuring assginment` 합니다.

  ```tsx
  // BAD 👎
  <Text>{`${props.name}님의 나이는 ${props.age}입니다.`}</Text>;

  // GOOD 👍
  const { name, age } = props;

  <Text>{`${name}님의 나이는 ${age}입니다.`}</Text>;
  ```
