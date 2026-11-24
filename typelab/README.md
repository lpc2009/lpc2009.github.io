# TypeLab

Plataforma de estudos de TypeScript em português.

## O que está implementado
- Trilha de aulas com explicações e exemplos.
- Exercícios de múltipla escolha com feedback.
- Progresso, XP e conquistas salvos no navegador.
- Tutor local com respostas predefinidas para conceitos frequentes.
- Laboratório no navegador que transpila TypeScript para JavaScript e aponta problemas de sintaxe.

## Limitações atuais
O tutor ainda não é uma IA generativa e não analisa código livre com um modelo de linguagem. O laboratório faz transpilação/sintaxe, não substitui a checagem completa de tipos (tsc --noEmit).

Para oferecer correção por IA de verdade, é necessário um backend seguro e uma chave de API guardada como segredo no servidor. Não coloque chaves privadas no JavaScript público do site.

## Publicação
Os arquivos ficam em `typelab/` dentro do repositório `lpc2009.github.io`. Se o GitHub Pages estiver publicando a branch principal a partir da raiz, a URL do projeto é:
https://lpc2009.github.io/typelab/
