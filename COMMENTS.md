# Comments

DRAFT

Good code should be self-explanatory and easy to read, potentially regardless the seniority of the reader.

Due to the previous assumption comments should be reduced to the minimun and used only to explain what is not understandable just reading the code.

## Unconventional choices driven by third party or temporary situation

> Good

```js
// An existing bug in the fecth method requires the usage of the fetchWithRetry.
// More info https://github.com/facebookincubator/create-react-app/issues/1023#issuecomment-265344421

myCode.fetchWithRetry(...);
```

## Style

Comments are part of the code so their styles should consistent across the codebase and enforce elegance. 

> Bad

```js
// this is a comment
```

> Good

```js
// This is a more elegant comment.
```

## Uselfulness

Comments shouldn't describe what the code does. In that case they are useless and redundant. 

> Bad

```js
// Looping through the article list.
articles.forEach((article) => ...);
```
In some cases, some coding choices deserve an explanation and additional external references to track for future refactoring.
> Good

```js
someHandler(event) {
  // Prevent Safari to execute the default event.
  // https://github.com/EconomistDigitalSolutions/fe-blogs/issues/1806
  event.preventDefault();
  return somethingElse();
}

```

