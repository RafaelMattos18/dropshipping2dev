# Pendencia

Em caso de pendencia o fornecedor deve comunicar a API com um POST

[http://integra02.connectparts.com.br:8032/dropshipping/PedidoFornecedorPendencia/Inserir](http://integra02.connectparts.com.br:8032/dropshipping/PedidoFornecedorPendencia/Inserir)

**Com o objeto **

```text
{
  "PedidoFornecedorCodigo": "string",
  "FabricacaoCodigo": "string",
  "ProdutoCodigo": "string",
  "FornecedorCodigo": "00000000-0000-0000-0000-000000000000",
  "Motivo": "string",
  "DataPrevisao": "string"
}
```

