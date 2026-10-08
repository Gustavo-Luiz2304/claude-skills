# claude-skills

Marketplace de plugins do Claude Code (`gl-skills`).

## Plugins

Todas as skills só rodam quando chamadas explicitamente pelo comando.

| Plugin | Comando | O que faz |
| --- | --- | --- |
| `refactor-senior` | `/refactor-senior` | Refatoração de código nível sênior: mapeia o código em blocos, diagnostica code smells por severidade e aplica refatorações seguras **sem mudar o comportamento**. |
| `debug` | `/debug` | Debug metódico: reproduz o bug, levanta hipóteses, acha a causa raiz e só então corrige. |
| `docs` | `/docs` | Gera e atualiza documentação a partir do código real: README, JSDoc/TSDoc, docstrings Python e endpoints de API. |

## Passo a passo de instalação

### Pré-requisito

Ter o [Claude Code](https://claude.com/claude-code) instalado e funcionando. Para conferir, rode no terminal:

```
claude --version
```

### 1. Abra o Claude Code

No terminal, entre na pasta de qualquer projeto e rode:

```
claude
```

### 2. Adicione o marketplace

Dentro do Claude Code, digite:

```
/plugin marketplace add Gustavo-Luiz2304/claude-skills
```

Isso registra o marketplace `gl-skills` a partir deste repositório.

### 3. Instale os plugins

Instale só os que quiser:

```
/plugin install refactor-senior@gl-skills
/plugin install debug@gl-skills
/plugin install docs@gl-skills
```

Se o Claude Code pedir, escolha o escopo da instalação (só para você ou para o projeto) e confirme.

### 4. Reinicie o Claude Code

Saia com `/exit` e abra de novo com `claude` para carregar os plugins.

### 5. Confira se instalou

Digite `/plugin` e veja se os plugins aparecem na lista de instalados.

### 6. Use as skills

```
/refactor-senior src/services/pedido.ts
/debug TypeError: Cannot read properties of undefined (reading 'id') em src/api/user.ts
/docs readme
/docs src/utils
```

Também funciona colando um trecho de código logo depois do comando.

## Atualizar

Para buscar a versão mais recente:

```
/plugin marketplace update gl-skills
/plugin update refactor-senior@gl-skills
/plugin update debug@gl-skills
/plugin update docs@gl-skills
```

> Os comandos também funcionam direto no terminal, fora do Claude Code: troque `/plugin` por `claude plugin` (ex.: `claude plugin install debug@gl-skills`).

## Desinstalar

```
/plugin uninstall refactor-senior@gl-skills
/plugin uninstall debug@gl-skills
/plugin uninstall docs@gl-skills
/plugin marketplace remove gl-skills
```
