# Introducao

O dropshipping é uma técnica de gestão da cadeia logística na qual a CONNECTPARTS não mantém os produtos em estoque. Nesta técnica os produtos ficam disponíveis em todos os canais de venda da ConnectParts \(Loja virtual, Marketplaces e Mercado Livre\) e sempre que uma venda é realizada utilizamos o estoque do parceiro que realiza o envio da mercadoria diretamente do seu CD.

Quando um cliente adquire um produto Dropshipping, realizamos todas as análises necessárias e assim que aprovarmos o pagamento do pedido \(entre status ‘’pronto para manuseio’’ e ‘’preparando entrega’’ – conforme imagem abaixo\) a ConnectParts gera um pedido de compra dentro do seu ERP \(Ábacos\) de acordo com a tabela de preços fornecida pelo fornecedor parceiro \(A Connect Parts deve ser comunicada sobre qualquer alteração da tabela de preços com 20 dias de antecedência\).

![Fluxo 01 Dropshipping](http://developers.connectparts.com.br/imagens/drop2/dropforn01.png)

No momento em que o pedido de compra é inserido no ERP será disparada uma ordem de compra para o fornecedor e no mesmo momento é enviado o pedido do cliente. Após finalização das etapas acima, o fornecedor emite uma NF de venda do produto pra ConnectParts, que dará entrada na Nota Fiscal e fará o faturamento enviando a nota fiscal para o fornecedor que realizará o processo de embalagem, emissão de etiqueta e nota fiscal de venda da Connect e envio diretamente ao cliente.

A mercadoria só será enviada ao cliente via transportadora/correios após a ConnectParts enviar a NF de faturamento desse produto para o fornecedor e o mesmo emitir a NF de remessa / de NF de faturamento e etiqueta para acompanhar a mercadoria até o cliente.

Haverá uma informação na política de entrega do nosso site: "_**Por questões operacionais relativas à Logística é possível que a postagem e entrega dos produtos ocorram em dias diferentes**_". Quando um pedido dropshipping for faturado pela Connect, ele não será despachado pela Connect, dessa forma assim que ele for faturado, a Logística da Connect altera o status no ERP para despachado, lembrando que o pedido será despachado até 24 horas conforme informamos no e-mail para o cliente.

