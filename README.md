# tela-bonita

Skill para o Claude Code (e outros agentes com skills) que desenha, critica e melhora telas de sites e apps, com as regras do Brasil já embutidas.

Peça em português do jeito que você fala: "deixe a tela de login mais bonita", "o painel está com cara de IA, melhore", "critique o design desta página de vendas". A skill entende o pedido, escolhe o tipo de trabalho e entrega a tela pronta.

## O que ela traz além da Impeccable

A tela-bonita é uma versão modificada da [Impeccable](https://github.com/pbakaus/impeccable), de Paul Bakaus. Toda a parte de design vem de lá. O que esta versão acrescenta:

- **Entende pedidos em português** e responde em português.
- **Textos de interface em pt-BR:** verbos claros nos botões, acentos, mensagens de erro que dizem como resolver.
- **Formatos do Brasil:** datas, horas, R$, máscaras e validação de CPF, CNPJ, CEP e telefone, busca de endereço pelo CEP.
- **Pagamento brasileiro:** Pix com "copia e cola", boleto e parcelamento.
- **LGPD:** consentimento separado para dados de saúde, dados mascarados em telas compartilhadas, caminho "Seus dados".
- **Fichas rápidas:** menor número de toques, padrões inteligentes, rascunho automático.
- **Saúde e odontologia:** linguagem do dentista e do paciente, numeração FDI no odontograma, calibração 1:1 para medir em imagens, publicidade dentro das regras do CFO, acessibilidade para pacientes idosos.
- **Celular (Expo e React Native):** áreas seguras, teclado, listas longas, conexão ruim e botão voltar do Android.

Tudo isso está em [`skills/tela-bonita/reference/brasil.md`](skills/tela-bonita/reference/brasil.md). A lista completa de mudanças está em [CHANGES.md](CHANGES.md).

## Como instalar

Copie a pasta `skills/tela-bonita` para `~/.claude/skills/tela-bonita` (para todos os projetos) ou para `.claude/skills/tela-bonita` dentro de um projeto.

Se você já usa a Impeccable, desative uma das duas: as descrições são quase iguais e o agente escolheria entre elas sem avisar.

## Como usar

- Fale normalmente: "melhore o visual da tela de agenda".
- Ou chame um comando: `/tela-bonita critique`, `/tela-bonita polish`, `/tela-bonita audit` e os demais da tabela em [`SKILL.md`](skills/tela-bonita/SKILL.md).

## O que roda no seu computador

O script `skills/tela-bonita/scripts/impeccable` é o mesmo da Impeccable. Na primeira vez, ele baixa o motor da Impeccable da página oficial de versões do projeto original no GitHub e confere o arquivo pelo SHA-256 listado em `engine-checksums.txt`. Se a conferência falhar, ele não roda.

## Créditos e licença

- Design e motor: [Impeccable](https://github.com/pbakaus/impeccable), de Paul Bakaus, sob a licença Apache 2.0.
- Referências de iOS e Android: derivadas de [platform-design-skills](https://github.com/ehmo/platform-design-skills), de ehmo, sob a licença MIT.
- Adaptação brasileira: Marcos Bruno Araujo (MB Gestão), 2026, sob a licença Apache 2.0.

Este projeto não é afiliado nem endossado pelo autor da Impeccable. Veja [LICENSE](LICENSE) e [NOTICE.md](NOTICE.md).
