
## Otimização para provas longas

O fluxo de resolução foi otimizado para não executar revisões duplicadas em todas as questões. A extração usa no máximo 700 tokens e não inclui a base curricular; cada questão usa no máximo 280 tokens, e uma segunda tentativa de 220 tokens só ocorre quando a opção é ilegível ou o JSON não contém uma alternativa. O contexto curricular por questão foi reduzido para 4.500 caracteres, o OCR é limitado a 24.000 caracteres e a resolução limita-se às primeiras 30 questões por execução. A tela agora oferece `Cancelar resolução` e verifica cancelamento entre questões.

Esses limites reduzem o tempo e o consumo de memória no iPhone, mas a inferência local de um modelo de 4B parâmetros ainda depende do desempenho do dispositivo.
