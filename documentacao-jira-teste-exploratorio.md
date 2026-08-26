# Teste exploratório - Trilhas do Conhecimento

## Informações gerais

- **Aplicação:** https://trilha-de-conhecimento.netlify.app/
- **Data do teste:** 26/08/2026
- **Tipo:** Teste exploratório manual com automação MCP/browser
- **Conta utilizada:** Usuária de teste autorizada (credenciais não registradas)
- **Escopo:** Login, logout, trilhas, inscrição, área do estudante, favoritos, busca, menus, certificado e responsividade.

## Resultado executivo

O login, a inscrição em uma trilha e a inclusão de favorito funcionaram. Foram identificados 10 problemas, sendo 1 crítico, 3 altos, 3 médios e 3 baixos.

---

## B-01 - Acesso indevido após logout

- **Tipo:** Bug de segurança
- **Prioridade Jira:** Highest
- **Severidade:** Crítica
- **Componente:** Autenticação / autorização

### Passos para reproduzir

1. Acessar a aplicação.
2. Fazer login com uma conta autorizada.
3. Acessar “Minhas Trilhas”.
4. Clicar em “Sair”.
5. Abrir novamente a rota `/student/.../my-list`.

### Resultado esperado

O usuário deve ser redirecionado para a tela de login e nenhum dado privado deve ser renderizado.

### Resultado atual

O cabeçalho mostra “Login”, mas a página continua exibindo o nome completo da estudante e suas trilhas.

### Impacto

Exposição de dados pessoais e falha no controle de acesso a uma rota protegida.

### Critério de aceite

Após o logout, qualquer rota `/student/*` deve redirecionar para `/login`, sem exibir dados do usuário. O comportamento deve permanecer correto após recarregar a página e usar o botão voltar.

---

## B-02 - Menu “Comunidade” sem ação

- **Tipo:** Bug funcional
- **Prioridade Jira:** High
- **Severidade:** Alta
- **Componente:** Navegação

### Passos para reproduzir

1. Fazer login.
2. Clicar em “Comunidade” no menu principal.

### Resultado esperado

O usuário deve ser direcionado para a página ou funcionalidade da comunidade.

### Resultado atual

O item aparenta ser clicável, mas não altera a URL nem apresenta conteúdo.

### Critério de aceite

O menu deve abrir uma rota funcional ou deixar de apresentar estado clicável até a funcionalidade estar disponível.

---

## B-03 - Ações do rodapé não navegam

- **Tipo:** Bug funcional
- **Prioridade Jira:** High
- **Severidade:** Alta
- **Componente:** Rodapé / navegação

### Passos para reproduzir

1. Acessar a página inicial ou uma página autenticada.
2. Clicar em “Sobre os criadores”, “Emitir Certificado”, “Fale com a gente”, “Quero voluntariar” ou “Quero mentorar”.

### Resultado esperado

Cada item deve abrir seu destino correspondente.

### Resultado atual

Nenhuma das ações apresenta navegação ou feedback observável.

### Critério de aceite

Todos os itens devem possuir links válidos, com destino testado e acessível por teclado.

---

## B-04 - Progresso da trilha não é atualizado

- **Tipo:** Bug funcional
- **Prioridade Jira:** High
- **Severidade:** Alta
- **Componente:** Área do estudante / progresso

### Passos para reproduzir

1. Fazer login.
2. Inscrever-se em uma trilha.
3. Acessar “Minhas Trilhas”.
4. Abrir a trilha inscrita.

### Resultado esperado

O sistema deve informar o progresso da trilha e permitir registrar conteúdos concluídos.

### Resultado atual

A trilha permanece como “Não Iniciado” e não há ação evidente para concluir conteúdos.

### Critério de aceite

O estudante deve conseguir marcar conteúdos como concluídos, visualizar percentual/status e manter o progresso após sair e entrar novamente.

---

## B-05 - Busca não filtra conteúdos

- **Tipo:** Bug funcional
- **Prioridade Jira:** Medium
- **Severidade:** Média
- **Componente:** Busca

### Passos para reproduzir

1. Abrir uma trilha.
2. Digitar `Figma` no campo “Pesquisa”.

### Resultado esperado

Somente conteúdos relacionados a “Figma” devem permanecer visíveis.

### Resultado atual

Os conteúdos não relacionados continuam visíveis; não há estado de resultados filtrados ou “nenhum resultado”.

### Critério de aceite

A busca deve filtrar por título, etapa e descrição, ignorar diferenças de maiúsculas/minúsculas e apresentar mensagem quando não houver resultados.

---

## B-06 - Emissão de certificado indisponível

- **Tipo:** Bug funcional
- **Prioridade Jira:** Medium
- **Severidade:** Média
- **Componente:** Certificado

### Resultado esperado

O item “Emitir Certificado” deve abrir o fluxo de emissão ou informar claramente os requisitos.

### Resultado atual

O item é exibido no rodapé, mas não leva a um fluxo funcional.

### Critério de aceite

A ação deve abrir uma tela funcional, indicar elegibilidade e permitir emitir ou baixar o certificado quando os requisitos forem cumpridos.

---

## B-07 - Conteúdo incompleto e descrições genéricas

- **Tipo:** Bug de conteúdo
- **Prioridade Jira:** Medium
- **Severidade:** Média
- **Componente:** Conteúdo das trilhas

### Resultado esperado

Cada etapa deve possuir nome, descrição e conteúdo revisados e específicos.

### Resultado atual

A trilha UX/UI contém itens “Nome do Tópico” e descrições genéricas repetidas.

### Critério de aceite

Remover placeholders, revisar descrições e validar o conteúdo das seis trilhas antes da publicação.

---

## B-08 - Overflow horizontal em telas estreitas

- **Tipo:** Bug de responsividade
- **Prioridade Jira:** Low
- **Severidade:** Baixa
- **Componente:** Layout responsivo

### Resultado esperado

O conteúdo deve se adaptar à largura do viewport sem rolagem horizontal involuntária.

### Resultado atual

Em viewport de 708 px, o documento ocupa 947 px, cortando parte do layout e criando barra horizontal.

### Critério de aceite

Validar os principais fluxos em 320 px, 375 px, 768 px e desktop, sem overflow horizontal e sem conteúdo cortado.

---

## B-09 - Erros de texto e título duplicado

- **Tipo:** Bug de conteúdo
- **Prioridade Jira:** Low
- **Severidade:** Baixa
- **Componente:** Conteúdo editorial

### Ocorrências

- “Metiodos de pesquisa” → “Métodos de pesquisa”
- “materais” → “materiais”
- “Algorítmos” → “Algoritmos”
- “HTM CSS” → “HTML e CSS”
- “Trilha de Trilha de UX/UI Design” → revisar título duplicado

### Critério de aceite

Executar revisão ortográfica e validação dos títulos em todas as trilhas.

---

## B-10 - Problemas de semântica e acessibilidade

- **Tipo:** Bug de acessibilidade
- **Prioridade Jira:** Low
- **Severidade:** Baixa
- **Componente:** Acessibilidade / navegação

### Resultado esperado

Ações devem usar elementos semânticos, ter nome acessível e funcionar por teclado e leitor de tela.

### Resultado atual

Ícones de favorito não possuem nome acessível; menus e ações usam elementos genéricos clicáveis em vez de links e botões semânticos.

### Critério de aceite

Adicionar nomes acessíveis, foco visível, navegação por teclado e validação automatizada/manual com ferramenta de acessibilidade.

---

## Plano recomendado de correção

1. Corrigir imediatamente B-01 e executar novo teste de autorização após logout.
2. Corrigir B-02, B-03 e B-04, pois bloqueiam navegação e a jornada principal do estudante.
3. Implementar B-05 e B-06 para completar descoberta de conteúdo e conclusão da jornada.
4. Revisar B-07 a B-10 antes da próxima publicação.
5. Criar testes automatizados para login, logout, rotas protegidas, inscrição, favoritos, busca, progresso e navegação do rodapé.

## Observação sobre MCP/token

Foi utilizada uma única sessão MCP/browser para reduzir consumo. Não foi criado token de autenticação, pois a aplicação não disponibiliza esse recurso e a geração de credenciais estaria fora do escopo do teste.
