# Teste exploratório - Trilhas do Conhecimento

Documentação do teste exploratório realizado na aplicação [Trilhas do Conhecimento](https://trilha-de-conhecimento.netlify.app/).

## Objetivo

Avaliar os principais fluxos públicos e autenticados da plataforma:

- Login e logout
- Navegação pelas trilhas
- Inscrição em uma trilha
- Área do estudante
- Favoritos
- Busca de conteúdos
- Menu e rodapé
- Certificado
- Responsividade e acessibilidade

## Resultado

Foram identificados 10 problemas:

| Severidade | Quantidade | Identificação |
|---|---:|---|
| Crítica | 1 | Acesso indevido após logout |
| Alta | 3 | Comunidade, rodapé e progresso |
| Média | 3 | Busca, certificado e conteúdo incompleto |
| Baixa | 3 | Responsividade, textos e acessibilidade |

O problema mais grave é a permanência de dados da estudante em uma rota protegida após o logout.

## Documentos

- [Documentação para Jira](documentacao-jira-teste-exploratorio.md): tickets individuais com prioridade, passos para reproduzir, resultado esperado, resultado atual e critérios de aceite.
- [Relatório visual em HTML](relatorio-teste-exploratorio.html): versão formatada para leitura e exportação em PDF pelo navegador.

## Evidências principais

- Login, inscrição e inclusão de favorito funcionaram.
- A busca por `Figma` não filtrou os conteúdos.
- Os itens “Comunidade” e as ações do rodapé não apresentaram navegação.
- A trilha permaneceu como “Não Iniciado” após ser acessada.
- Após o logout, a rota `/student/.../my-list` continuou exibindo dados da estudante.
- Em viewport de 708 px, a página ocupou 947 px de largura e apresentou overflow horizontal.

## Recomendações prioritárias

1. Corrigir a proteção das rotas e a limpeza da sessão após logout.
2. Implementar progresso persistente e o fluxo de certificado.
3. Corrigir menus, links do rodapé e busca.
4. Revisar conteúdo, responsividade e acessibilidade.
5. Criar testes automatizados para autenticação, autorização, inscrição, favoritos, busca, progresso e navegação.

## Como usar no Git

```bash
git init
git add README.md documentacao-jira-teste-exploratorio.md relatorio-teste-exploratorio.html
git commit -m "docs: adiciona documentação do teste exploratório"
```

Para publicar em um repositório remoto:

```bash
git remote add origin URL_DO_REPOSITORIO
git branch -M main
git push -u origin main
```

## Segurança

Nenhuma senha ou token foi incluído nos arquivos. O teste utilizou uma conta autorizada e uma única sessão MCP/browser para reduzir consumo. A aplicação não disponibilizou recurso de criação de token.

## Data do teste

26/08/2026
