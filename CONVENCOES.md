# Convenções do estúdio interativo

## Intercom

- **ENG** — linha técnica entre DTV, Videoman e câmeras.
- **PRD** — linha de produção compartilhada por todas as estações.
- **PGM** — retorno de intercom das estações para escuta no sistema.

Estas designações devem ser usadas de forma consistente em todos os equipamentos e diagramas do projeto.

## Interface e responsividade

As páginas de equipamentos devem preservar primeiro o funcionamento do simulador. Melhorias de layout não podem substituir, envolver ou reescrever o JavaScript operacional já validado.

- Cada equipamento mantém seu próprio JavaScript. Não usar uma camada global de popup, zoom ou responsividade injetada em todas as páginas.
- O contexto usa um **drawer local** da própria página. Ele fica fora da área do desenho, abre após clicar em um controle e nunca sobrepõe o aparelho.
- O drawer fecha pelo botão **×**, pela tecla **Esc** e por clique fora do drawer e fora de um controle interativo.
- O botão de fechar pertence ao drawer local e não deve compartilhar seletor ou handler com modais do rack.
- Em telas estreitas, SVGs devem usar largura responsiva, `min-width: 0` e margem lateral. Evitar rolagem horizontal.
- Equipamentos naturalmente largos devem ser reduzidos dentro da viewport em vez de criar barra horizontal.
- Em painéis densos, como RCP-1500 e WFM-5000, o zoom deve preservar contexto visual e deixar espaço vertical para a explicação e os botões de teste.
- Textos descritivos curtos ficam abaixo da figura. Explicações detalhadas ficam no drawer.
- Alterações visuais devem preservar os handlers existentes dos controles. Não trocar `$`/`$$` nem reescrever seletores de coleção sem validação.
- Não usar scripts ou CSS legados `ubq-*` / `UBIQUIDADE` nas páginas novas ou revisadas.

## Validação antes de publicar

Antes de considerar uma página validada:

1. Todos os blocos `<script>` devem passar pelo parser JavaScript.
2. Não pode haver `$$$()`, `$().forEach` para coleções nem IDs JavaScript inexistentes no HTML.
3. O clique em um controle deve continuar executando a função original e abrir apenas o drawer de contexto.
4. O drawer deve fechar em **×**, **Esc** e clique externo.
5. A página não pode depender de `ubq-mobile-layer` nem do CSS global antigo.
6. Em viewport vertical, o aparelho deve caber sem barra horizontal.
7. Para controles que alteram estado visual, a mudança deve permanecer perceptível com o drawer aberto.
