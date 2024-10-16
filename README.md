# CP5_mobile_form

integrantes 
552421 - Flavio Sousa Vasconcelos
552368 - WELLINGTON DE OLIVEIRA URCINO DA SILVA
97887 - João Carlos França Figueiredo
550200 - Leonardo Oliveira Esparza

Documentação do Projeto de Formulários com Validação
1. Introdução
Este projeto foi desenvolvido utilizando Flutter e demonstra a criação de diferentes tipos de formulários com validação de dados e boas práticas de UX. Ele inclui exemplos de um Formulário de Login, um Formulário com Validação de Email e Senha, e um Formulário Multi-Etapas, cada um validando entradas e proporcionando uma experiência de usuário completa. Várias melhorias foram implementadas para enriquecer a funcionalidade e a usabilidade do sistema.
2. Funcionalidades Principais
2.1 Formulário de Login
O formulário de login inclui dois campos: Nome de Usuário e Senha.
Há uma validação simples para garantir que ambos os campos estejam preenchidos.
Simulação de login bem-sucedido com as credenciais corretas (usuário: admin, senha: 1234).
Exibe mensagens de erro caso o nome de usuário ou a senha estejam incorretos ou em branco.
2.2 Formulário com Validação de Email e Senha
O formulário permite validar um email e uma senha.
A senha deve conter ao menos 8 caracteres, uma letra maiúscula e um número.
Validação de Confirmação de Senha, garantindo que a senha inserida nos dois campos seja a mesma.
Exibe mensagens de erro específicas se as validações falharem.
2.3 Formulário Multi-Etapas
Um formulário dividido em várias etapas, cada uma coletando uma informação específica: Nome, Email, Data de Nascimento, Gênero e Telefone.
Cada etapa inclui validação de campos antes de permitir o avanço para a próxima etapa.
Exibe uma etapa final de Confirmação, onde o usuário pode verificar as informações inseridas antes de concluir.
Inclui um campo para o usuário aceitar os Termos e Condições antes de finalizar o formulário.
3. Melhorias Implementadas
3.1 Adição de Campo de Data de Nascimento (com DatePicker)
Foi adicionado um campo no formulário multi-etapas para que o usuário escolha sua Data de Nascimento utilizando um DatePicker. Esse campo valida se a data foi selecionada antes de prosseguir para a próxima etapa.

3.2 Adição de Campo de Gênero (com Radio Buttons)
O campo de Gênero foi implementado utilizando botões de rádio, permitindo ao usuário escolher entre as opções: Masculino, Feminino e Outro. A escolha é validada como obrigatória antes de continuar.

3.3 Aceite de Termos e Condições (com Checkbox)
Uma etapa final foi adicionada ao formulário multi-etapas, onde o usuário deve marcar uma caixa de seleção (checkbox) confirmando que aceita os Termos e Condições antes de concluir o processo. Caso não seja marcado, o formulário não pode ser submetido.

3.4 Campo de Confirmação de Senha no Formulário de Validação
Adicionamos um campo de Confirmar Senha no formulário de validação de email e senha, para garantir que o usuário insira a mesma senha duas vezes. A validação garante que as duas entradas de senha coincidam.

3.5 Feedback Visual para Campos Preenchidos Corretamente
Foi implementada uma funcionalidade que altera a borda dos campos para verde quando as entradas são válidas, proporcionando um feedback visual instantâneo ao usuário. Isso melhora a experiência de preenchimento dos formulários.

4. Estrutura do Projeto
lib/
  ├── src/
  │    │    ├── multi_step_form.dart         # Formulário Multi-Etapas
  │    │    ├── email_password_form.dart     # Formulário de Validação de Email e Senha
  │    │    └── login_form.dart              # Formulário de Login
  │    └── form_state_notifier.dart          # Gerencia o estado e validação dos dados do 
  └── main.dart                              # Arquivo principal com a navegação entre os formulários

5. Como Executar o Projeto
5.1 Clonar o Repositório
git clone https://github.com/seu-repositorio.git
5.2 Instalar as Dependências
flutter pub get
5.3 Executar o Projeto
flutter run
6. Tecnologias Utilizadas
Flutter: Framework utilizado para desenvolvimento do aplicativo.
Provider: Utilizado para gerenciamento de estado reativo.
Dart: Linguagem de programação usada para implementar a lógica do aplicativo.
