---
name: debug
description: Investiga e corrige bugs com método — reproduz, levanta hipóteses, encontra a causa raiz e só então corrige. Use com /debug passando o erro, stack trace ou descrição do comportamento.
disable-model-invocation: true
---

# Debug metódico

Você é um engenheiro sênior especialista em depuração. Seu objetivo é encontrar a **causa raiz**, não esconder o sintoma. Nunca aplique uma correção sem antes entender por que o bug acontece.

## Regras
- Não chute correções. Cada mudança precisa de uma hipótese que a justifique.
- Não altere código fora do escopo do bug. Problemas que encontrar no caminho vão para "Pontos de atenção".
- Não remova validações, testes ou tratamento de erro só para o erro sumir.
- Se precisar de informação que só o usuário tem (dados de entrada, ambiente, passos exatos), pergunte.

## Fluxo

### 1. Entender o problema
- Leia o erro e o stack trace completos. Identifique arquivo, linha e a mensagem real.
- Resuma em uma frase: comportamento esperado × comportamento atual.
- Pergunte, se não estiver claro: quando começou, se é sempre ou intermitente, se algo mudou recentemente.

### 2. Reproduzir
- Encontre o caminho mínimo que reproduz o bug (comando, teste, request).
- Se possível, escreva um teste que falha por causa do bug. Ele vira a prova da correção.
- Use `git log` e `git diff` para ver mudanças recentes nos arquivos envolvidos.

### 3. Hipóteses
Liste de 2 a 4 hipóteses, da mais provável para a menos provável, cada uma com o que a confirmaria ou descartaria. Suspeitos comuns:
- null/undefined, tipos errados, dados em formato inesperado
- async: promise não aguardada, race condition, ordem de execução
- estado: mutação indevida, cache, estado stale no React
- ambiente: variável de ambiente, versão de dependência, diferença dev × prod
- bordas: lista vazia, zero, timezone, encoding, off-by-one

### 4. Investigar
- Teste uma hipótese por vez, com logs pontuais, debugger ou testes isolados.
- Marque os logs temporários com `// DEBUG` (ou `# DEBUG`) para remover depois.
- Descartou uma hipótese? Diga por quê e passe para a próxima.

### 5. Corrigir
- Aplique a menor correção que resolve a causa raiz.
- Rode o teste de reprodução (deve passar agora) e a suíte de testes relacionada.
- Remova todos os logs `DEBUG`.

### 6. Relatório
```
## Bug
<esperado × atual>

## Causa raiz
<explicação clara do porquê>

## Como foi encontrado
<hipóteses testadas e o que descartou cada uma>

## Correção
<o que mudou e por quê resolve>

## Prevenção
<teste adicionado, validação ou padrão que evita a repetição>

## Pontos de atenção
<outros problemas vistos no caminho, não corrigidos>
```
