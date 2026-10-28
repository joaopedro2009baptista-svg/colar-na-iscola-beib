# Estuda Offline — relatório desta entrega

## Executado

- Projeto ZIP extraído e revisado: 18 arquivos originais.
- Runtime local atualizado em `Services/LocalLlamaRuntime.swift` com API alinhada ao exemplo Swift oficial atual do llama.cpp.
- Adicionados cancelamento cooperativo via `Task.checkCancellation()`, limpeza de memória, `unloadModel()` e liberação de sampler, batch, contexto, modelo e backend.
- Gerenciamento do GGUF atualizado com download por `URLSessionDownloadTask`, progresso, cancelamento, `resumeData`, SHA-256, armazenamento em Application Support, exclusão e carregamento/descarregamento.
- Tela de modelo atualizada com progresso, bytes, cancelar/retomar, carregar, descarregar e excluir.
- SHA-256 registrado para `Qwen3-4B-Q4_K_M.gguf`: `7485fe6f11af29433bc51cab58009521f205840f5b4ae3a32fa7f92e8534fdf5`.
- Deployment target alterado para iOS 16.4, coerente com o script oficial atual do XCFramework; adicionada descrição de uso da câmera.
- Adicionado `scripts/prepare_llama_xcframework.sh` para clonar o llama.cpp e executar `build-xcframework.sh ios-sim ios-device` em um Mac.
- README atualizado com fontes, licença Apache-2.0 do modelo, hash, limitações e passos de compilação/assinatura.

## Verificações executadas

- Referências de arquivos do `project.pbxproj`: PASS, 16 referências verificadas.
- Arquivos Swift presentes: 15.
- Base curricular presente: 7.617 bytes.
- Varredura do código Swift por FoundationModels, ChatGPT e api.openai.com: nenhum resultado.
- Verificação de presença do hash documentado e script executável: PASS.
- Empacotamento do projeto atualizado em ZIP: concluído.

## Não executado por bloqueio do ambiente

Este ambiente é Linux e não possui Xcode, SDK iOS, `xcodebuild`, `xcrun`, simulador, iPhone conectado, certificado Apple ou provisioning profile. Por isso não foram executados build iOS, testes de integração no aparelho, benchmark de latência/memória, teste em modo avião, Archive, exportação IPA ou assinatura ESign.

Também não foi incluído o binário `llama.xcframework` nem o GGUF de aproximadamente 2,5 GB. O script e o README explicam a geração do framework no Mac; o app baixa e verifica o GGUF em primeira execução.

## Resultado

A entrega é uma fonte atualizada e verificável, não uma IPA pronta. A conclusão operacional exige executar o script em um Mac, adicionar o XCFramework ao target no Xcode, compilar para o iPhone 15 Pro Max, testar os fluxos com o GGUF e somente então exportar/assinar a IPA com credenciais válidas.
