# Estoque

O segundo passo é alimentar o estoque. O endereço para isso é:

http://integra02.connectparts.com.br:8032/dropshipping/Estoque/Atualizar

Nesse endereço deve ser fazer um POST com o seguinte json:

```
{
  "CodigoFabricacao": "string",
  "CodigoProduto": "string",
  "SaldoDisponivel": 0,
  "FornecedorCodigo": "00000000-0000-0000-0000-000000000000",
  "Sucesso": true
}
```


