Configuração de Impressão no Linux com CUPS e Compartilhamento via Samba
Este repositório apresenta a implementação de um ambiente de impressão no Linux utilizando o CUPS e o compartilhamento via Samba, permitindo que máquinas Windows utilizem uma impressora virtual CUPS‑PDF instalada em um servidor Ubuntu. O projeto integra conceitos de administração de sistemas, serviços de impressão e interoperabilidade entre plataformas.

Objetivo do Projeto
Configurar uma impressora virtual no Linux e disponibilizá‑la na rede para uso por clientes Windows, aplicando práticas reais de administração de sistemas operacionais e serviços de rede.

Tecnologias e Ferramentas
- Ubuntu Linux (máquina virtual)
- CUPS – Sistema de impressão
- CUPS‑PDF – Impressora virtual
- Samba – Compartilhamento de recursos
- Windows 11 – Cliente de teste
- Firefox – Acesso ao painel do CUPS

Etapas Principais
Instalação da impressora virtual
sudo apt install printer-driver-cups-pdf


Configuração no CUPS
- Acesso via navegador: http://localhost:631
- Adição da impressora CUPS‑PDF
- Seleção do driver Generic CUPS‑PDF Printer
- Ativação do compartilhamento
Instalação e configuração do Samba
sudo apt install samba
sudo nano /etc/samba/smb.conf


Trecho adicionado:
[printers]
   comment = Impressoras compartilhadas
   path = /var/spool/samba
   browseable = yes
   printable = yes
   guest ok = yes
   read only = yes


Ajustes na seção global:
printing = cups
printcap name = cups


Criação do diretório de spool:
sudo mkdir -p /var/spool/samba
sudo chmod 1777 /var/spool/samba


Reinício e validação:
sudo systemctl restart smbd
testparm


Teste no Windows
Acesso via Explorador de Arquivos:
\\IP_DA_VM


ou
\\NOME-DA-VM


Resultado esperado:
- Impressora CUPS‑PDF visível
- Impressão de teste gerando PDF corretamente

Competências Demonstradas
- Administração de sistemas Linux
- Configuração de serviços de impressão
- Compartilhamento de recursos via Samba
- Integração Linux ↔ Windows
- Edição e análise de arquivos de configuração
- Diagnóstico e solução de problemas em serviços de rede

Documentação Completa
O relatório detalhado da atividade está disponível no arquivo:
portfolio_unidadeV_config_impressao_linuxCUPS_viaSamba.pdf

Autor
Antonio Osly Pereira
RGM 37425625
Universidade Cruzeiro do Sul – Sistemas Operacionais
2026
