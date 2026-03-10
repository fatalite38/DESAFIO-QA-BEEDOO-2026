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
 Casos de Teste Criados: 30 casos
    Distribuição por Tipo:
    - Happy Path: 1 caso
    - Validações de Campos: 15 casos
    - Verificação de Exibição: 6 casos
    - Funcionalidades CRUD: 4 casos
    - Segurança: 1 caso
    - Performance: 2 casos
    - Exploratórios: 1 caso
 
  Link da planilha: blank<https://docs.google.com/spreadsheets/d/1TzkBkyM3-McZF7PswD4OK8hYLtlxUBttuzW1N_103XA/edit?usp=sharing>

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

Bugs Críticos:
  BUG-001: Sistema permite cadastro vazio sem validações
  Severidade: 🔴 Crítica
  Impacto: Compromete integridade total dos dados
  Status: Aberto
  
  BUG-002: Exclusão não funciona (apenas exibe alert)
  Severidade: 🔴 Crítica
  Impacto: Funcionalidade CRUD quebrada
  Status: Aberto
  
  BUG-006: Aceita valores negativos e zero em carga horária
  Severidade: 🔴 Crítica
  Impacto: Dados logicamente inconsistentes
  Status: Aberto


Bugs Altos:
  BUG-003: Instrutor não aparece na listagem
  Severidade: 🟠 Alta
  Impacto: Perda de informação crítica
  Status: Aberto
  
  BUG-004: Campos texto aceitam números
  Severidade: 🟠 Alta
  Impacto: Sem validação de tipo de dados
  Status: Aberto
  
  BUG-005: URLs aceitam qualquer formato
  Severidade: 🟠 Alta
  Impacto: Imagens quebradas, links inválidos
  Status: Aberto

Bug Médio:
  BUG-007: Aceita espaços em branco nos campos
  Severidade: 🟡 Média
  Impacto: Burla validações básicas
  Status: Aberto


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

## Melhorias Sugeridas
  - Implementar feedback visual para todas as ações
  - Adicionar confirmação antes de exclusão
  - Implementar funcionalidade de edição de cursos
  - Melhorar mensagens de erro (mais específicas e orientativas)
  - Adicionar validação de datas (formato, passado vs futuro)

## Autor
- Luiz Fernando Dionizio Pedrozo
