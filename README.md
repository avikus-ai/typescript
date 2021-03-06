# Typescript Code Style Guideβ¨

<aside>
π‘ νλ‘κ·Έλλ¨Έλ νκ·  80%μ μκ°μ μ μ§λ³΄μμ μ¬μ©ν©λλ€. 
κ·Έλ¬λ―λ‘ μ½λλ₯Ό μ°λ κ² λ³΄λ€ μ½λλ₯Ό μ½λ κ²μ λ λ§μ λΉμ©μ΄ μλͺ¨λ©λλ€.
κ²°λ‘ μ μΌλ‘ μ½λλ₯Ό λͺ¨λ κ°μ μ€νμΌλ‘ ν΅μΌνμ¬ κ°λμ±μ λμ΄ μ¬λ €μΌνλ€λ κ²°μ μ νκ²λμμ΅λλ€.

</aside>

## κ°μ΄λμ μμ..

μ΅κ³ μ μ½λ μ€νμΌμ μ°λ¦¬κ° μ¬μ©νκΈ° νΈνκ³  μ°λ¦¬μ νλ‘μ νΈμ μ΅μ νλ μ€νμΌμλλ€.

μ°λ¦¬ λͺ¨λκ° μ¬μ©νκΈ° λλ¬Έμ μΈμ λ  μ€νμΌμ **μ μ**ν  μ μμ§λ§ λͺ¨λμ **ν©μ**κ° **νμμ **μλλ€.

ν©μμλ μ½λ μ€νμΌ μ μ©μ κΆλ ₯ μΈμμ μ§λμ§ μμ΅λλ€.

μ μκ³Ό ν©μ κ·Έλ¦¬κ³  ν΅μΌλ μ½λλ₯Ό ν΅ν΄ μ¦κ±°μμ μ°Ύμλ³΄μΈμ !!! π

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

- React Component, Class, interfaceλ `PascalCase` λ‘ μ μ΅λλ€.

  ```jsx
  //React Component
  export function WidgetButton() {...}

  //Class
  class Thing
  ```

- constants μ μμλ€μ `UPPER_CASE`λ‘ μ μ΅λλ€.

  ```tsx
  //constants/mipInfo.ts

  // BAD π
  export const MIP_INFO = {
    KEY: "value",
  };

  // GOOD π
  export const MIP_INFO = {
    key: "value",
    camelCase: true,
  };
  ```

- μ΄ μΈ λͺ¨λ  λ³μλ `camelCase` λ‘ μ μ΅λλ€.

  ```tsx
  // BAD π
  const UserInfo = {...}

  // GOOD π
  const userInfo = {...}
  ```

- μΆμ½μ΄λ λλ¬Έμλ‘ μ μ΅λλ€.

  ```tsx
  // BAD π
  const isEoCamera = true;
  const apiUrl = "https://...";

  // GOOD π
  const isEOCamera = true;
  const apiURL = "https://...";
  ```

- `boolean` νμμ λ³μλ λλλ‘ `is, has, can` μ λμ¬λ₯Ό λΆμλλ€.

  ```tsx
  // BAD π
  const enable = true;
  const loading = true;
  const nextItemCheck = true;

  // GOOD π
  const isEnabled = true;
  const isLoading = true;
  const hasNextItem = true;
  const canSubmit = true;
  ```

### If-else

- κ°λμ±μ μν΄ μ½λκ° 1μ€μ΄λλΌλ `{}` curly braces λ₯Ό μλ΅νμ§ μμ΅λλ€. λ¨, early returnμ κ²½μ°μ νν΄μλ§ `{}` μ μλ΅ν  μ μμ΅λλ€.

  ```jsx
  // BAD π
  if (condition) doSomething();

  // GOOD π
  if (condition) return;

  if (condition) {
    doSomething();
  }
  ```

- μ€μ²© `if`λ¬Έμ κ²½μ° `Guard Clause` λ₯Ό μ μ©ν©λλ€.
  `Guard Clause` λ₯Ό μ μ©νμ¬ μ½λλ₯Ό ννν μν΅λλ€.

  ```tsx
  // BAD π
  if (condition1) {
    if (condition2) {
      if (condition3) {
        return "κ½";
      }
    }
  }

  // GOOD π
  if (!condition1) {
    return;
  } //condition1μ΄ trueμμ΄ λ³΄μ₯λ¨
  if (!condition2) {
    return;
  } //condition2μ΄ trueμμ΄ λ³΄μ₯λ¨
  if (!condition3) {
    return;
  } //condition3μ΄ trueμμ΄ λ³΄μ₯λ¨
  return "κ½";
  ```

- `else`λ¬Έμ μ¬μ©νμ§ μμ΅λλ€.
  `else`λ¬Έμ μ¬μ©νμ§ μκ³  μμΈ κ²½μ°λ₯Ό λ³΄μ₯μν΅λλ€.

  ```tsx
  // BAD π
  if (isReady) {
    return "let's go";
  } else {
    return "stop";
  }

  // GOOD π
  if (isReady) {
    return "let's go";
  }
  return "stop";
  ```

### Padding lines

- ν¨μ returnλ¬Έ μ΄μ μ contentκ° μλ€λ©΄ `blank line`μ 1μ€ λ£μ΅λλ€.

  ```tsx
  // BAD π
  function numberOneMaker() {
    const one = 1;
    return one;
  }

  // GOOD π
  function numberOneMaker() {
    const one = 1;

    return one;
  }

  function numberOneMaker() {
    return 1;
  }
  ```

### Types

- `enum` λμ  `union`μ μ¬μ©ν©λλ€.

  ```tsx
  // BAD π
  enum CAMERA {
    eo = "EO",
    ir = "IR",
  }

  // GOOD π
  const CAMERA = {
    eo: "EO",
    ir: "IR",
  } as const;

  type Camera = typeof CAMERA[keyof typeof CAMERA]; // 'EO' | 'IR'
  ```

### Function

- ν¨μλ function μ μΈμ λμ  Arrow Functionμ μ¬μ©ν©λλ€.

  ```tsx
  // BAD π
  function doSomething() {...}
  export function Button() {...}

  // GOOD π
  const doSomething = () => {...}
  export const Button = () => {...}
  ```

---

## React / TSX Code Style Guide

<aside>
π‘ TSXλ Class Component λμ  λ°λμ Function Componentλ‘ μμ±ν©λλ€.

</aside>

### **Project Structure**

- _example_
  ```
  <project>
  	ββ .husky
  	ββ cypress
  	β   βββ fixtures
  	β   βββ integration
  	β   βββ plugins
  	β   βββ support
  	ββ public
  	β   βββ favicons
  	β       βββ favicon.ico
  	ββ src
  	β   βββ components          # componentsλ React Atomic Design μ λ°λ¦λλ€.
  	β       βββ icons
  	β 	  	βββ atoms
  	β	    βββ molecules
  	β	    βββ organisms
  	β		βββ templates
  	β	βββ pages
  	β	βββ styles
  	β		βββ theme.ts
  	β   βββ apis
  	β	βββ contexts             # (alternatively `store`)
  	β	βββ hooks               # Custom hooks
  	β       βββ useScript.ts
  	β	βββ utils
  	β       βββ makeQueryString.ts  #νκ°μ§ κΈ°λ₯λ§ μννλ μμ ν¨μ
  	β	βββ libs
  	β	    βββ sentry
  ```

### **Folder Naming**

- src/components νμ ν΄λλ `PascalCase` λ‘ μ μ΅λλ€. (λ¨, atomic design system folder μ μΈ)

  ```jsx
  // BAD π
  components / Atoms / Button / Button.tsx;
  components / atoms / button / Button.tsx;
  components / atoms / button / button.tsx;

  // GOOD π
  components / atoms / Button / Button.tsx;
  ```

### **File Naming**

- React Componentλ₯Ό μ μν νμΌμ `PascalCase` λ‘ μ μ΅λλ€.

  ```jsx
  // BAD π
  button.tsx;

  // GOOD π
  Button.tsx;
  ```

- React Componentλ₯Ό ν¬ν¨νκ³  μμ§ μλ€λ©΄ `.ts`λ₯Ό νμΌ νμ₯μλ‘ μ μ΅λλ€.

  ```jsx
  // BAD π
  theme.tsx;
  useScript.tsx;
  makeQueryString.tsx;

  // GOOD π
  theme.ts;
  useScript.ts;
  makeQueryString.ts;
  ```

- React Componentλ₯Ό μ μν νμΌκ³Ό Hookμ μ¬μ©ν νμΌμ μ μΈν λͺ¨λ  νμΌμ `kebab-case`λ‘ μ μ΅λλ€.

  ```tsx
  // BAD π
  makeQueryString.ts;

  // GOOD π
  make - query - string.ts;
  ```

  μ΄μ : macOSμμ νμΌ μ΄λ¦μ λμλ¬Έμλ₯Ό λ°κΎΈκ²λλ©΄ git μΆμ μ λ¬Έμ κ° μκΈ°κ³ , CI κ³Όμ μμ μ€ν¨ν  μ μκΈ° λλ¬Έμλλ€.

### Props Naming

- Propsλ₯Ό λκΈΈ λ `props` λ₯Ό μ΄λ¦μΌλ‘ νμ§ μμ΅λλ€.

  ```tsx
  // BAD π
  <Button
    props={{
      name: "confirm",
      onClick: onClickButton ,
    }}
  />

  // GOOD π
  <Button
    name="confirm"
    onClick={onClickButton}
  />

  // BAD π
  [...].map((item) => {
    return (
      <ListItem props={item} />
    )
  }

  // GOOD π
  [...].map((item) => {
    return (
      <ListItem item={item} />
    )
  }

  ```

- Props type μ `μ»΄ν¬λνΈ μ΄λ¦ + Props` λ‘ μ μν©λλ€.
  λ³΅μ‘ν μ°μ°μ΄ μλ€λ©΄ `type` λμ  `interface` λ₯Ό μ¬μ©ν©λλ€.

  ```tsx
  // BAD π
  interface Props {...}

  // GOOD π
  interface ButtonProps {...}
  ```

- Chakra-UI propsλ μΆμ½μ΄λ₯Ό μ°μ§ μμ΅λλ€.

  ```tsx
  // BAD π
  <Box
    w="10px"
    h="10px"
    mx="1px"
    pb="10px"
  />

  // GOOD π
  <Box
    width="10px"
    height="10px"
    marginX="1px"
    paddingBottom="10px"
  />

  ```

### Component Definition

- `index.ts` νμΌμλ μ»΄ν¬λνΈ λ₯Ό μ μνμ§ μμ΅λλ€.
  index.ts μμλ import, export λ§ μ μν©λλ€.

  ```tsx
  // Button/index.ts

  import { Button } from "./Button.tsx";

  export { Button } from "./Button.tsx";
  ```

- ν νμΌμλ νλμ μ»΄ν¬λνΈ λ§ μ μν©λλ€.

  ```tsx
  // Button.tsx

  // BAD π
  export const Button = () => {...}
  export const ButtonWrapper = () => {...}

  // GOOD π
  export const Button = () => {...}
  ```

### Component Layout

- μ»΄ν¬λνΈμ μ΅μμ μμλ `margin, padding, position` μ κ°μ§μ§ μμ΅λλ€.
  _λ¨, νλλ¦¬κ° μλ€λ©΄ `padding` μ κ°μ§ μλ μμ΅λλ€._
  _λν μμ μμμ `positioning` μ μ΄μ λ‘ `position` μ κ°μ§ μλ μμ΅λλ€._
  μ¬μ©νλ κ³³μμ λν ν λν μμμ `margin, position` μ μ μ©ν©λλ€.

  ```tsx
  // BAD π
  export const LoginButton = () => {
    return (
      <Button margin="0 auto" position="absolute">
        {...}
      </Button>
    )
  }

  // NOT BAD π  # λΆκ°νΌν κ²½μ°μλ§ νμ©!
  // μμ)
  export const LoginForm = () => {
    return (
      <Form>
        <LoginButton margin="0 2px"/>
      </Form>
    )
  }

  // GOOD π
  export const LoginForm = () => {
    return (
      <Box margin="0 auto" position="absolute">
        <LoginButton />
      </Box>
    )
  }
  ```

### Destructuring assignment

- κ°λμ±μ μν΄ `Destructuring assginment` ν©λλ€.

  ```tsx
  // BAD π
  <Text>{`${props.name}λμ λμ΄λ ${props.age}μλλ€.`}</Text>;

  // GOOD π
  const { name, age } = props;

  <Text>{`${name}λμ λμ΄λ ${age}μλλ€.`}</Text>;
  ```
