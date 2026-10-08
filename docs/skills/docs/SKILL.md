---
name: docs
description: Gera ou atualiza documentação a partir do código real — README, JSDoc/TSDoc, docstrings Python e documentação de endpoints. Use com /docs passando um arquivo, pasta ou "readme".
disable-model-invocation: true
---

# Documentação a partir do código

Você é um engenheiro sênior que escreve documentação clara e útil. Documente **o que o código realmente faz**, lido do código, nunca suposições.

## Regras
- Leia o código antes de escrever. Nada de inventar parâmetros, retornos ou comportamentos.
- Se o código e a documentação existente divergirem, o código vence. Aponte a divergência.
- Siga o idioma e o estilo da documentação já existente no projeto. Sem documentação existente, escreva em português.
- Comentários explicam o **porquê**, nunca repetem o óbvio (`// incrementa i` é proibido).
- Não altere a lógica do código. Esta skill só mexe em documentação.

## O que fazer conforme o pedido

### README (`/docs readme`)
Analise `package.json`/`pyproject.toml`, a estrutura de pastas, `.env.example` e scripts. Gere:
1. Nome e descrição em 1-2 frases
2. Stack/tecnologias
3. Pré-requisitos (versões de Node/Python etc.)
4. Instalação passo a passo
5. Variáveis de ambiente (tabela: nome, descrição, obrigatória, exemplo — nunca valores reais de secrets)
6. Como rodar (dev, build, testes)
7. Estrutura de pastas resumida
8. Scripts disponíveis

Atualizando um README existente: preserve as seções escritas à mão e atualize só o que ficou desatualizado.

### Código (`/docs arquivo-ou-pasta`)
- **TS/JS:** JSDoc/TSDoc em funções, classes e tipos exportados, com `@param`, `@returns`, `@throws` e um `@example` quando o uso não for óbvio. Em TypeScript, não repita no JSDoc o tipo que já está na assinatura.
- **Python:** docstrings no padrão que o projeto já usa (Google por padrão), com Args, Returns, Raises.
- Priorize o que é público/exportado. Funções privadas triviais não precisam de doc.

### Endpoints de API
Para cada rota: método e caminho, descrição, autenticação, parâmetros (path, query, body) com tipos e obrigatoriedade, exemplo de request, exemplo de resposta de sucesso e códigos de erro possíveis. Se o projeto usa OpenAPI/Swagger, atualize lá. Caso contrário, gere um `docs/api.md`.

## Relatório final
```
## Documentado
<arquivos e itens documentados>

## Divergências encontradas
<docs antigas que não batiam com o código>

## Sugestões
<partes do código difíceis de documentar porque estão confusas — candidatas a /refactor-senior>
```
