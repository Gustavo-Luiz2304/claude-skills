# claude-skills

Marketplace de plugins do Claude Code (`gl-skills`).

## refactor-senior

Refatoração de código nível sênior: mapeia o código em blocos, diagnostica code smells por severidade, aplica refatorações seguras em passos pequenos **sem mudar o comportamento** e entrega um relatório final no estilo code review.

A skill só roda quando chamada explicitamente com `/refactor-senior`.

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

### 3. Instale o plugin

```
/plugin install refactor-senior@gl-skills
```

Se o Claude Code pedir, escolha o escopo da instalação (só para você ou para o projeto) e confirme.

### 4. Reinicie o Claude Code

Saia com `/exit` e abra de novo com `claude` para carregar o plugin.

### 5. Confira se instalou

Digite `/plugin` e veja se `refactor-senior` aparece na lista de plugins instalados.

### 6. Use a skill

Chame o comando passando o que deve ser refatorado:

```
/refactor-senior src/services/pedido.ts
```

Também funciona colando um trecho de código logo depois do comando.

## Atualizar

Para buscar a versão mais recente:

```
/plugin marketplace update gl-skills
/plugin update refactor-senior@gl-skills
```

> Os comandos também funcionam direto no terminal, fora do Claude Code: troque `/plugin` por `claude plugin` (ex.: `claude plugin install refactor-senior@gl-skills`).

## Desinstalar

```
/plugin uninstall refactor-senior@gl-skills
/plugin marketplace remove gl-skills
```
