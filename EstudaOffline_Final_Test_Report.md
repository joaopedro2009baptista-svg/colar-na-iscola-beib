# caminhoneiro — relatório técnico da revisão final

Data da revisão: 2026-10-28

## Implementado

- Inferência local via `llama.cpp` usando o modelo GGUF Qwen3-4B Q4_K_M.
- Download na primeira utilização, fora da IPA, com persistência em `Application Support/Models`.
- Validação de status HTTP, tamanho esperado, assinatura GGUF, SHA-256, arquivo temporário e substituição atômica.
- Retomada de download interrompido quando o servidor suporta `Range`; reinício seguro quando a retomada não é aceita.
- Verificação final do arquivo antes de disponibilizá-lo ao runtime.
- Cabeçalho GGUF verificado novamente antes de abrir o arquivo no runtime local.
- OCR local por Vision e RAG baseado em `CurriculumKnowledge.md` preservados.
- Nome visível definido como `caminhoneiro`; Bundle Identifier preservado como `br.estudaoffline.app`.
- Workflow configurado para arquivar, empacotar, testar o ZIP da IPA, validar `Info.plist`, executável e base curricular, e publicar IPA, archive e logs.

## Validações realizadas nesta revisão

- Fonte final empacotada em `Eee_FINAL_iOS_Source.zip` e verificada com `unzip -t`.
- URL oficial do modelo conferida no Hugging Face: `Qwen/Qwen3-4B-GGUF`, arquivo `Qwen3-4B-Q4_K_M.gguf`.
- SHA-256 conferido no metadata oficial do repositório: `7485fe6f11af29433bc51cab58009521f205840f5b4ae3a32fa7f92e8534fdf5`.
- Tamanho esperado conferido no metadata oficial: `2,497,280,256` bytes.
- Verificação estática dos símbolos de download, hash, GGUF, runtime `llama_model_load_from_file`, nome visível e Bundle Identifier.
- Busca de APIs iOS 17 problemáticas citadas na migração anterior: nenhuma ocorrência encontrada.

## O que o build do GitHub Actions deve provar

- Compilação e archive em runner macOS com `xcodebuild`.
- Construção do XCFramework atual do `llama.cpp`.
- Existência do executável dentro do `.app`.
- IPA ZIP estruturalmente válido (`unzip -t`).
- `Info.plist` válido e presença de `CurriculumKnowledge.md`.
- Publicação do arquivo `.ipa`, do `.xcarchive` e do log de validação como artefatos.

## Ainda não afirmado como aprovado

- Não há simulador iOS nem iPhone físico neste ambiente Linux para executar a UI, Vision OCR ou inferência real.
- A abertura do GGUF e a geração de tokens local dependem de teste em dispositivo iOS após o download de aproximadamente 2,5 GB.
- A IPA é deliberadamente não assinada; instalação em iPhone requer assinatura/provisionamento Apple válidos.
- O download do modelo não é incluído na IPA e, portanto, não pode ser validado offline antes da primeira aquisição do modelo.

A conclusão do build não será interpretada como aprovação desses itens pendentes; eles permanecem explicitamente separados acima.
