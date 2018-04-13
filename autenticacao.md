# Autenticacao

O Primeiro passo é realizar a autenticação, para isso deve acessar a API de autenticação.

**URL de Homologação:**

[http://integra02.connectparts.com.br:8034/swagger/ui/index\#!/OAuth/OAuth\_Token](http://integra02.connectparts.com.br:8034/swagger/ui/index#!/OAuth/OAuth_Token)

Para recuperar o token bearer deve-se autenticar passando usuário e senha por um get, como no exemplo abaixo:

**URL de Homologação:**

[http://integra02.connectparts.com.br:8034/OAuth/Token?username=teste&password=teste](http://integra02.connectparts.com.br:8034/OAuth/Token?username=teste&password=teste)

A resposta para essa execução é o seguinte json, nele é possível notar o acess\_token, e com ele você pode fazer as requisições em nossas API’s.

![autenticacao](http://developers.connectparts.com.br/imagens/drop2dev/img01.png)

