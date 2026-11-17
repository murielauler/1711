# Regras da escola para os números de mensalidades

Kensington International School. Use sempre estas regras ao analisar a base de mensalidades exportada do sistema. Elas valem para qualquer mês.

## Antes de calcular: limpar a base

1. **Boleto repetido.** O mesmo `ID_Boleto` em mais de uma linha é reprocessamento do sistema. Vale uma linha por boleto.
2. **Valor em centavos.** Mensalidade acima de R$ 100.000 foi exportada em centavos. Divida por 100 as colunas `Valor_Mensalidade`, `Desconto`, `Valor_Cobrado` e `Valor_Pago` dessa linha.
3. **Status desatualizado.** Boleto "Em aberto" com vencimento já passado está vencido. Vale a data de vencimento, não o status.
4. **Aluno é a matrícula.** Identifique o aluno pela coluna `Matricula`, nunca pelo nome.
5. **Só mensalidade.** Os três números usam apenas as linhas com `Tipo` igual a Mensalidade. Rematrícula 2027 e Matrícula 2027 ficam fora e são informadas à parte.

A data-base é a data da exportação informada no pedido. Se ela não vier no pedido, pergunte.

## 1. Alunos ativos

Matrículas com boleto de mensalidade na competência mais recente da base, com status diferente de Cancelado e de Trancado.

- Bolsista integral (status Isento) é aluno ativo.
- Quem só tem Matrícula 2027 ainda não é aluno.

## 2. Faturamento do mês

Soma do `Valor_Cobrado` das mensalidades da competência pedida, sem os boletos cancelados.

- É o valor cobrado, não o valor recebido.
- O valor recebido (`Valor_Pago`) é informado à parte.

## 3. Inadimplência

Inadimplência é o valor de mensalidades vencidas **há mais de 30 dias** e ainda não pagas, dividido pelo valor cobrado dessas mesmas mensalidades.

- **Entra no valor em atraso:** boleto vencido há mais de 30 dias sem pagamento. No pagamento parcial, entra só o saldo (`Valor_Cobrado` menos `Valor_Pago`).
- **Não entra no valor em atraso:** dívida em **Acordo**. Ela é carteira renegociada e é informada à parte.
- **Fora da conta toda:** boletos vencidos há 30 dias ou menos, cancelados e trancados.
- **Divisor:** soma do `Valor_Cobrado` de todas as mensalidades vencidas há mais de 30 dias, sem cancelados e trancados. Os boletos em acordo continuam no divisor.

Informe sempre à parte: o valor em acordo e o valor vencido há 30 dias ou menos.

## Como entregar

1. Uma tabela com os três números: alunos ativos, faturamento do mês e inadimplência. Use R$ em milhões com duas casas e percentual com uma casa.
2. As limpezas feitas, com a quantidade de linhas de cada uma.
3. Até três pontos de atenção para a diretoria.
4. No fim, os três números em uma linha.

Se aparecer um caso que estas regras não cobrem, pergunte antes de assumir.
