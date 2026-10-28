
## Diagnóstico do segundo vídeo

O crash ocorria ao tocar em `Resolver todas as questões` depois do OCR. O runtime criava `llama_batch` com capacidade de apenas 512 tokens, mas o texto OCR e o prompt curricular podiam ultrapassar esse limite. `addToken` então escrevia fora dos buffers nativos e o iOS encerrava o processo sem mensagem. A capacidade foi ajustada para 4096, igual ao contexto máximo, e a geração agora para antes de ultrapassar o contexto.

As imagens selecionadas também são reduzidas para no máximo 2048 px antes do Vision OCR, diminuindo o pico de memória e mantendo resolução suficiente para texto impresso. Redação e Chat agora têm foco explícito, dismiss interativo e botão `Concluído` na barra do teclado.
