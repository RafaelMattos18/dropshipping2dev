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


