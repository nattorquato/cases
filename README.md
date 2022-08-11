# describe(‘Salsa’, ()  => {
	it(‘1. Acessar http://zero.webappecurity.com/’,()  => {
		cy.visit({
		       url:  ‘http://zero.webappecurity.com/’,
         		       method:  ‘GET’ 
		  })
		cy.get(‘#signin_button’).click();
	});
	It(‘2.  Realizar login na plataforma  (usuário:  usrname  |  senha:  password’,  () => {
		cy.get(‘#user_login’).type(‘username’);
		cy.get(‘#user_password’).type(‘password’);
cy.get(‘.btn’).click();
