# Analisador Sintático - Trabalho de Compiladores

**Autores:** Luiz Augusto Dalla Rosa e Luiz Henrique Zucchi Menosso  
**Data de Entrega:** 05/06/2025

---

## Gramática Proposta

S::= aAb | bBc | cCd
A::= aDa | bAb
B::= bCD | ε
C::= cAB | aDb
D::= dSa | cBd

---

## Conjuntos FIRST

S = a, b, c
A = a, b
B = b, ε
C = a, c
D = c, d

---

## Conjuntos FOLLOW

S = $, a
A = b, c, d
B = c, d
C = c, d
D = a, b

---

## Tabela de Parsing

|              | a            | b            | c            | d            | $   |
|--------------|--------------|--------------|--------------|--------------|-----|
| **S**        | S → aAb      | S → bBc      | S → cCd      | -            | -   |
| **A**        | A → aDa      | A → bAb      | -            | -            | -   |
| **B**        | -            | B → bCD      | B → ε        | B → ε        | -   |
| **C**        | C → aDb      | -            | C → cAB      | -            | -   |
| **D**        | -            | -            | D → cBd      | D → dSa      | -   |

---

## Como Utilizar o Analisador

1. **Faça o Download** do projeto.

2. **Abra o arquivo `index.html`** no seu navegador.

3. Existem **três formas principais de criar a sentença** que será analisada:

   - **Digitando no campo com a label "Sentença"**:  
     - Permite escrever qualquer sentença, sem limite de tamanho ou restrição de caracteres.  
     - Se a sentença contiver símbolos inválidos para a gramática, o erro será detectado durante a validação.

   - **Clicando no botão ao lado do campo "Sentença Aleatória"**:  
     - Gera automaticamente uma sentença **válida**, com tamanho máximo de **20 caracteres**.  

   - **Interagindo com a Tabela de Parsing**:  
     - É possível clicar nas **células azuis** da Tabela de Parsing exibida na página.  
     - A sentença será construída a partir das produções clicadas.  
     - Essa forma **permite criar sentenças inválidas**.  
     - Para limpar a sentença gerada dessa forma, basta clicar no botão **"Resetar Derivações"** abaixo da Tabela de Parsing.

4. **Após inserir a sentença (digitando):**
   - É necessário **clicar fora do campo de texto** para que o evento `onblur` do JavaScript seja acionado.  
   - Isso habilita os botões de validação:  
     - **"Direta"**  
     - **"Passo a Passo"**

5. **Sobre a Validação:**
   - Ao clicar em **"Direta"**, o analisador processa toda a sentença de uma vez.
   - Ao clicar em **"Passo a Passo"**, será adicionado um botão no rodapé do card da **Tabela de Validação**, permitindo que o usuário avance **um passo por vez** no processo.
   - Ao final da validação:
     - Se a sentença for aceita, a tabela será destacada em **verde**.
     - Se houver erro, será destacada em **vermelho**.
     - Será mostrada a **quantidade de iterações** até ocorrer a Aceitação ou o Erro.

---

### Observação

Para facilitar a visualização, o desenvolvimento e a entrega, **todo o código JavaScript do ANALISADOR está embutido diretamente no `index.html`**.  
Não foi realizada a separação entre HTML e JS neste projeto.
