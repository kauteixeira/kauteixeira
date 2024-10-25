my-cypress-project/
├── cypress/
│   ├── integration/
│   │   └── shopping.spec.js
│   ├── fixtures/
│   └── support/
├── package.json
└── README.md


// cypress/integration/shopping.spec.js

import { Given, When, Then } from "cypress-cucumber-preprocessor/steps";

Given('que estou na página inicial do Advantage Online Shopping', () => {
    cy.visit('https://advantageonlineshopping.com/#/');
});

When('eu busco pelo produto {string}', (produto) => {
    cy.get('#searchBar').type(produto);
    cy.get('#searchBtn').click();
});

Then('eu vejo uma lista de produtos relacionados a {string}', (produto) => {
    cy.get('.productList').should('be.visible');
    cy.get('.productList .product').should('have.length.greaterThan', 0);
});

When('eu seleciono um produto da lista', () => {
    cy.get('.productList .product').first().click();
});

When('eu clico no botão "Adicionar ao carrinho"', () => {
    cy.get('#buyButton').click();
});

Then('o produto deve ser adicionado ao carrinho', () => {
    cy.get('#cart').should('contain', '1 item');
});

Then('eu vejo uma mensagem de confirmação de que o produto foi adicionado', () => {
    cy.get('.confirm-message').should('be.visible');
});

When('eu navego até a tela de pagamento', () => {
    cy.get('#cart').click();
    cy.get('#checkout').click();
});

Then('eu vejo o produto listado na tela de pagamento', () => {
    cy.get('.checkout-product').should('be.visible');
});


# Projeto de Testes Automatizados - Advantage Online Shopping

## Tecnologias Utilizadas
- **BDD**: Cucumber
- **Linguagem**: JavaScript
- **Framework**: Cypress

## Pré-requisitos
- Node.js instalado
- NPM (gerenciador de pacotes do Node)

## Instalação do Ambiente

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seuusuario/my-cypress-project.git
   cd my-cypress-project

