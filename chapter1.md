# Autenticação


O Primeiro passo é realizar a autenticação, para isso deve acessar a API de autenticação.
 
[http://integra02.connectparts.com.br:8032/swagger/ui/index#!/OAuth/OAuth_Token](http://integra02.connectparts.com.br:8032/swagger/ui/index#!/OAuth/OAuth_Token)

Para recuperar o token bearer deve-se autenticar passando usuário e senha por um get, como no exemplo abaixo:

[http://integra02.connectparts.com.br:8032/OAuth/Token?username=teste&password=teste](http://integra02.connectparts.com.br:8032/OAuth/Token?username=teste&password=teste)

A resposta para essa execução é o seguinte json, nele é possível notar o acess_token, e com ele você pode fazer as requisições em nossas API’s.
