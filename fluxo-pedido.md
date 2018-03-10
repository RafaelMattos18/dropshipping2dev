# Fluxo Pedido

O próximo passo é se preparar para receber um novo pedido de a ConnectParts, para isso deve ser criada uma API para receber um novo pedido. 

Segue abaixo objeto que será enviado pela ConnectParts:



```
string NomeComprador  //Nome do cliente
int TipoPessoa   //Tipo de pessoa, 1 para física 2 para jurídica
string CpfCnpj  
string TipoDocumento
string TipoComprador   //(INDUSTRIA, COMERCIO, OUTRAS)
bool ContribuidorIcms 
bool Suframa 
string SuframaNumero 
bool SuframaPisCofins 
string Telefone 
string Celular 
string EmailCliente 
string Endereco 
string EnderecoNumero 
string EnderecoEntrega 
string Cep 
string Cidade 
string CidadeEntrega 
string EstadoEntrega 
string Pais 
string NumeroPedido 
int? CodigoIbge 
decimal ValorVenda 
int QuantidadeVendida 
string TipoFrete 
Lista ItensCompra 
             Objeto Intes de compra
             string CodigoProduto 
             int Quantidade     
             decimal TotalDoProduto 
             decimal ValorUnitario 

```

Após a emissão da nota de compra (**_para connect_**) /de venda (**_para o fornecedor_**) pelo ERP deve ser comunicado esse faturamento para a nossa API 

http://integra02.connectparts.com.br:8032/dropshipping/PedidoCompra/Inserir

Com o **JSon**: 

```
{
  "PedidoFornecedorCodigo": "string",
  "Notafiscal": "string",
  "Valor": 0,
  "PedidoCompraProdutos": [
    {
      "PedidoCompraCodigo": "string",
      "ProdutoCodigo": "string",
      "Quantidade": 0,
      "PrecoUnitario": 0
    }
  ]
}

```

**Observação importante:**
> Todos os valores praticados pelo ERP da Connect Parts são em inteiro, nesse caso o Json de vocês os números decimais no caso Valor, Quantidade e PrecoUnitario devem ser multiplicados por 100 e então ter seus zeros após a virgula removidos, por exemplo:
> Quantidade = 1,00 * 100 => Quantidade = 100,00 
> Então devem ser removidos os 00 após a virgula, tornando em 100, um número inteiro.

Com essas informações e com a **API de Download XML/DANFE** a ConnectParts consegue emitir a nota de venda para o cliente e então nós comunicaremos o faturamento para a API de vocês que deve ser criada para receber um objeto assim: 

```
string NumeroNotaFiscal
string NumeroPedido
DateTime DataEmissao
string ChaveNotaFiscal 
string CodigoRastreio 
```

A empresa fornecedora deve disponibilizar um FTP, onde será inserida a DANFE da nota fiscal faturada pela Connect Parts. **Essa inserção é feita em um intervalo de 10 minutos**.

Agora a empresa fornecedora é responsável por emitir uma nota fiscal de remessa, e então ao ser transmitida pelo ERP deveremos ser comunicados disso com um post na API

[http://integra02.connectparts.com.br:8032/dropshipping/NotafiscalRemessa/Inserir](http://integra02.connectparts.com.br:8032/dropshipping/NotafiscalRemessa/Inserir)

**Com o objeto:**

```
{
  "PedidoCodigo": "string",
  "Rastreio": "string",
  "Chave": "string",
  "Numero": "string",
  "DataEmissao": "string"
}
```