# INTRODUÇÃO NMAP - Aula prática
Nmap scan report for scanme.nmap.org (45.33.32.156)

Host is up (0.33s latency).

Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f

Not shown: 994 closed tcp ports (conn-refused)

PORT      STATE SERVICE    VERSION
- 22/tcp    open  ssh        OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
- 80/tcp    open  http       Apache httpd 2.4.7 ((Ubuntu))
- 2000/tcp  open  tcpwrapped
- 5060/tcp  open  tcpwrapped
- 9929/tcp  open  nping-echo Nping echo
- 31337/tcp open  tcpwrappedService Info: OS: Linux; CPE: cpe:/o:linux:linux_kernelnmap -sV -T4 

As portas abertas e seus respectivos serviços são:
22/tcp - ssh
80/tcp - http
2000/tcp - tcpwrapped
5060/tcp - tcpwrapped
9929/tcp - nping-echo
31337/tcp - tcpwrapped

outras 994 portas estão fechadas

## CENÁRIO A

22/tcp - ssh
80/tcp - http
3306/tcp - mySQL

## CENÁRIO B

- **filtered (Filtrada):** O Nmap não consegue determinar se a porta está aberta ou fechada. Isso acontece porque um dispositivo de segurança no meio do caminho (como um Firewall ou filtro de pacotes) bloqueou o tráfego para aquela porta antes que ele chegasse ao destino (ou bloqueou a resposta de volta). O pacote simplesmente é ignorado ou descartado (drop).

- **closed (Fechada):** O pacote conseguiu chegar ao host de destino, mas não há nenhum aplicativo ou serviço escutando nessa porta. O sistema operacional responde imediatamente com um pacote de rejeição (RST/ACK no TCP ou uma mensagem de porta inacessível no ICMP).

## CENÁRIO C

- **Superfície de Ataque Reduzida:** Como apenas a porta 443 (HTTPS) está aberta no roteador/gateway, o tráfego externo legítimo é direcionado estritamente para o servidor web ou proxy reverso configurado. Todas as outras portas e serviços dos demais computadores da rede ficam completamente invisíveis e protegidos contra varreduras e ataques externos diretos.

- **Necessidade de Acesso Interno:** Para interagir ou testar os demais hosts da rede, um atacante (ou auditor) precisaria primeiro romper a defesa da borda (como o serviço na porta 443 ou vulnerabilidades humanas/phishing) para obter um ponto de apoio (pivot) dentro da rede local.
