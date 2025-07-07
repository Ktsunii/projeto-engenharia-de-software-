# Casos de Teste e Classes de Equivalência - Sistema Meteorológico
A seguir cada caso de equivalencia e teste que fizemos com cada funcionalidade do sistema:
---

## História #17 - Como Usuário urbano quero acessar mapas meteorológicos interativos

**Critérios:** Permite filtros e exportação de imagens  
**Regras:** Exportação com data; limitado a 5 por hora

| Condição de entrada | Classes válidas | Classes inválidas | Classes inválidas |
|---------------------|------------------|--------------------|--------------------|
| Data                | Data válida (1)  | Data impossível (2)| Data com letras (3)|
| Limite por hora     | Dentro do limite (4) | Fora do limite por hora (5) | |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                          | Resultado Esperado        |
|------|--------------------------|-----------------------------------|----------------------------|
| 1    | 1, 4                     | 01/01/2023, 3 exportações         | Exportação realizada       |
| 2    | 2, 4                     | 31/12/2023, 3 exportações         | Exportação não realizada   |
| 3    | 3, 4                     | abc123, 3 exportações             | Exportação não realizada   |
| 4    | 1, 5                     | 01/01/2023, 6 exportações         | Exportação não realizada   |

---

## História #16 - Como Meteorologista quero consultar históricos climáticos por região

**Critérios:** Filtro por data, local  
**Regras:** Histórico mantido por 5 anos; exclusivo a meteorologistas

| Condição de entrada | Classes válidas | Classes inválidas | Classes inválidas |
|---------------------|------------------|--------------------|--------------------|
| Data                | Data válida (1)  | Data impossível (2)| Data com letra (3) |
| Local               | Local existente (4) | Lugar inexistente (5) | Local vazio (6) |
| Perfil              | Sou meteorologista (7) | Não sou meteorologista (8) | |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                      | Resultado Esperado        |
|------|--------------------------|-------------------------------|----------------------------|
| 1    | 1, 4, 7                 | 01/01/2023, São Paulo         | Consulta realizada         |
| 2    | 2, 4, 7                 | 31/12/2023, São Paulo         | Consulta não realizada     |
| 3    | 3, 4, 7                 | abc123, São Paulo             | Consulta não realizada     |
| 4    | 1, 5, 7                 | 01/01/2023, Lugar X           | Consulta não realizada     |
| 5    | 1, 6, 7                 | 01/01/2023, ""                | Consulta não realizada     |
| 6    | 1, 4, 8                 | 01/01/2023, São Paulo         | Consulta não realizada     |

---

## História #10 - Como Gestor de segurança quero registrar ocorrências climáticas e seus impactos

**Critérios:** Deve conter data, local, descrição, fotos  
**Regras:** Dados salvos por 10 anos; visíveis apenas para gestores e meteorologistas

| Condição de entrada | Classes válidas | Classes inválidas | Classes inválidas |
|---------------------|------------------|--------------------|--------------------|
| Data                | Data válida (1)  | Data impossível (2)|                    |
| Local               | Local existente (3) | Local inexistente (4) |               |
| Descrição           | Descrição preenchida (5) | Vazia (6)        |                    |
| Foto                | PNG (7)          | Outro formato (8)  |                    |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                             | Resultado Esperado        |
|------|--------------------------|------------------------------------------------------|----------------------------|
| 1    | 1, 3, 5, 7              | 01/01/2023, São Paulo, "Chuva forte", foto.png      | Registro realizado         |
| 2    | 2, 3, 5, 7              | 31/12/2023, São Paulo, "Chuva forte", foto.png      | Registro não realizado     |
| 3    | 1, 4, 5, 7              | 01/01/2023, Lugar X, "Chuva forte", foto.png        | Registro não realizado     |
| 4    | 1, 3, 6, 7              | 01/01/2023, São Paulo, "", foto.png                 | Registro não realizado     |
| 5    | 1, 3, 5, 8              | 01/01/2023, São Paulo, "Chuva forte", foto.jpg      | Registro não realizado     |

---

## História #8 - Como Jornalista quero receber alertas de mudanças bruscas no tempo

**Critérios:** Notificação enviada com ao menos 1h de antecedência  
**Regras:** Mudança maior que 5°C ou 60% de chance de chuva em 1h gera alerta

| Condição de entrada        | Classes válidas            | Classes inválidas           |
|----------------------------|-----------------------------|------------------------------|
| Configurar tipo de alerta | Gmail ou notificação (1)    | Nenhum selecionado (2)       |
| Alerta ativo              | Alerta ativo (3)            | Alerta desligado (4)         |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                | Resultado Esperado      |
|------|--------------------------|-----------------------------------------|--------------------------|
| 1    | 1, 3                     | Gmail ou notificação, alerta ativo      | Alerta enviado           |
| 2    | 2, 3                     | Nenhum selecionado, alerta ativo        | Alerta não enviado       |
| 3    | 1, 4                     | Gmail ou notificação, alerta desligado  | Alerta não enviado       |

---
## História #7 - Como jornalista quero receber dicas de saúde baseadas no clima

**Critérios:** Geração de dicas com base nas condições atuais  
**Regras:** As dicas devem ser regionalizadas

| Condição de entrada | Classes válidas      | Classes inválidas             | Classes inválidas               |
|---------------------|----------------------|-------------------------------|----------------------------------|
| Local               | Nome de local (1)    | Nome inexistente (2)          | Nome vazio (3)                  |
| Data                | Data válida (4)      | Data fora do intervalo (5)    | Data no passado com previsão falsa (6) |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                     | Resultado Esperado        |
|------|--------------------------|------------------------------|----------------------------|
| 1    | 1, 4                     | São Paulo, 01/01/2023        | Dicas de saúde geradas     |
| 2    | 2, 4                     | Lugar X, 01/01/2023          | Dicas não geradas          |
| 3    | 1, 5                     | São Paulo, 31/12/2023        | Dicas não geradas          |
| 4    | 1, 6                     | São Paulo, 01/01/2022        | Dicas não geradas          |
| 5    | 3, 4                     | "", 01/01/2023               | Dicas não geradas          |

---
## História #6 - Como gestor de segurança quero exportar dados meteorológicos

**Critérios:** Exportação por período e região  
**Regras:** Intervalo máximo de 90 dias por solicitação

| Condição de entrada | Classes válidas        | Classes inválidas       | Classes inválidas             |
|---------------------|-------------------------|--------------------------|-------------------------------|
| Período             | Até 90 dias (1)         | Mais de 90 dias (2)      | Intervalo inválido (3)        |
| Região              | Nome válido (4)         | Nome genérico (5)        | Nome mal formatado/vazio (6) |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                     | Resultado Esperado        |
|------|--------------------------|----------------------------------------------|----------------------------|
| 1    | 1, 4                     | 01/01/2023 - 30/03/2023, São Paulo          | Exportação realizada       |
| 2    | 2, 4                     | 01/01/2023 - 31/12/2023, São Paulo          | Exportação não realizada   |
| 3    | 3, 4                     | 01/01/2023 - 31/12/2023, São Paulo          | Exportação não realizada   |
| 4    | 1, 5                     | 01/01/2023 - 30/03/2023, Brasil             | Exportação realizada       |
| 5    | 1, 6                     | 01/01/2023 - 30/03/2023, ""                 | Exportação não realizada   |

---
## História #5 - Como meteorologista quero receber alertas automáticos sobre inconsistências nos modelos

**Critérios:** Alerta para divergência > 5°C ou 20mm  
**Regras:** Inconsistência relevante se ultrapassa limiar

| Condição de entrada | Classes válidas       | Classes inválidas         | Classes inválidas         |
|---------------------|------------------------|-----------------------------|----------------------------|
| Modelos climáticos  | Divergência > 5°C (1)  | Divergência < 5°C (2)       | Dados ausentes (3)         |
| Local e período     | Correspondentes (4)    | Período desalinhado (5)     | Local indefinido (6)       |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                | Resultado Esperado        |
|------|--------------------------|-----------------------------------------|----------------------------|
| 1    | 1, 4                     | Divergência > 5°C, correspondentes      | Alerta gerado              |
| 2    | 2, 4                     | Divergência < 5°C, correspondentes      | Alerta não gerado          |
| 3    | 3, 4                     | Dados ausentes, correspondentes        | Alerta não gerado          |
| 4    | 1, 5                     | Divergência > 5°C, desalinhado          | Alerta não gerado          |
| 5    | 1, 6                     | Divergência > 5°C, local indefinido     | Alerta não gerado          |

---
## História #4 - Como jornalista quero compartilhar a previsão do tempo

**Critérios:** Compartilhamento em redes sociais  
**Regras:** Link deve ser público ou imagem embutida

| Condição de entrada | Classes válidas        | Classes inválidas         | Classes inválidas         |
|---------------------|-------------------------|----------------------------|----------------------------|
| Período             | Até 90 dias (1)         | Mais de 90 dias (2)        | Intervalo vazio (3)        |
| Formato             | PDF, CSV, XLSX (4)      | Formato não suportado (5)  | Nenhum formato (6)         |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                     | Resultado Esperado        |
|------|--------------------------|----------------------------------------------|----------------------------|
| 1    | 1, 4                     | 01/01/2023 - 30/03/2023, PDF                 | Compartilhamento realizado |
| 2    | 2, 4                     | 01/01/2023 - 31/12/2023, PDF                 | Compartilhamento não realizado |
| 3    | 1, 5                     | 01/01/2023 - 30/03/2023, JPG                 | Compartilhamento não realizado |
| 4    | 3, 4                     | "", PDF                                      | Compartilhamento não realizado |
| 5    | 1, 6                     | 01/01/2023 - 30/03/2023, ""                  | Compartilhamento não realizado |

### Casos de Teste

| Caso | Classes de Equivalência           | Entradas                                          | Resultado Esperado      |
|------|-----------------------------------|---------------------------------------------------|--------------------------|
| 1    | 1, 3, 5, 7, 9, 11                 | 01/01/2023, São Paulo, Boletim, texto, foto.png   | Boletim publicado        |
| 2    | 2, 3, 5, 7, 9, 11                 | 31/12/2023, São Paulo, Boletim, texto, foto.png   | Boletim não publicado    |
| 3    | 1, 4, 5, 7, 9, 11                 | 01/01/2023, Lugar X, Boletim, texto, foto.png     | Boletim não publicado    |
| 4    | 1, 3, 6, 7, 9, 11                 | 01/01/2023, São Paulo, Tipo inválido, texto, png  | Boletim não publicado    |
| 5    | 1, 3, 5, 8, 9, 11                 | 01/01/2023, São Paulo, Boletim, "", png           | Boletim não publicado    |
| 6    | 1, 3, 5, 7, 10, 11                | 01/01/2023, São Paulo, Boletim, texto, .jpg       | Boletim não publicado    |
| 7    | 1, 3, 5, 7, 9, 12                 | 01/01/2023, São Paulo, Boletim, texto, png        | Boletim não publicado    |

---
## História #13 - Como usuário urbano quero ver a previsão do tempo para os próximos 7 dias

**Critérios:** Inclui máxima, mínima, sensação térmica e chance de chuva  
**Regras:** Atualização a cada 3h; fonte oficial

| Condição de entrada | Classes válidas     | Classes inválidas        |
|---------------------|----------------------|---------------------------|
| Localização         | Válida (1)           | Inválida (2)              |
| Atualização         | A cada 3h (3)        | Atualização inválida (4)  |
| Fonte               | Oficial (5)          | Não oficial (6)           |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                      | Resultado Esperado        |
|------|--------------------------|-----------------------------------------------|----------------------------|
| 1    | 1, 3, 5                 | São Paulo, a cada 3h, oficial                 | Previsão exibida           |
| 2    | 2, 3, 5                 | Lugar X, a cada 3h, oficial                   | Previsão não exibida       |
| 3    | 1, 4, 5                 | São Paulo, atualização inválida, oficial     | Previsão não exibida       |
| 4    | 1, 3, 6                 | São Paulo, a cada 3h, não oficial            | Previsão não exibida       |

---
## História #15 - Como gestor de segurança quero receber alertas meteorológicos graves

**Critérios:** Notificação push + e-mail com instruções de segurança  
**Regras:** Apenas com severidade alta/extrema e usuários autorizados

| Condição de entrada | Classes válidas         | Classes inválidas         |
|---------------------|--------------------------|----------------------------|
| Severidade          | Alta/extrema (1)         | Baixa/média (2)            |
| Canal               | Push + e-mail (3)        | Canal inválido (4)         |
| Usuário             | Autorizado (5)           | Não autorizado (6)         |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                      | Resultado Esperado        |
|------|--------------------------|-----------------------------------------------|----------------------------|
| 1    | 1, 3, 5                 | Alta, push + e-mail, autorizado              | Alerta enviado             |
| 2    | 2, 3, 5                 | Baixa, push + e-mail, autorizado             | Alerta não enviado         |
| 3    | 1, 4, 5                 | Alta, canal inválido, autorizado             | Alerta não enviado         |
| 4    | 1, 3, 6                 | Alta, push + e-mail, não autorizado          | Alerta não enviado         |

## História #3 - Como jornalista quero salvar locais favoritos

**Critérios:** Adicionar múltiplos locais organizados por nome e coordenadas  
**Regras:** Sem duplicidade por usuário

| Condição de entrada | Classes válidas       | Classes inválidas         |
|---------------------|------------------------|----------------------------|
| Local               | Adicionado (1)         | Já existente (2)           |
| Múltiplos locais    | Vários (3)             | Limite excedido (4)        |
| Organização         | Organizado (5)         | Desorganizado (6)          |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                 | Resultado Esperado           |
|------|--------------------------|------------------------------------------|-------------------------------|
| 1    | 1, 3, 5                 | SP, RJ, Brasília                         | Locais salvos e organizados  |
| 2    | 2, 3, 5                 | SP, RJ, SP                               | Apenas 2 locais salvos       |
| 3    | 1, 4, 5                 | 6 locais                                 | Apenas 5 locais salvos       |
| 4    | 1, 3, 6                 | SP, RJ, Brasília                         | Locais salvos, desorganizados|

---
## História #12 - Como gerente de desastre quero apertar um botão para sinalizar desastre

**Critérios:** Envia para área padrão  
**Regras:** Não pode cancelar nem reenviar em 24h

| Condição de entrada | Classes válidas      | Classes inválidas         |
|---------------------|-----------------------|----------------------------|
| Botão               | Pressionado (1)       | Não pressionado (2)        |
| Área                | Área enviada (3)      | Área inválida (4)          |
| Avaliação           | Iniciada (5)          | Não iniciada (6)           |
| Cancelamento        | Não cancelado (7)     | Cancelado (8)              |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                  | Resultado Esperado                  |
|------|--------------------------|-------------------------------------------|--------------------------------------|
| 1    | 1, 3, 5, 7              | Pressionado, área padrão, avaliada, não cancelado | Alerta enviado e avaliação iniciada |
| 2    | 2, 3, 5, 7              | Não pressionado, área padrão, avaliação   | Alerta não enviado                   |
| 3    | 1, 4, 5, 7              | Pressionado, área inválida, avaliação     | Alerta não enviado                   |
| 4    | 1, 3, 6, 7              | Pressionado, área padrão, sem avaliação   | Alerta enviado, avaliação não iniciada|
| 5    | 1, 3, 5, 8              | Pressionado, área padrão, avaliação, cancelado | Alerta não enviado               |

---
## História #11 - Como jornalista quero marcar afazeres ao ar livre sem chuva

**Critérios:** Armazenar e alterar segundo clima  
**Regras:** Alterações diárias permitidas

| Condição de entrada | Classes válidas        | Classes inválidas        |
|---------------------|-------------------------|---------------------------|
| Horário             | Armazenado (1)          | Não armazenado (2)        |
| Alteração           | Permitida (3)           | Não permitida (4)         |
| Clima               | Permitido (5)           | Não permitido (6)         |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                | Resultado Esperado        |
|------|--------------------------|-----------------------------------------|----------------------------|
| 1    | 1, 3, 5                 | Armazenado, alteração permitida, clima permitido | Horário alterado          |
| 2    | 2, 3, 5                 | Não armazenado, alteração permitida     | Horário não alterado       |
| 3    | 1, 4, 5                 | Armazenado, alteração não permitida     | Horário não alterado       |
| 4    | 1, 3, 6                 | Armazenado, alteração permitida, clima não permitido | Horário não alterado |

---
## História #9 - Como pessoa urbana quero notificações de resumo climático diário

**Critérios:** Escolha horário, inclui temperatura, eventos extremos  
**Regras:** Envio só se variação >3°C ou eventos severos

| Condição de entrada     | Classes válidas      | Classes inválidas        |
|-------------------------|-----------------------|----------------------------|
| Horário de notificação  | Selecionado (1)       | Não selecionado (2)        |
| Resumo climático        | Enviado (3)           | Não enviado (4)            |
| Variação de temperatura | > 3°C (5)             | ≤ 3°C (6)                  |
| Eventos extremos        | Severos (7)           | Sem eventos (8)            |

### Casos de Teste

| Caso | Classes de Equivalência | Entradas                                         | Resultado Esperado        |
|------|--------------------------|--------------------------------------------------|----------------------------|
| 1    | 1, 3, 5, 7              | Selecionado, enviado, variação > 3°C, severos   | Notificação enviada        |
| 2    | 2, 3, 5, 7              | Não selecionado, enviado, variação > 3°C        | Notificação não enviada    |
| 3    | 1, 4, 5, 7              | Selecionado, não enviado, variação > 3°C        | Notificação não enviada    |
| 4    | 1, 3, 6, 7              | Selecionado, enviado, variação ≤ 3°C            | Notificação não enviada    |
| 5    | 1, 3, 5, 8              | Selecionado, enviado, variação > 3°C, sem evento| Notificação não enviada    |

