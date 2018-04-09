# E2E tips

## PageObjects philosophy

As plain as possible. Two criteria to extend pageObjects beyond retrieving DOM elements:

1) Something is done LOTS of times

2) It generates LOTS of codelines.


## Method base PageObject

Always use methods to retrieve DOM elements so we always get an updated version on element (and prevents referencing stale elements)

Avoid:

```ts

class AppPage {
  public submitButton;
  
  constructor() {
    this.submitButton = element(by.className('login-btn');
   }
}

```

Prefer:

```ts

class AppPage {
  constructor() {}
  
  getSubmitButton() {
    return element(by.className('login-btn'));
  }
}
```

# Protractor tips

## Wait until element doesn't exists

Use ExpectedConditions:

```ts
  let loadingSpinner = element(by.className('spinner'));
  browser.wait(ExpectedConditions.not(ExpectedConditions.presenceOf(loadingSpinner)), 15000, 'Loading too slow.');
```



