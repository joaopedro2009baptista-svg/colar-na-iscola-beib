
## Diagnóstico adicional após vídeo de teste

A gravação mostrou instalação bem-sucedida do ícone `caminhoneiro`, seguida de tela preta e encerramento imediato. A inspeção Mach-O confirmou que o executável depende de `@rpath/llama.framework/llama`, mas a IPA anterior não continha `Payload/EstudaOffline.app/Frameworks/llama.framework/llama`. Esse era o motivo técnico do crash no launch, independente da assinatura aplicada depois.

A correção adiciona uma fase `Embed Frameworks` com `CodeSignOnCopy` e `RemoveHeadersOnCopy`, define `@executable_path/Frameworks` no `LD_RUNPATH_SEARCH_PATHS` e faz o workflow falhar se o framework não estiver presente na IPA. O novo build precisa ser instalado e assinado novamente; a IPA anterior não deve ser reutilizada.
