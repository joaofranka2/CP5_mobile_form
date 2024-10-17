# CP5_mobile_form


integrantes 

552421 - Flavio Sousa Vasconcelos

552368 - WELLINGTON DE OLIVEIRA URCINO DA SILVA

97887 - João Carlos França Figueiredo

550200 - Leonardo Oliveira Esparza

integrantes 
552421 - Flavio Sousa Vasconcelos
552368 - WELLINGTON DE OLIVEIRA URCINO DA SILVA
97887 - João Carlos França Figueiredo
550200 - Leonardo Oliveira Esparza

Documentação do Projeto: Formulário Multi-Etapas com Reset Automático
1. Descrição Geral do Projeto

Este projeto consiste em um Formulário Multi-Etapas desenvolvido em Flutter. Ele guia o usuário por uma sequência de etapas para preencher informações pessoais, como nome, email, telefone, gênero, data de nascimento, e aceitar os termos e condições.

O projeto também inclui uma funcionalidade de reset automático do formulário. Assim que o formulário é concluído e salvo, ele é automaticamente redefinido para permitir que o usuário crie um novo formulário desde o início, sem a necessidade de recarregar a página ou manualmente apagar os campos preenchidos.

2. Funcionalidades Principais

Formulário Multi-Etapas: Utiliza o widget Stepper para dividir o preenchimento de dados em várias etapas.
Salvamento Local dos Dados: O formulário salva os dados preenchidos utilizando o pacote SharedPreferences.
Reset Automático: Após a conclusão do preenchimento do formulário, todos os campos são redefinidos automaticamente, e o formulário volta ao seu estado inicial para um novo preenchimento.
Validação de Termos e Condições: O usuário é obrigado a aceitar os termos e condições antes de concluir o preenchimento do formulário.

3. Estrutura de Pastas

lib/
├── src/
│   ├── form_state_notifier.dart   # Gerencia o estado do formulário e inclui a função de reset
│   ├── multi_step_form.dart       # Implementa o formulário multi-etapas com reset automático
└── main.dart                      # Arquivo principal do aplicativo que gerencia a navegação

4. Dependências
Este projeto utiliza as seguintes dependências no arquivo pubspec.yaml:
dependencies:
  flutter:
    sdk: flutter
  cupertino_icons: ^1.0.2
  intl: ^0.19.0            # Para formatação de datas
  shared_preferences: ^2.0.15 # Para salvamento local dos dados
  provider: ^6.0.0         # Para gerenciamento de estado do formulário
O pacote provider é utilizado para gerenciar o estado do formulário através da classe FormStateNotifier. O pacote shared_preferences é utilizado para salvar os dados localmente e permitir que o usuário possa recuperá-los em futuras sessões do aplicativo.


5. Explicação Detalhada do Código

5.1 form_state_notifier.dart
Este arquivo contém a lógica de gerenciamento do estado do formulário. Ele armazena os dados inseridos pelo usuário e salva as informações localmente usando SharedPreferences.

Variáveis de Estado: São utilizadas variáveis como _name, _email, _phone, _gender, _birthDate, e _acceptTerms para armazenar os valores dos campos do formulário.
Função saveFormData: Salva os dados do formulário em SharedPreferences como um objeto JSON.
Função resetForm: Redefine todos os campos para seus valores padrão (vazios ou falsos).
Exemplo de Função resetForm:

void resetForm() {
  _name = '';
  _email = '';
  _phone = '';
  _gender = '';
  _birthDate = '';
  _acceptTerms = false;
  notifyListeners();  // Notifica os widgets dependentes para que sejam atualizados
}


5.2 multi_step_form.dart

Este arquivo implementa o formulário multi-etapas. O Stepper é utilizado para guiar o usuário por cada etapa do formulário.

Reset Automático: Após o preenchimento completo do formulário, o método resetForm() é chamado para redefinir o estado, e o Stepper retorna à primeira etapa.
Exemplo da Chamada de resetForm ao Concluir o Formulário:

if (formState.acceptTerms) {
  formState.saveFormData();  // Salva os dados após o preenchimento
  formState.resetForm();  // Reseta o formulário após salvar
  ScaffoldMessenger.of(context).showSnackBar(
    const SnackBar(content: Text('Formulário Completo!')),
  );
  setState(() {
    _currentStep = 0;  // Reseta o Stepper para a primeira etapa
  });
}

5.3 main.dart

O arquivo main.dart inicializa o aplicativo e configura a navegação. Ao clicar no botão "Preencher Novo Formulário", o usuário é direcionado para o formulário multi-etapas.

Uso de Provider: O Provider é utilizado para disponibilizar a instância do FormStateNotifier para o formulário multi-etapas.
Exemplo de Inicialização do Aplicativo:

void main() {
  runApp(
    MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (_) => FormStateNotifier()),
      ],
      child: const MyApp(),
    ),
  );
}

6. Fluxo do Usuário
Início: O usuário inicia o aplicativo na tela inicial, onde pode clicar no botão "Preencher Novo Formulário".
Preenchimento do Formulário: O usuário preenche os dados em diferentes etapas. Cada etapa pode ser validada antes de prosseguir.
Aceitar Termos e Condições: Para concluir o formulário, o usuário deve aceitar os termos e condições.
Finalização e Reset: Após a conclusão, o formulário é salvo, o usuário é notificado, e os campos são automaticamente redefinidos para permitir um novo preenchimento.

7. Personalização e Extensibilidade
Este projeto é altamente extensível. Aqui estão algumas sugestões de melhorias e personalizações:

Validação Avançada: Adicionar validações avançadas, como verificação de email e número de telefone.
Armazenamento em Nuvem: Utilizar um backend para armazenar os formulários em um banco de dados remoto, em vez de salvar localmente.
Temas Customizados: Implementar suporte a múltiplos temas visuais, permitindo que o usuário escolha o estilo da interface.
Notificações Push: Adicionar notificações para lembrar o usuário de completar o formulário, caso ele seja deixado incompleto.

8. Conclusão
Este projeto demonstra como construir um formulário multi-etapas em Flutter com um ciclo completo de salvamento de dados localmente e redefinição automática do estado após a submissão. Ele oferece uma estrutura escalável e modular, permitindo futuras expansões e melhorias de funcionalidade.

Se você deseja personalizar o comportamento ou adicionar mais etapas ao formulário, basta modificar a lógica dentro dos widgets do Stepper ou adicionar novos campos no FormStateNotifier.



Como Rodar o Código 

Instalar o Flutter:

Baixe o Flutter SDK em: https://flutter.dev/docs/get-started/install.
Após o download, descompacte o SDK em um diretório acessível no seu sistema.
Adicione o Flutter ao PATH do sistema para que o comando flutter possa ser utilizado no terminal.
No terminal, execute o comando: flutter doctor para verificar se o Flutter foi instalado corretamente e identificar o que ainda precisa ser configurado.
Clonar o Repositório:

Abra o terminal ou prompt de comando.
Execute o comando git clone https://github.com/seu-usuario/seu-repositorio.git para clonar o repositório.
Acesse o diretório do projeto com cd form_app.
Instalar as Dependências:

No terminal, execute flutter pub get para instalar todas as dependências especificadas no arquivo pubspec.yaml.
Rodar o Projeto:

Conecte um dispositivo Android ou iOS, ou inicie um emulador.
No terminal, execute flutter run para rodar o projeto no dispositivo ou emulador conectado.
Rodar no Emulador ou Dispositivo Físico:

Se estiver usando um emulador, inicie-o pelo Android Studio ou pelo terminal com flutter emulators --launch nome_do_emulador.
Para um dispositivo físico, habilite o modo de desenvolvedor e conecte o dispositivo ao computador via USB. Execute flutter devices e depois flutter run.
Compilar para Web (Opcional):

Ative o Flutter Web com o comando flutter config --enable-web.
Execute o projeto no navegador com flutter run -d chrome.
