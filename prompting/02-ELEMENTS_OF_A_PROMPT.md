# Elementos de um Prompt

Conforme cobrimos mais exemplos e aplicações de engenharia de prompt, você notará que certos elementos compõem um prompt.

Um prompt pode conter qualquer um dos seguintes elementos:

- **Instrução** (*Instruction*): uma tarefa ou instrução específica que você deseja que o modelo execute.

- **Contexto** (*Context*): informações externas ou contexto adicional que podem direcionar o modelo a respostas melhores.

- **Dados de Entrada** (*Input Data*): a entrada ou pergunta para a qual estamos interessados em obter uma resposta.

- **Indicador de Saída** (*Output Indicator*): o tipo ou formato esperado da resposta.

Para demonstrar melhor esses elementos, veja um prompt simples que visa realizar uma tarefa de classificação de texto:

*Prompt*

```text
Classifique o texto em neutro, negativo ou positivo

Texto: Eu achei a comida razoável.

Sentimento:
```

No exemplo acima, a instrução corresponde à tarefa de classificação: `"Classifique o texto em neutro, negativo ou positivo"`. Os dados de entrada correspondem à parte `"Eu achei a comida razoável."`, e o indicador de saída utilizado é `"Sentimento:"`. Observe que este exemplo básico não utiliza um contexto explícito, mas ele também poderia ser fornecido. Por exemplo, o contexto para esta classificação poderia ser exemplos adicionais incluídos no prompt para ajudar o modelo a entender melhor a tarefa e alinhar o tipo de resposta esperada.

Você não precisa de todos os quatro elementos em um único prompt; o formato correto depende da tarefa a ser executada.

## Créditos da Fonte Original

Este material foi traduzido e adaptado a partir do conteúdo original fornecido pelo **Prompt Engineering Guide**.

- **Fonte Original:** https://www.promptingguide.ai/
- **Projeto de Origem:** DAIR AI (Democratizing AI Research and Education)