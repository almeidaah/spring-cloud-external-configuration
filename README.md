# spring-cloud-external-configuration
Spring Cloud project with external configuration properties.

This project reads form configuration-service to a real repository at github containing application1.properties.
<b>https://github.com/almeidaah/springcloudfileconfig.git</b>


Você sobe o CLIENT E O SERVICE.

1 - No Configuration-client há um arquivo em resources = bootstrap.properties que contém o nome da aplicação cliente(application1) e o host do servidor do spring cloud(Configutarion-service)

2 - O Configuration-service possui o application.properties que apontará para onde estará o arquivo properties(neste caso, no GitHub) necessário para realizar as configurações do client(application1)

3 - O Configuration-service aponta para o repositório do GIT onde está o application1.properties (application1 é o nome definido no configuration-client, por isso ele encontra o arquivo)

4 - Com o arquivo application1.properties carregado pelo service, a aplicação(client) agora tem acesso às propriedades definidas no servidor.

5 - O client, ao chamar o endpoint '/message', buscará no arquivo .properties o valor para a variável e injetará a mesma na resposta.

OBS: caso o arquivo de properties seja alterado, o cliente não precisa ser parado, apenas chama-se o endpoint http://localhost:8080/refresh via método POST para que as propriedades sejam atualizadas no cliente.
