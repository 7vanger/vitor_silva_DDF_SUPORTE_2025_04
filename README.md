# vitor_silva_DDF_SUPORTE_2025_04

*Case 1*
*Item Troubleshooting:* Imagine que você é um analista de suporte e recebe um chamado do cliente reportando um problema na importação dos dados da Dadosfera. Você deve responder como se estivesse interagindo com o cliente no atendimento do chamado. O erro ocorreu nesta pipeline de coleta na Dadosfera. Sugira a alteração a ser feita no Dataset e escreva sobre outros cuidados que nosso usuário deve ter quando carregar dados do Google Sheets para a plataforma. Utilize a documentação da Dadosfera para entender como baixar os logs.

Resolução: 
O erro que está ocorrendo é por conta que a planilha que a plataforma está tentando acessar não têm permissões de autenticação necessárias para o acesso a planilha e com isso ocorre o erro na importação. O que se deve fazer nesse caso é verificar: 

  1° Se dentro da script no formato json contem as permissões para que a plataforma acesse a planilha como, "https://www.googleapis.com/auth/spreadsheet", se não houver, atualizar.

  2° Se há uma scrpit no formato json onde cria o fluxo para o envio da planilha para a plataforma, e se não houver criar o script por exemplo: exemplo.json

      {
      ...
      "oauthScopes": [
        "https://www.googleapis.com/auth/spreadsheets.readonly",
        "https://www.googleapis.com/auth/userinfo.email"
      ],
      ...
      }

Se tiver mais dúvidas pode perguntar, e segue abaixo o link da documentação google referente a essa ação:

  https://developers.google.com/apps-script/concepts/scopes?hl=pt-br

--------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------
*Case 2* *Item processos internos:* Imagine que a Dadosfera está passando por um upgrade e incorporando uma nova plataforma de gerenciamento de diretório em nuvem, com SSO e recursos de ciclo de vida do usuário. Como você organiza e implementa esses marcos para garantir uma transição suave e eficiente? Isso pode impactar o caso anterior? Explique como se daria cada interação com a base de clientes, de forma que eles se preparem para a mudança.

Resolução: 
Para essa mudança é necessária envolver todas as partes interessadas, criar um plano de comunicação claro e transparente com todos os envolvidos, realizar o backup dos dados, oferecer suporte contínuo aos colaboradores durante a transição como também a comunicação e interação com os clientes a deixar eles a parte da mudança que vai ocorrer, com isso alguns pontos:

 *Planejamento e análise:* 
  * Mapeamento das partes interessadas; 
  * avaliação dos riscos e desafios; 
  * Elaboração de um cronograma.

 *Planejamento técnico:* 
  * Levantar os requisitos técnicos e os impactos operacionais; 
  * Criação de um roadmap compartilhável com os stakeholders internos e externos; 
  * Bateria de teste para buscar uma melhor performance da plataforma e como está sendo suportada.

 *Comunicação com os clientes:* 
  * Realizar o aviso prévio com o contexto sobre a mudança e datas; 
  * Canal de suporte sendo email e/ou chat exclusivo para dúvidas relacionadas a transição; 
  * Central de ajuda com perguntas frequentes; 
  * E outra opção seria a migração assistida para os clientes com os dados mais críticos ou todos os clientes.

E com relação ao caso anterior, pode afetar sim, depedendo do caminho do endereço da plataforma pode gerar outro tipo de erro de acesso, como também permissões alteradas ou depreciação da permissão. Outro ponto a se antentar é o modo de acessar a nova plataforma se restringe a outros tipos de envios de arquivos.

---------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------

*Case 3* *Item Boas-Práticas de Suporte*: Suponha que você tenha acesso a uma ferramenta de Chatbot com AI robusta que possa ser integrada à Dadosfera para melhorar a interação do cliente. Como você implementaria essa ferramenta para melhorar a satisfação e o envolvimento do cliente?

Desenhe o processo do fluxo do processo de atendimento, incluindo interações entre usuário, máquina (IA como o GPT ou outra), documentação (docs.dadosfera.ai) e humano (Suporte Dadosfera).

Exemplifique, com um print de um prompt e uma resposta, como que uma IA poderia ajudar nesse atendimento. Sugerimos o uso de ChatGPT ou Bard.

Resolução:
Com relação a essa propota de implementação do chatbot primeiro realizaria um mapeamento de perguntas e dores frequentes como coleta de dados históricos e tickets, outro ponto seria o treinamento e personalização da IA sendo moldada pelos documentos da dadosfera para entender todo o processo dentro das atividades. Integração com o site/suporte da Dadosfera sendo uma adição de um botão de chat no portão e se o chat não conseguir resolver o problema é aberto um ticket com todo o contexto do usuário e do erro já estruturado para o humano.

*Processo de fluxo de atendimento*
![image](https://github.com/user-attachments/assets/96468f51-e099-4a88-bcce-4884127df261)


*Exemplo de prompt de um cliente com o chatbot*
  ![image](https://github.com/user-attachments/assets/1a40422b-2ba9-4c34-830f-7b959086e32d)

--------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------

*Case 4* *Item Consultas SQL*

Criação da tabela referente a toda informação da tablea disponibilizada

    select *
    
    from TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB

![cropped-image-1744411532992lq9je](https://github.com/user-attachments/assets/93302bbf-0c0b-42be-8659-4d6d2985dc0b)

Criação do gráfico pizza referente a informação da quantidade de deparamentos

    select  
        a.DEPARTMENT,
        count(*) as Quantity
    
    from TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB as a

![cropped-image-1744411532992lq9je (1)](https://github.com/user-attachments/assets/3916d03f-3c5d-4e9d-a0d0-8c04b3ddcdf4)


Criação das barras laterais referente a informação da quantidade de cargos

    select 
        JOBROLE,
        count(*) as Quantidade

    from TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB

![cropped-image-17444116430742z1pa (1)](https://github.com/user-attachments/assets/447be366-afde-4270-8e92-3fb169b8f505)


Criação das barras verticais referente a informação da média de idade em cada cargo ocupado

    select
        JOBROLE as cargo,
        avg(age) as idade
    
    from TB__YCYBP3__CASE_TECNICO_EMPLOYEE_TB

![cropped-image-17444116430742z1pa](https://github.com/user-attachments/assets/c6bc5347-96e6-4866-8a81-752689b273b5)

