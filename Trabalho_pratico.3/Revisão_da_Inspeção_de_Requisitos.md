# Correção de historias do usuario
Conforme a revisão demonstrou haviam algumas historias crieterio e regras de negocios que precisavam ser corrigidas, disponivel a seguir algumas dessas correções:

# Como gestor de segurança quero exportar dados meteorológicos para relatórios gerenciais. #6 <br>
### Critérios de Aceitação
O usuário pode escolher o período e região dos dados meteorológicos a serem exportados.
A exportação deve estar disponível nos formatos PDF, CSV e XLSX
### Regras de Negócio
A exportação de dados meteorológicos é permitida para um intervalo máximo de 90 dias por solicitação.
## Alteração 
Adição de criterios e regras de negocio:
A exportação deve estar disponível nos formatos PDF, CSV e XLSX
<br>
<br>
# Como Meteorologista quero consultar históricos climáticos por região. #16<br>
### Critérios:
Filtro por data, local.
### Regras:
Histórico mantido por 5 anos; exclusivo a meteorologistas.
## Alteração
remoção do filtro por tipo de dado
<br>
<br>
# Como meteorologista quero receber alertas automáticos sobre inconsistências nos modelos climáticos. #5<br>
### Critérios de Aceitação
O sistema deve monitorar automaticamente os modelos climáticos
Um alerta deve ser gerado quando houver diferença significativa entre modelos para o mesmo local e período (por exemplo, mais de 5°C ou mudança brusca de condição).
### Regras de Negócio
A inconsistência é considerada relevante quando ultrapassa um limiar configurável (ex: diferença de temperatura > 5°C ou precipitação > 20mm).
O sistema deve registrar os alertas gerados, inclusive os que foram ignorados ou sinalizados como falso positivo.
## Alteração
Adição:
Critérios de Aceitação e Regras de Negócio e A inconsistência é considerada relevante quando ultrapassa um limiar configurável (ex: diferença de temperatura > 5°C ou precipitação > 20mm).
