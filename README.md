# Alert
O objetivo desta função é apresentar uma mensagem na tela do PowerShell, onde o usuário só poderá continuar após tomar uma decisão.

Esta função de alerta é composta por um título, uma mensagem e botões de ação.

## Parâmetros:

### 1. PROMPT (Obrigatório):
   Uma string que representa a mensagem exibida na caixa de diálogo. O prompt pode ser ilimitado de caracteres por padrão. No entanto, é possível limitar a quantidade de caracteres do prompt definindo o valor de charPrompt para um número maior que 0. Se o prompt consistir em mais de uma linha, automaticamente a linha será quebrada.

### 2. TITLE (Opcional):
   Uma string que representa o título exibido na barra de título da caixa de diálogo. Se omitido, o nome do aplicativo é colocado na barra de título. O desenvolvedor tem uma quantidade limitada de caracteres, dependendo do tipo de botão escolhido e se será utilizado o recurso de CONTEXT. Se o texto for maior que o espaço disponível, os últimos 3 caracteres serão retirados para adicionar reticências (...).

### 3. BUTTONS (Opcional):
   Um número que é a combinação de valores que especificam o número e o tipo de botões a serem exibidos, o estilo do ícone a ser usado, a identidade do botão padrão e a modalidade da caixa de mensagem. Se omitido, o valor padrão de buttons será 0. Os botões estão listados juntamente com o ícone que será apresentado ao lado do TITLE e o retorno esperado desta função por meio do botão pressionado. Veja os tipos de botões aceitos e como criar um botão próprio:

   0 - btOkOnly
            Botões: [O]k; [X]
   Retornos esperados: o ou x
            Ícone: Nenhum

   1 - btOkCancel
            Botões: [O]k; [C]ancelar; [X] 
   Retornos esperados: o, c ou x
            Ícone: Nenhum

   2 - btAbortRetryIgnore
            Botões: [A]nular; [R]eparar; [I]gnorar
   Retornos esperados: a, r ou i
            Ícone: Nenhum

   3 - btCritical
            Botões: [O]k; [X]
   Retornos esperados: o ou x
            Ícone: X

   4 - btYesNoCancel
            Botões: [O]k; [N]ão; [C]ancelar; [X]
   Retornos esperados: o, n, c, x
            Ícone: Nenhum

   5 - btYesNo
            Botões: [O]k; [N]ão
   Retornos esperados: o ou n
            Ícone: Nenhum

   6 - btRetryCancel
            Botões: [R]epetir; [C]ancelar; [X]
   Retornos esperados: r, c ou x
            Ícone: Nenhum

   7 - btExclamation
            Botões: [O]k; [X]
   Retornos esperados: o ou x
            Ícone: !

   8 - btInformation
            Botões: [O]k; [X]
   Retornos esperados: o ou x
            Ícone: i

   9 - btHelp
            Botões: [O]k; [A]juda; [X]
   Retornos esperados: o, a ou x
            Ícone: Nenhum

   10 - btQuestion
            Botões: [O]k; [X]
   Retornos esperados: o ou x
            Ícone: ?

   11 - btSystemModal
            Botões: [O]k; [X]
   Retornos esperados: o ou x
            Ícone: ☰

   12 - btNext
            Botões: [A]vamçar; [X]
  Retornos esperados: a, x
           Ícone: >

   13 - btNextBack
            Botões: [V]oltar; [X]
  Retornos esperados: v, x
           Ícone: <

   14 - btPersonalize ['?',true,'Saber mais','Buscar', 'Sair']
           Botões: [S]aber mais; [B]uscar; S[A]ir
 Retornos esperados: s, b, a
           Ícone: ?
Esse último tipo de botão é customizado pelo desenvolvedor. O primeiro atributo do objeto se refere ao ícone que será exibido ao lado do botão. O segundo atributo determina a presença do botão 'X' (fechar janela), sendo true para que o botão exista ou false para que ele não seja exibido. Em seguida, são listados os textos dos botões. O sistema selecionará automaticamente o primeiro caractere de cada texto para determinar a seleção do botão. No caso de dois botões começarem com a mesma letra, será escolhido o segundo ou o terceiro, e assim por diante. Se dois atributos forem iguais, um deles será desconsiderado.

### 4. HELPFILE:
Se um texto de ajuda for especificado no HelpFile, a barra de título receberá o botão de interrogação [?]. Quando o usuário pressionar '?', será exibida uma tela explicando melhor o motivo daquele alerta. Ao pressionar 'O' do [O]k ou o 'X' do botão [X], ele voltará ao alerta.

### 5. CONTEXT:
Opcional. É uma expressão numérica que representa o número de contexto da Ajuda atribuído ao tópico da Ajuda correspondente pelo autor. Se o contexto for fornecido, o helpfile também deve ser fornecido.
