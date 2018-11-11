![alt tag](https://wiki.postgresql.org/images/3/30/PostgreSQL_logo.3colors.120x120.png)

Scripts para particionamento do banco de dados do banco do zabbix(postgresql).

Nota: 
   O uso desses scripts assim como os possiveis danos ou perda de dados causados ao banco de dados e de inteira responsabilidade do usuarios.
   
   Esses scripts sao destinados a ambientes de laboratorio.

# ° NOTAS DE VERSÃO

°  Versão 1.0 - 11/11/2018 ==> Criação do Repositorio.

# ° PRÉ-REQUISITO

Banco de dados postgres instalado e configurados.

# Copiar os sql para a pasta /var/lib/postgresql

# ALTERAR O OWNER DOS ARQUIVOS SQL PARA O USUARIO POSTGRES

  chown postgres.postgres /var/lib/postgresql/*.sql
                                                
# LOCAR COM O USUARIO POSTGRES
  su - postgres
  cd ~  

# PARTICIONAR O BANCO DE DADOS(DEVE SER APLICADO PELO USUARIO POSTGRES)
  psql -U postgres -W -d zabbix < schema.sql
    
  psql -U postgres -W -d zabbix < trg_partition.sql
     
  psql -U postgres -W -d zabbix < trigger.sql

# Verificando a tabela de histórico
  zabbix=> \d+ history;

# FONTe
Todos os procedimentos de particionamento do banco de dados executados acima foram extraídos da documentação oficial, no link a baixo:

https://zabbix.org/wiki/Docs/howto/zabbix2_postgresql_autopartitioning

