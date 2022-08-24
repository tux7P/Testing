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

FakerJS comes to your aid by dynamically generating as much data as you want to test. 

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
