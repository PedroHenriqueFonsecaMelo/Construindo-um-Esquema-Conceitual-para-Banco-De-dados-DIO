# Construindo-um-Esquema-Conceitual-para-Banco-De-dados-DIO

Descrição do Desafio
Agora você irá criar um esquema conceitual do zero. A partir da narrativa fornecida você será capaz de criar todas as entidades, relacionamentos e atributos. Caso encontre algo que não foi definido na narrativa, utilize a sua compreensão do contexto e deixe uma descrição no README do seu github. para verificação.

O esquema deverá ser adicionado a um repositório do Github para futura avaliação do desafio de projeto. Adicione ao Readme a descrição do projeto conceitual para fornecer o contexto sobre seu esquema.

Objetivo:
Cria o esquema conceitual para o contexto de oficina com base na narrativa fornecida

Narrativa:
Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica
Clientes levam veículos à oficina mecânica para serem consertados ou para passarem por revisões  periódicas
Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma OS com data de entrega.
A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra
O valor de cada peça também irá compor a OSO cliente autoriza a execução dos serviços
A mesma equipe avalia e executa os serviços
Os mecânicos possuem código, nome, endereço e especialidade
Cada OS possui: n°, data de emissão, um valor, status e uma data para conclusão dos trabalhos.
Agora é a sua vez de ser o protagonista! Implemente o desafio sugerido pela expert e suba seu projeto para um repositório próprio, com isso, você aumentará ainda mais seu portfólio de projetos no GitHub!

![image](https://github.com/user-attachments/assets/2fc0ddf8-93d3-463b-93d6-482a0f5d2e2e)

// Diagrama UML - Oficina Mecânica

// Cliente e Veículo
[Cliente|Nome VARCHAR(100); Telefone VARCHAR(15); Endereço VARCHAR(255)]1-*[Veículo|Placa VARCHAR(10); Modelo VARCHAR(50); Ano INT(4); Marca VARCHAR(50)]

// Veículo e Ordem de Serviço (OS)
[Veículo]1-*[Ordem_de_Serviço|N° INT(10); Data_Emissão DATE(); Valor_Total DECIMAL(10,2); Status VARCHAR(20); Data_Conclusão DATE()]

// OS é preenchida por uma Equipe de Mecânicos
[Ordem_de_Serviço]1-1>[Equipe|ID INT(10); Nome_Equipe VARCHAR(100)]

// Equipe é composta por Mecânicos
[Equipe]1-*[Mecânico|Código INT(10); Nome VARCHAR(100); Endereço VARCHAR(255); Especialidade VARCHAR(50)]

// OS tem Serviços a serem realizados
[Ordem_de_Serviço]1-*[Serviço|Descrição VARCHAR(255); Valor DECIMAL(10,2); Tempo_Estimado INT(4)]

// OS pode incluir Peças para substituição
[Ordem_de_Serviço]1-*[Peça|Código INT(10); Descrição VARCHAR(255); Valor_Unitário DECIMAL(10,2)]

// Tabela de Referência para cálculo de mão de obra
[Serviço]1-1>[Tabela_Referencia|Código INT(10); Descrição VARCHAR(255); Valor_Mão_de_Obra DECIMAL(10,2)]

// Cliente autoriza OS antes da execução
[Cliente]1-1>[Autorização_OS|ID INT(10); Data DATE(); Status_Autorização VARCHAR(20)]
