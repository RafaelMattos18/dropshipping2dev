# Estoque

O segundo passo é alimentar o estoque. O endereço de **homologação** para isso é:

[http://integra02.connectparts.com.br:8034/dropshipping/Estoque/Atualizar](http://integra02.connectparts.com.br:8034/dropshipping/Estoque/Atualizar)

Nesse endereço deve ser fazer um POST com o seguinte **JSon**:

```text
{
  "CodigoFabricacao": "string",
  "CodigoProduto": "string",
  "SaldoDisponivel": 0,
  "FornecedorCodigo": "00000000-0000-0000-0000-000000000000",
  "Sucesso": true
}
```

### Pontos importantes

> 1. Apenas um dos campos entre **CodigoFabricao** ou **CodigoProduto** deve ser preenchido. Caso você opte por utilizar o CodigoFabricacao esse é o código do produto no ERP do fornecedor, o outro, CodigoProduto se refere ao código da connectparts.
> 2. O **FornecedorCodigo** é um Guid único que se refere ao fornecedor, para recupera-lo basta realizar um GET na API: **URL de Homologação:** [http://integra02.connectparts.com.br:8034/dropshipping/Fornecedor/Listar](http://integra02.connectparts.com.br:8034/dropshipping/Fornecedor/Listar)
> 3. O **SaldoDisponivel** é a quantidade de estoque do produto.
> 4. A frequência dessa alimentação vai variar de fornecedor para fornecedor.

