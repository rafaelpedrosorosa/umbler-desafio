# Parte 4 – E-mail e Deliverability (Exim)

Eu começaria verificando os logs do Exim para identificar se os e-mails estão sendo enviados, rejeitados ou permanecendo na fila.

```bash
tail -f /var/log/exim/mainlog
tail -f /var/log/exim/rejectlog
exim -bp
```

Também verificaria os registros DNS do domínio, principalmente SPF, DKIM, DMARC e PTR (Reverse DNS), pois eles ajudam a validar a autenticidade dos e-mails enviados.

Para verificar problemas de reputação, consultaria ferramentas como MXToolbox e Spamhaus para identificar se o IP está em alguma blacklist.

Se forem encontrados problemas nos registros DNS, trataria como problema de configuração. Caso os registros estejam corretos e o IP esteja listado em blacklist, a causa provavelmente está relacionada à reputação do IP.

Durante a investigação manteria o cliente informado sobre o andamento da análise, explicando de forma simples o que está sendo verificado e quais ações serão tomadas para normalizar a entrega dos e-mails.

