# tf_22_04

🧪 Cenário do teste

Foi utilizada uma estrutura de árvore genealógica com 15 níveis de profundidade, onde cada nível representa uma geração ligada por um campo filho.

O objetivo foi avaliar:

Facilidade de inserção
Complexidade da consulta no nível mais profundo
Legibilidade
Esforço de desenvolvimento
🐘 PostgreSQL (JSONB)
✔ Inserção

A inserção foi realizada com sucesso utilizando o tipo JSONB.
O banco aceitou a estrutura profundamente aninhada sem problemas.

🔍 Consulta (nível 15)

A consulta exigiu o uso repetitivo de operadores:

dados->'filho'->'filho'->'filho'...
⚠ Dificuldades encontradas
A consulta se torna extremamente longa e difícil de escrever
Alta dependência da estrutura exata (se mudar um nível, quebra tudo)
Baixa legibilidade
Difícil manutenção
Maior chance de erro humano
💡 Observação técnica

Apesar do PostgreSQL suportar JSONB, ele é um banco relacional.
Consultas em profundidade não são o foco principal da ferramenta.

🍃 MongoDB
✔ Inserção

A inserção foi mais natural, pois o MongoDB é orientado a documentos.
A estrutura foi inserida diretamente como um objeto JSON.

🔍 Consulta (nível 15)

A consulta foi feita usando dot notation:

filho.filho.filho.filho...
✅ Vantagens observadas
Consulta mais simples e direta
Melhor legibilidade
Menor esforço para escrever
Mais intuitivo para estruturas hierárquicas
⚠ Limitações
Ainda depende da profundidade fixa
Estruturas muito profundas também podem se tornar difíceis de manter
⚖️ Comparação Geral
Critério	PostgreSQL (JSONB)	MongoDB
Inserção	Funciona bem	Mais natural
Consulta	Complexa e longa	Simples e direta
Legibilidade	Baixa	Alta
Manutenção	Difícil	Moderada
Adequação ao cenário	Média	Alta
🧠 Conclusão
O PostgreSQL conseguiu lidar com o JSON, mas demonstrou limitações práticas ao trabalhar com muitos níveis de profundidade.
O MongoDB se mostrou mais eficiente e natural para esse tipo de estrutura hierárquica.
Mesmo assim, nenhum dos dois modelos é ideal para profundidades extremas, sendo mais recomendado o uso de estruturas com referência (ex: parent_id) em cenários reais.
