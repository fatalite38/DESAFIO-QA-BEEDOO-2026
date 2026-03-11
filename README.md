# DESAFIO-QA-BEEDOO-2026

Aplicação Testada:
URL: https://creative-sherbet-a51eac.netlify.app/
Módulo Alvo: Cadastro e Listagem de Cursos

Funcionalidades Disponíveis:
✅ Cadastro de novos cursos
✅ Listagem de cursos cadastrados
❌ Edição de cursos (não implementada)
⚠️ Exclusão de cursos (não funcional)

## 1.1. Objetivo da Aplicação
A aplicação é um sistema web simples de gestão educacional focado no módulo de cadastro e de listagem de cursos. O objetivo principal é permitir que administradores e gestores educacionais realizem operações de gerenciamento de cursos de forma centralizada, incluindo:

- Cadastramento de novos cursos com informações estruturadas
- Visualização e consulta de cursos cadastrados
- Manutenção e atualização de dados dos cursos
- Controle de informações críticas como nome, descrição, tipo de curso, número de vagas, data de início, fim e instrutor

O sistema visa proporcionar uma interface intuitiva para gestão acadêmica, facilitando o planejamento e a organização de ofertas educacionais.

## 1.2. Principais Fluxos Disponíveis
Fluxo 1: Cadastro de Curso
Permite ao usuário criar um novo curso no sistema através de um formulário com os seguintes campos esperados:

- Nome do curso
- Descrição
- Instrutor
- Url da imagem de capa
- Data de início e fim ( formato de data)
- Número de vagas (obrigatório, numérico)
- Tipo de Curso (Presencial, Online)
  - Se presencial -> Colocar o endereço
  - Se online -> Colocar o link de inscrição

Ação principal: Submissão do formulário, com validação de campos obrigatórios e formatos esperados.

Fluxo 2: Listagem de Cursos
Exibe todos os cursos cadastrados no sistema, apresentando:

- Informações resumidas de cada curso
  - Modalidade, Curso, Descrição, data de início, fim e quantidade de vagas.
  - Botão de exclusão

Ação principal: Visualização consolidada dos dados cadastrados.
Nota importante: Não existe funcionalidade de edição de cursos na aplicação atual. A exclusão apresenta problemas de funcionamento (exibe mensagem em um alerta, mas não executa a ação).


## 1.3. Pontos Críticos para teste
  2.3.1 Ausência de Validações de Obrigatoriedade
  Justificativa: A aplicação permite cadastro de cursos completamente vazios, sem nenhum campo preenchido. Isso compromete totalmente a integridade dos dados e a finalidade do sistema.
  Impacto: Sistema perde sua função principal ao permitir registros sem informações mínimas necessárias. Impossibilita filtros, buscas e relatórios confiáveis.
  
  2.3.2 Ausência de Validações de Tipo de Dados
  Justificativa: Campos de texto (Nome, Descrição, Instrutor) aceitam valores numéricos, e campos de URL aceitam qualquer formato. Isso permite entrada de dados inconsistentes e sem sentido.
  Impacto: Dados sem significado semântico, impossibilidade de aplicar regras de negócio adequadas, comprometimento de integrações e exportações de dados.
  
  1.3.3 Funcionalidade de Exclusão Não Implementada
  Justificativa: O botão de exclusão exibe mensagem de sucesso, mas não executa a remoção do curso, criando uma falsa impressão de funcionalidade.
  Impacto: Impossibilita gerenciamento adequado do catálogo de cursos, acúmulo de dados desnecessários, mensagem enganosa destrói confiança no sistema.
  
  1.3.4 Exibição Incompleta de Dados na Listagem
  Justificativa: O nome do instrutor não é exibido na listagem, apesar de ser um dado fundamental para identificação e organização dos cursos.
  Impacto: Perda de informação crítica para gestão acadêmica, impossibilidade de identificar responsável pelo curso sem acessar detalhes individuais.
  
  1.3.5 Validação de URLs e Links
  Justificativa: Campos de URL de imagem e link de inscrição aceitam qualquer string sem validação de formato, podendo causar quebra de imagens e links inválidos.
  Impacto: Imagens quebradas na interface, links não funcionais para inscrição, má experiência do usuário, possível injeção de URLs maliciosas.
  
  1.3.6 Impossibilidade de Edição de Cursos
  Justificativa: Sem funcionalidade de edição, qualquer erro no cadastro requer exclusão e recadastramento completo (que também não funciona).
  Impacto: Inflexibilidade operacional total, impossibilidade de correção de dados, sistema inadequado para uso real.
  

## 2. Criação de cenários e casos de teste
  2.1 Raciocínio de Priorização
  A estratégia de priorização foi baseada em: 
  
  Análise de risco:
  Validações de obrigatoriedade (permite cadastro vazio - CRÍTICO)
  Funcionalidade de exclusão quebrada (CRÍTICO)
  Validações de tipo de dados (CRÍTICO)
  Dados faltantes na listagem (ALTO)
  Validações de formato de URLs (MÉDIO)
  
  Frequência de Uso:
  Cadastro de curso: Fluxo principal, executado frequentemente
  Listagem de cursos: Acesso constante para consultas
  Exclusão de cursos: Operação frequente em manutenção do catálogo
  
  Impacto no Usuário:
  Mensagens enganosas (exclusão "bem-sucedida" mas não funciona)
  Falta de feedback visual adequado
  Dados incompletos comprometem tomada de decisões

 2.2 Documentação de Testes
 Casos de Teste Criados: 35 casos
    Distribuição por Tipo:
    - Happy Path: 2 Casos (online e presencial)
    - Validações de Obrigatoriedade: 10 casos
    - Validações de Tipo/Formato: 8 casos
    - Validações de Datas: 4 casos
    - Listagem: 4 casos
    - Exclusão: 1 caso
    - Segurança/Performance: 2 casos
 
  Link da planilha: https://docs.google.com/spreadsheets/d/1qdKBqGojkwLux5KYx8ZnAgWuF7auO-4wsCVh3Yb37Uk/edit?usp=sharing
    Aba 1: 35 casos de teste detalhados
    Aba 2: Resumo da execução

  
## 3. Execução dos testes
  Principais Resultados:
  
  ✅ TC-001: Cadastro válido completo - PASSOU
  Sistema funciona quando todos os campos são preenchidos corretamente
  
  ❌ TC-002: Cadastro vazio - FALHOU
  Sistema permite cadastro sem nenhum campo preenchido
  
  ❌ TC-016: Exclusão de curso - FALHOU
  Exibe mensagem de sucesso mas não remove o curso
  
  ❌ TC-014: Exibição do instrutor - FALHOU
  Nome do instrutor não aparece na listagem

  Relatório Completo: https://docs.google.com/spreadsheets/d/1TzkBkyM3-McZF7PswD4OK8hYLtlxUBttuzW1N_103XA/edit?usp=sharing

## 4. Registros de Bugs
🔴 Crítica  2  BUG-001, BUG-002
🟠 Alta     4  BUG-003, BUG-004, BUG-005, BUG-006
🟡 Média    1  BUG-007
TOTAL7

Bugs Críticos:
  BUG-001 🔴 CRÍTICO.
  Título: Sistema permite cadastro de curso completamente vazio sem nenhuma validação de obrigatoriedade.
  Módulo: Cadastro de Cursos.
  Ambiente: Web (Chrome, Firefox, Edge).
  Severidade: 🔴 Crítica.
  
  Passos para reproduzir:
    1- Acessar https://creative-sherbet-a51eac.netlify.app/
    2- Acessar o formulário de cadastro de cursos.
    3- NÃO preencher nenhum campo - deixar todos vazios.
    4- Não selecionar tipo de curso.
    5- Clicar no botão "Salvar" ou "Cadastrar".
    6- Verificar se o curso foi cadastrado.
    7- Acessar a listagem de cursos.
    
  Resultado atual: Sistema aceita o cadastro sem nenhum dado preenchido. Um curso vazio é criado e aparece na listagem sem informações.
  Resultado esperado: Sistema deve validar campos obrigatórios mínimos (Nome, Descrição, Instrutor, Data início, Data fim, Número de vagas, Tipo de curso) e exibir mensagens de erro específicas. O cadastro deve ser bloqueado até que os campos obrigatórios sejam preenchidos.
  
  Impacto: 
  - Compromete completamente a integridade dos dados do sistema.
  - Permite criação de registros sem significado, impossibilita buscas, filtros e relatórios confiáveis.
  - Sistema perde sua função principal de gerenciar informações de cursos.

  
  BUG-002 🔴 CRÍTICO.
    Título: Botão de exclusão exibe mensagem "Curso excluído com Sucesso!" mas não remove o curso da listagem.
    Módulo: Exclusão de Cursos / Listagem de Cursos.
    Ambiente: Web (todos os navegadores).
    Severidade: 🔴 Crítica.
    Passos para reproduzir:
      1- Acessar a aplicação
      2- Cadastrar um curso com dados válidos
      3- Navegar para a listagem de cursos
      4- Localizar o curso recém-cadastrado
      5- Clicar no botão vermelho de exclusão abaixo do curso
      6- Observar o alerta: "Curso excluído com Sucesso!"
      7- Fechar o alert (clicar OK)
      8- Verificar a listagem de cursos
    Resultado atual: Sistema exibe alerta de sucesso, porém o curso permanece visível na listagem. Nenhuma alteração é feita
    Resultado esperado: Após clicar em excluir: (1) Exibir mensagem APENAS se exclusão foi executada, (2) Remover curso da listagem, (3) Atualizar interface, (4) Persistir exclusão no backend
    Impacto: 
    - Funcionalidade de exclusão completamente não funcional. 
    - Impossibilidade de gerenciamento do catálogo, mensagem enganosa destrói confiança no sistema. 
    - Viola princípios básicos de CRUD.


Bugs Altos:
  BUG-003 🟠 ALTO
    Título: Nome do instrutor não é exibido na listagem de cursos
    Módulo: Listagem de Cursos
    Ambiente: Web (todos os navegadores)
    Severidade: 🟠 Alta
    Passos para reproduzir:
      1- Cadastrar curso com instrutor "Maria Silva"
      2- Navegar para listagem
      3- Verificar dados exibidos
    Resultado atual: Nome do instrutor não é exibido na listagem
    Resultado esperado: Instrutor deve ser exibido, pois é informação crítica
    Impacto: 
    - Perda de informação fundamental para gestão acadêmica.
    - Impossibilita identificar responsável pelo curso.
    
  BUG-004 🟠 ALTO
    Título: Campos de texto (Nome, Descrição, Instrutor) aceitam valores numéricos sem validação
    Módulo: Cadastro de Cursos
    Ambiente: Web (todos os navegadores)
    Severidade: 🟠 Alta
    Passos para reproduzir:
      1- Preencher "Nome do curso": "12345"
      2- Preencher "Descrição": "999999"
      3- Preencher "Instrutor": "777"
      4- Preencher demais campos válidos
      5- Salvar
    Resultado atual: Sistema aceita valores numéricos em campos de texto
    Resultado esperado: Validação de tipo de conteúdo
    Impacto: 
    - Dados sem significado semântico.
    - Cursos com nomes numéricos não fazem sentido.
    
  BUG-005 🟠 ALTO
    Título: Campos URL e Link aceitam qualquer texto sem validação de formato
    Módulo: Cadastro de Cursos
    Ambiente: Web (todos os navegadores)
    Severidade: 🟠 Alta
    Passos para reproduzir:
      1- Preencher "URL da Imagem": "imagem qualquer"
      2- Selecionar tipo "Online"
      3- Preencher "Link de inscrição": "abc123"
      4- Salvar
    Resultado atual: Sistema aceita qualquer string sem validar formato de URL
    Resultado esperado: Validação de formato http:// ou https://
    Impacto: 
    - Imagens quebradas.
    - links não funcionais.
  
  BUG-006 🟠 ALTO
    Título: Campo Número de Vagas aceita valores negativos e zero
    Módulo: Cadastro de Cursos
    Ambiente: Web (todos os navegadores)
    Severidade: 🟠 Alta
    Passos para reproduzir:
      1- Preencher "Número de vagas": "-5"
      2- Preencher demais campos válidos
      3- Salvar
      4- Repetir com: "0"
    Resultado atual: Sistema aceita valores negativos e zero
    Resultado esperado: Validação: número positivo >= 1. Erro: "Número de vagas deve ser maior que zero"
    Impacto:
    - Dados logicamente inconsistentes.
    - Curso sem vagas ou com vagas negativas não faz sentido


Bug Médio:
  BUG-007 🟡 MÉDIO
    Título: Campos de texto aceitam apenas espaços em branco
    Módulo: Cadastro de Cursos
    Ambiente: Web (todos os navegadores)
    Severidade: 🟡 Média
    Passos para reproduzir:
      1- Preencher campos com apenas espaços: "     "
      2- Salvar
    Resultado atual: Sistema aceita whitespace
    Resultado esperado: Aplicar trim() e validar
    Impacto: Cria registros sem conteúdo significativo
     

## Métricas de Qualidade
Cobertura de Testes
  - Fluxo Principal: 100% coberto
  - Validações de Campos: 75% executado
  - Funcionalidades CRUD: 50% executado
  - Testes de Segurança: 0% executado (pendente)

Densidade de Defeitos
  - Bugs Críticos: 3
  - Bugs por Funcionalidade:
      - Cadastro: 4 bugs
      - Listagem: 2 bugs
      - Exclusão: 1 bug

Taxa de Aprovação
  - Happy Path: 100% passou
  - Validações: 0% passou (13 falharam)
  - Geral: 6.7% passou


## Captura de Evidências

  Bug de Validação de dados
  https://drive.google.com/file/d/1SFKwLjEMY44_ngkKs2ZQq21GWnwuVxjH/view?usp=sharing
  
  Bug de cadastro vazio
  https://drive.google.com/file/d/1lQD4W32AVGjw6NNBvH-mWwYmb549OaOz/view?usp=sharing

  Bug de exclusão
  https://drive.google.com/file/d/1lQD4W32AVGjw6NNBvH-mWwYmb549OaOz/view?usp=sharing

  Erros no devTools
  https://drive.google.com/file/d/1QM-6tixmuoqp6yS0sK4lIuVxclAgG5CJ/view?usp=sharing


## Melhorias Sugeridas 
  - Implementar validações de obrigatoriedade em todos os campos.
  - Implementar feedback visual para todas as ações.
  - Adicionar confirmação antes da exclusão.
  - Corrigir funcionalidade de exclusão.
  - Implementar funcionalidade de edição de cursos.
  - Melhorar mensagens de erro (mais específicas e orientativas).
  - Adicionar validação de dados.

## Autor
- Luiz Fernando Dionizio Pedrozo
