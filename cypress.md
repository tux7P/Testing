### Folder structure for projects with UI & API tests
### Naming conventions for folders, files, classes, methods and variables
### 3rd party libraries
- ESLint
- Prettier
- Husky
- Commitzen or commitlint
- Cypress Testing Library
- Cypress Xpath
- FakerJS


#### FakerJS

When writing tests, you generate a large amount of unique data (e.g. usernames). Setting up new data every single time before starting testing won’t do anymore, we’re IT, and we’re not wasting time like that. Fortunately, FakerJS comes to your aid by dynamically generating as much data as you want to test. 

```
const { faker } = require('@faker-js/faker');

describe('Faker test', () => {
  Cypress._.times(3, () => {
    it(`Test #1`, () => {
      cy.visit('http://uiplayground.in/main/');
      cy.get('#frmName').type(faker.name.firstName());
      cy.get('#frmEmail').type(faker.name.lastName());
      cy.get('#frmComments').type(faker.lorem.sentence(10));
    });
  });
});
```

#### Cypress-iframe

Working with iframes is extremely hard and tedious but the Cypress-iframe library will help by making tests more stable and pleasant to implement.

```
///<reference types="cypress-iframe" />
import 'cypress-iframe';

describe('Iframe Test', () => {
  it(`Test iframe`, () => {
    cy.visit('https://www.w3schools.com/html/html_iframe.asp');
    cy.frameLoaded('iframe[title="W3Schools HTML Tutorial"]');
    cy.iframe('iframe[title="W3Schools HTML Tutorial"]').should('be.visible');
    cy.iframe('iframe[title="W3Schools HTML Tutorial"]').find('#submitBtn').should('be.visible').click();
  });
});
```

#### Cypress-lighthouse

Even the best application’s UX can be spoiled by poor performance. To avoid this, it is worth keeping eye on it, and since your tests are running anyway, it’s a perfect opportunity to check performance. Two birds with one stone. In addition, you can also check PWA, SEO, and whether good practices on the frontend. The icing on the cake is the ability to verify accessibility. 

```
import 'cypress-lighthouse';

describe('Lighthouse Test', () => {
  it('Test #1', () => {
    cy.visit('https://www.w3schools.com');
    cy.lighthouse('https://www.w3schools.com').then((result) => {
      cy.log(JSON.stringify(result));
    });
  });
});
```
