# Fluxo pedido

O próximo passo é se preparar para receber um novo pedido de a ConnectParts, para isso deve ser criada uma API para receber um novo pedido.

Segue abaixo objeto que será enviado pela ConnectParts:

```text
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

Após a emissão da nota de compra \(_**para connect**_\) /de venda \(_**para o fornecedor**_\) pelo ERP deve ser comunicado esse faturamento para a nossa API

### **URL Pedido de Compra \(homologação\):**

* [http://integra02.connectparts.com.br:8034/dropshipping/PedidoCompra/Inserir](http://integra02.connectparts.com.br:8034/dropshipping/PedidoCompra/Inserir)

Com o **JSon**:

```text
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

### **Observação importante:**

> Todos os valores praticados pelo ERP da Connect Parts são em inteiro, nesse caso o Json de vocês os números decimais no caso Valor, Quantidade e PrecoUnitario devem ser multiplicados por 100 e então ter seus zeros após a virgula removidos, por exemplo:  
> Quantidade = 1,00 \* 100 =&gt; Quantidade = 100,00  
> Então devem ser removidos os 00 após a virgula, tornando em 100, um número inteiro.

Com essas informações e com a **API de Download XML/DANFE** a ConnectParts consegue emitir a nota de venda para o cliente e então nós comunicaremos o faturamento para a API de vocês que deve ser criada para receber um objeto assim:

```text
string NumeroNotaFiscal
string NumeroPedido
DateTime DataEmissao
string ChaveNotaFiscal 
string CodigoRastreio
```

A empresa fornecedora deve disponibilizar um FTP, onde será inserida a DANFE da nota fiscal faturada pela Connect Parts. **Essa inserção é feita em um intervalo de 10 minutos**.

Agora a empresa fornecedora é responsável por emitir uma nota fiscal de remessa, e então ao ser transmitida pelo ERP deveremos ser comunicados disso com um post na API

### **URL de Nota Fiscal Remessa Inserir \(homologação\):**

* [http://integra02.connectparts.com.br:8034/dropshipping/NotafiscalRemessa/Inserir](http://integra02.connectparts.com.br:8034/dropshipping/NotafiscalRemessa/Inserir)

**Com o objeto:**

```text
{
  "PedidoCodigo": "string",
  "Rastreio": "string",
  "Chave": "string",
  "Numero": "string",
  "DataEmissao": "string"
}
```

Assim que a mercadoria for despachada, deve ser acionada a API com um POST

### **URL de Nota Fiscal Remessa Despacho \(homologação\):**

[http://integra02.connectparts.com.br:8034/dropshipping/NotafiscalRemessa/NotificarDespacho](http://integra02.connectparts.com.br:8034/dropshipping/NotafiscalRemessa/NotificarDespacho)

**Com um objeto **

```text
{
  "PedidoCodigo": "string",
  "DataDespacho": "2018-03-10T12:16:45.224Z"
}
```

---

## Recepção passiva do pedido

Iremos disponibilizar uma API onde o cliente poderá consultar informações sobre o seu pedido. 

**Observações**

- A API da Connectparts será atualizada _real-time_.
- O tempo de consulta externa do cliente, será determinada pelo mesmo.
- Após o consumo das informações sobre o pedido, o cliente terá que alterar o status deste pedido, para retirada deste da listagem.
