/// <reference types="cypress" />

describe('Salsa', ()  => {

  it('1. Acessar http://zero.webappsecurity.com/', () => {
      Cypress.config('chromeWebSecurity', true);
      cy.visit({
          url: 'http://zero.webappsecurity.com/',
          method: 'GET'
        })  

  });
  
  it('2. Realizar login na plataforma (usuário: username | senha: password)', () => {
      cy.get('#signin_button').click();
      cy.get('#user_login').type('username');
      cy.get('#user_password').type('password');
      cy.get('.btn').click();


  });

  it('3. Acessar a aba “Pay Bills”', () => {
    cy.get('#onlineBankingMenu > div > strong').click();
    cy.get('#pay_bills_link').click();
   
  });

  it('5. Realizar um pagamento e validar a mensagem de sucesso”', () => {
    cy.get('id="sp_amount"').type('500');
    cy.get('id="sp_date"').type('2022-08-02');
    cy.get('id="sp_description"').type('PAY');
    cy.get('id="pay_saved_payees"').click();
    cy.contains('The payment was successfully submitted.');
   
  });


  it('6. Acessar a aba “Account Activity” e “Find Transactions”', () => {
    cy.get('id="account_activity_tab"').click();
    cy.get('xpath=//*[@id="tabs"]/ul/li[2]/a"').click();
   
  });

  it('7. Preencher os campos Dates com data do dia 04/09/2012 até dia 06/09/2012', () => {
    cy.get('id="aa_fromDate"').type('04/09/2012');
    cy.get('id="aa_toDate"').type('06/09/2012');
   
  });

  it('8. Preencher os campos Amounts com 40 até 60', () => {
    cy.get('id="aa_fromAmount"').type('40');
    cy.get('id="aa_toAmount"').type('60');

});

it('9. Realizar a consulta e validar que o resultado foi exibido', () => {
    cy.get('.btn-primary').click();
    cy.contains('id="filtered_transactions_for_account"').type('50');

});   

it('10. Realizar Logout e validar que o usuário não está mais logado', () => {
    cy.get('xpath=//*[@id="settingsBox"]/ul/li[3]/ul').click();
    cy.get('xpath=////*[@id="logout_link"]"').click();
    cy.contains('#signin_button"').type('Signin');
});
