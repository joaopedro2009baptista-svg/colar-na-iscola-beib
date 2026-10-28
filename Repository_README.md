# Estuda Offline — iOS com LLM local

Fonte atualizada do aplicativo SwiftUI Estuda Offline. O pacote completo está em [`EstudaOffline_iOS_Updated_Source.zip`](./EstudaOffline_iOS_Updated_Source.zip), acompanhado do [relatório de implementação](./EstudaOffline_Implementation_Report.md).

A fonte usa OCR local com Vision e inferência GGUF por llama.cpp. O modelo Qwen3-4B Q4_K_M não está incluído no repositório por ter aproximadamente 2,5 GB; o app o baixa sob demanda, verifica o SHA-256 e armazena-o localmente.

Este repositório contém a fonte e a documentação. A IPA ainda precisa ser compilada em um Mac com Xcode, testada em um iPhone real e assinada com certificado e provisioning profile compatíveis com o ESign. Consulte o README dentro do ZIP para os passos de integração do `llama.xcframework`.
