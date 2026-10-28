# Estuda Offline — expansão curricular e build remoto

A base curricular local foi ampliada para Português e Literatura, Inglês, Matemática I, Matemática II, Química, Física, Biologia, História, Geografia, Filosofia, Sociologia e Redação. Cada seção contém conceitos, fórmulas quando aplicáveis, exemplos, contrastes, erros comuns e instruções de raciocínio. O app continua usando RAG textual local; isso não altera os pesos do Qwen nem constitui treinamento supervisionado do modelo.

A recuperação foi melhorada para dividir o Markdown em blocos por títulos, ranquear sobreposição de termos e aplicar reforço para a disciplina escolhida. O contexto enviado ao modelo permanece limitado para evitar carregar toda a base em cada pergunta.

O `llama.xcframework` passou a ser uma referência explícita da fase de frameworks do projeto. Como o binário não deve ser versionado no repositório, foi incluído um workflow GitHub Actions em macOS que clona o llama.cpp, gera o XCFramework para iOS, executa `xcodebuild archive` sem assinatura e publica `EstudaOffline-unsigned.ipa` como artefato.

A IPA gerada pelo workflow será compilada, mas não será instalável pelo ESign sem assinatura Apple compatível. Para produzir uma IPA assinada, ainda são necessários certificado de distribuição, chave privada, provisioning profile, Bundle ID e secrets configurados no GitHub Actions. Nenhuma IPA foi declarada como pronta antes da execução real do workflow.

Validações locais concluídas: 12 seções curriculares presentes, 14.611 caracteres de base, 15 arquivos Swift, referência do XCFramework no `project.pbxproj`, workflow com `xcodebuild archive` e ausência de dependências de Foundation Models, ChatGPT ou API externa no código Swift.
