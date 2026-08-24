# Kali Linux: Linhas de Comando

- Handshake TCP e estados de porta
  - SYN-ACK, ACK
- Tipos de scan e o Nmap
  - SYN scan (-sS), Connect scan (-sT), detectação de versão (-sV)
  - `sudo nmap -sS *alvo*`
 
  - Estrutura do sistema: FHS
    - / (diretório raiz)
      - /etc
        - passwd (senhas)
        - group (nomes e usuários dos grupos)
      - /home (diretório usuários)
      - /root (superusuário)
      - /var (log, dados variáveis)
      - /usr
        - bin
        - share
      - /opt

  ## Navegação básica:
  - `pwd` (diretório atual)
  - `ls` (conteúdo do diretório atual)
  - `ls -la` (lista tudo detalhado, incluindo ocultos)
  - `cd /*caminho*` (muda diretório informado)
  - `cd --` (sobe um nível no diretório)
  - `cd ~` (diretório home do usuário)

- **Manipulação de arquivos e diretórios**
  - `mkdir *pasta*` (cria novo diretório)
  - `touch *arq*.txt` (cria arquivo vazio)
  - `cp *origem* *destino*` (copia arquivo ou diretório -r)
  - `mv *origem* *destino*` (move ou renomeia)
  - `rm *arquivo*` (remove um arquivo ou diretório -r)
  - `cat *arquivo*` (exibe todo conteúdo do arquivo)
  - `less *arquivo*` (exibe conteúdo com rolagem/paginação)
  - `nano` / `vim *arquivo*` (abre editores de texto no terminal)
 
- **Wildcards e globbing**
  - * (Qualquer sequência de caracteres) - `ls *.txt`
  - ? (Um único caracter qualquer) - `ls arquivo?.txt`
  - [abc] (Qualquer caracter
  - {a,b}
 
- **Encontrando arquivos: find e locate**
  - find / -name "*.conf"
  - find . -type f -mtime -7
  - find / -perm -4000 2>/dev/null
  - locate *nome*
 
- **Links simbólicos**
  - ln -s alvo link 
  - ls -l
  - rm link
 
- **Permissões: rwx e notação octal**
  - r (read): Leitura
  - w (write): Escrita
  - x: Execução
  - `-rwxr-xr--`
    - tipo (-), dono (rwx), grupo (r-x), outros(r--)

- chmod
  - Altera as permissões de um arquivo
  - `chmod 754 script.sh`
  - `chmod +x script.sh`
- chown
  - Altera o dono/grupo de um arquivo
  - `chown usuario:grupo arquivo`
 
- **Usuários, grupos e privilégio**
  - Usuário comum -> `sudo`/ `su -` -> root (privilégio total)
  - `whoami`
  - `id`
  - `groups`
  - `sudo assuser *aluno*`

- **Ajuda do próprio sistema**
  - `man nmap` (MAnual completo do comando)
  - `nmap --help` (Resumo rápido das opções de uso)
  - `apropos *porta*` (Comandos relacionados a um termo)
  - `man -k *rede*` (Equivalente a apropos)
 
- **Histórico, atalhos e aliases**
  - `history` (Comandos já executados na sessão)
  - Ctrl + R (Histórico de comandos)
  - Tab (Autocompleta comandos, arquivos e caminhos)
  - `alias nm='nmap -sV -T4'` (Cria atalho para um comando longo)
 
- **Redirecionamento e pipes**
  - `namp -sV *alvo*`
    - `grep open` (saída no terminal) - (passa a saída para outro comando)
    - `*resultado*.txt` (redireciona para um arquivo)
      - `cat *resultado*.txt` (lê o conteúdo salvo no arquivo)
  - oN também é redirecionamento
    - `nmap -oN *saida*.txt *alvo*` (nativo)
    - `nmap *alvo* > *saida*.txt` (redirecionamento genérico do shell)
    - `namp *alvo* | grep open`
   
- **Processos**
  - `ps` (lista processos em execução)
  - `ps aux` (lista **todos** os processos do sistema, de todos os usuários)
  - `top` / `htop` (Monitor interativo de processos em tempo real)
  - `kill PID` (encerra um processo pelo seu identificador)
  - `*comando* &` (executa um comando em segundo plano)
