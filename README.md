moip-transparente
=================

Recomendações Pré-Instalação:

	1 - Realize um full backup de seu ambiente.
	2 - Remova as versões antigas de nosso módulo e outros módulos de checkout.

Instalação.

	Recomendamos a instalação via Magento Connect, no entanto você poderá realiza-la via ftp usando o nosso git, basta extrair os arquivo e realizar o envio ao seu servidor.
	Após a instalação é recomendavel verificar o nível de pastas de seu magento, use o script fornecido pelo magento para este processo. Subido o arquivo magento-cleanup.php para a raiz de seu ambiente.
	Detalhes da execução do arquivo:
	 - Baixe o arquivo do link: http://www.magentocommerce.com/wiki/_media/groups/227/magento-cleanup2.zip
	 - Descompacte o arquivo e envie via ftp para a raiz do site.
	 - No navegador execute http://SEU_SITE.COM.BR/magento-cleanup.php


Fonte: http://www.magentocommerce.com/wiki/groups/227/resetting_file_permissions


Configuração

Após a instalação, deslogue-se do seu admin e entre novamente, isto corrige o erro 404 que terá ao acessar as guias dos nossos módulos.
Ao logar-se novamente, acesse no menu superior Sistema > Configurações.
Na Lateral do admin haverá a guia MOIP.COM.BR.


	Moip Carrinho:

	Recomendamos atenção unicamente a esses itens a baixo, evite alterar qualquer outro valor:
		- Layout
	 		- Seu Site é Responsivel: 
	 			Informe sim ou não.

		 	- Cor do Chekout:
		 		Informe valores em HEXA sem o uso do "#"

		 	- Cor dos Botões:
		 		Informe valores em HEXA sem o uso do "#"

		 - Box Modal
		 	- Altura: 
		 		Este item se refere ao tamanho que o box para login e visualização dos termos deverá ter. Vale lembrar que muitas vezes você precisará aumentar esse item, pois o tamnho de sea fonte impacta na exibição dele. 
		 		Não usar "px" nem "%", os valores já são por defaul em pixel.

		 	- Largura:
		 		Raramente você precisa alterar mas caso tenha a necessidade coleque o valor desejado.
		 		Não usar "px" nem "%", os valores já são por defaul em pixel.


	===================================================================================


	Moip Avançado:

	Recomendamos atenção unicamente a esses itens a baixo, evite alterar qualquer outro valor:
		
		- Designer
			- Habilitar jquery dos módulos?
				Essa função é para controlar a chamada de jquery versão 1.9 de nossos módulos, verifique em seu ambiente se no checkout a chamadas de outros módulos ou de seu tema que use jquery. Há um video tutorial explicando mais detalhadamente como tratar esse item.
				Caso o seu site possua outros jquery's funcões como CLICAR NO BOTÃO LOGIN, CÁLCULO DE FRETE, BUSCA DE ENDEREÇO e outros poderam não trabalhar corretamente.
				Verifique o video tutorial para maiores informações ->

			- Vai usar o módulo Carrinho MoIP?
				Caso não vá utilizar outro módulo de checkout informe não neste item e direto no arquivo: MOIP_onestepcheckout.xml localizado em app/etc/modules/ altere o valor da linha:
					 <active>true</active> para:  <active>false</active>

		- Google e outras analises - Análise de funil e tag de conversão
			- ID da conta Google:
				Informe o seu ID de sua conta google com o UA- na frente. Exemplo: UA-33860171-1

			- Outras tags de conversão
				Insira, caso possua, outras tags de conversão, Facebook, Google Adwords entre outros oferecem um código para acompanhamento de suas conversões. Esse campo não é obrigatório.


	===================================================================================

	Meios de Pagamento guia Moip Transparente:

	Após concluir todos os testes de funcionamento do módulo realize as alterações recomendadas a baixo:

		- Ambiente
			Essa configuração só poderá ser alterada para quando o módulo já se encontrar disponível para vendas.
			Após altera-lo um novo campo será solicitado:

		- Login Transparente
			É a sua conta moip, você deverá informar o dado que utiliza para logar-se no site moip.com.br, eventualmente seu login poderá ser um email, mas login e email podem ser diferentes dentro do moip.

		- Chave de validação para o retorno do Status
			Você informará um código, que será repassado ao moip na sua transação e este por sua vez irá analisar no momento em que retorna o status do pedido para o seu site.
			Este código é muito importante e evita fraudes no retorno de transação somente você deverá ter acesso a ele. 
			Utileze apenas Letras e Números não coloque caracter especial como ç%$$$ nem mesmo palavras com acentos á é í ó ú...

		- Nome Fantasia da Loja
			Este campo será visualizado na fatura do cartão e em seu boleto bancário, por isto atenção com ele.

		- Receber o valor do parcelamento à vista?
			Somente alterar com a permissão de seu gerente de conta, ou por informação prestada em nossa central de atendimento.

		- Formas de Pagamento
			- Utilize o shift para marcar qual a forma de pagamento que deseja utilizar.

		- Enviar email a cada alteração de status ao cliente
			Este campo controla somente o envio do email: Alteração no Status de seu Pedido. Você poderá notificar seu cliente dos processos de análise de pagamento, impressão do boleto bancário, cancelamento de um pedido ou mesmo aprovação do pagamento.

		- Número Máximo de Parcelas Permitido
			Informe a quantidade de parcelas que deseja trabalhar em seu site. O máximo permitido pelos nosso cartões são de 12x.

		- Valor Mínimo das Parcelas
			Informe o valor mínimo que as parcelas podem ter. Lembre-se que essa regra que tem prioridade inferior ao item acima (Número Máximo de Parcelas Permitido). Ou seja:
			Se este campo atual tem valor de 5 reais, mas o item anterior tem valor 5, uma compra de 100 reais só poderá oferecer parcelamento até no máximo 20 reias.
			Vide mais detalhes no video tutorial ->

		- Usar juros composto?
			Somente alterar com a permissão de seu gerente de conta, ou por informação prestada em nossa central de atendimento.

		- 1° - Parcelas de
		- 1° - Parcelas até
		- 1° - Juros de (%)
			Esses ítens são tratados em conjunto, com eles você controla questões de parcelamento em seu ambiente, vamos simular que você quer oferecer o pagamento em até 12x no cartão de crédito com juros de 2.99, para uma parcela mínima de 5 reais.
			Você então deverá configurar os itens na seguinte ordem:
				- 1
				- 12
				- 2.99 
				(não usar no último ítem vírgulas, usar apenas o ponto "." )
			Outra possibilidade:
				Oferecer Pagamento em 4x sem juros, para isto você deverá configurar os itens na seguinte ordem:
				 - 1
				 - 4
				 - 0
				 Nesta modalidade as demais parcelas (caso não limete o número de parcelas a 4 no item (Número Máximo de Parcelas Permitido)) aparecerão com juros, ou seja de 1 a 4 vezes sem juros de 5 a 12 com juros.

		- Dias de Vencimento para o Boleto: 
			Definir em dias corridos os valores e valores inteiros, exemplo:
				- Boletos com 3 dias para efetuar o pagamento: 
					Coloque no Campo o valor 3

===================================================================================

ERRO 404 AO ACESSAR A GUIA DO MÓDULO:

	Basta deslogar-se do admin e logar-se novamente.

===================================================================================


USO DO MOIP TRANSPARENTE COM OUTROS MÓDULOS DE CHECKOUT.

	Após instalar o pacote completo do nosso módulo vá a: 
		MOIP_onestepcheckout.xml localizado em app/etc/modules/ altere o valor da linha:
				 de:
				 	<active>true</active> 
				 para:
				   <active>false</active>

	Após isto é necessário apenas ajuste no css do módulo.
	Oferecemos suporte para que caso realizado esse processo acima não consiga ainda a utilização do moip em seu checkout.

===================================================================================


BOTÃO COMPRAR NÃO FUNCIONA, BOTÃO LOGIN NÃO FUNCIONA, BOTÃO TERMOS DE COMPRA NÃO FUNCIONAM.

	Esse erro é proveniente da falha de js. O primeiro passo para a correção é alterar o valor do Habilitar jquery dos módulos? localizado em:
		Sistema > Configurações > Moip Avançado > Guia Designer
	Caso este processo não corriga o problema verifique em nosso tutorial como soluciona-lo ->


===================================================================================


BUSCA CEP RETORNA OUTRO ESTADO:
	
	Este erro é proveniente de values para os campos estado não conformes, Verifique em nosso tutorial como trata-los ->


