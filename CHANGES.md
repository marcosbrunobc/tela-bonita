# O que mudou em relação à Impeccable

A tela-bonita parte da Impeccable 4.8.0 (commit d34c87e), de Paul Bakaus. Mudanças feitas por Marcos Bruno Araujo (MB Gestão) em 27/10/2026:

1. **Nome:** a skill passou a se chamar `tela-bonita`. Os comandos viraram `/tela-bonita <comando>` e o caminho de reserva dos scripts virou `.claude/skills/tela-bonita/scripts`.
2. **Descrição (`SKILL.md`):** frases em português que acionam a skill ("deixar a tela mais bonita", "melhorar o visual", "está com cara de IA", "criticar o design" e outras) e menção às convenções brasileiras.
3. **Novo passo 4 no Setup (`SKILL.md`):** quando a interface é em português do Brasil, a skill lê `reference/brasil.md` antes de escrever textos, formulários, pagamentos ou telas de saúde.
4. **Arquivo novo `reference/brasil.md`:** texto de interface em pt-BR, formatos do Brasil (data, hora, R$), máscaras e validação de CPF, CNPJ, CEP e telefone, Pix e boleto, LGPD para dados de saúde, fichas com o menor número de toques, regras para apps de saúde e odontologia (linguagem dentista x paciente, numeração FDI, calibração 1:1 de imagens, publicidade segundo o CFO, pacientes idosos), boas práticas de Expo e React Native e uma lista de conferência.
5. **Créditos:** `NOTICE.md` mantém os avisos originais e acrescenta os da Impeccable e da tela-bonita.

Os demais arquivos (`reference/*.md` originais e `scripts/`) seguem iguais aos da Impeccable, exceto pela troca de nome e de caminho descrita no item 1.
