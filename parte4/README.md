# Parte 4 – E-mail e Deliverability (Exim)

Eu começaria verificando os logs do Exim para identificar se as mensagens estão sendo entregues, rejeitadas ou permanecendo na fila de envio.

```bash
tail -f /var/log/exim/mainlog
tail -f /var/log/exim/rejectlog
exim -bp
```

Nos logs eu procuraria erros de autenticação, rejeições por políticas anti-spam, problemas de DNS, falhas de conexão com servidores remotos e mensagens acumuladas na fila.

Também verificaria os registros DNS do domínio, principalmente:

* SPF
* DKIM
* DMARC
* PTR/rDNS (Reverse DNS)

Esses registros são importantes para validar a autenticidade dos e-mails enviados e reduzir a possibilidade de classificação como spam.

Para verificar problemas de reputação, consultaria ferramentas como MXToolbox e Spamhaus para identificar se o IP de envio está presente em alguma blacklist.

Se forem encontrados erros nos registros DNS ou na configuração do servidor de e-mail, trataria como problema de configuração. Caso os registros estejam corretos e o IP esteja listado em blacklist ou possua histórico de bloqueios, a causa provavelmente estará relacionada à reputação do IP.

Durante toda a investigação manteria o cliente informado sobre o andamento da análise, explicando de forma simples o que está sendo verificado, os possíveis impactos identificados e as ações necessárias para normalizar a entrega dos e-mails.

