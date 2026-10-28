# Contexto brasileiro

> Arquivo novo da tela-bonita (não existe na Impeccable original). Carregue sempre que a interface estiver em português do Brasil, o público estiver no Brasil ou o PRODUCT.md disser Brasil. Ele soma às outras referências e nunca passa por cima de um pedido explícito do usuário.

## 1. Texto da interface

- Escreva em português do Brasil natural, tratando a pessoa por "você". Botões usam verbo no imperativo e dizem o que acontece: "Salvar orçamento", "Enviar para o paciente", "Agendar". Nada de "OK" ou "Submit".
- Use a palavra comum quando ela existe: "Entrar" e não "Login", "Sair" e não "Logout", "Configurações" e não "Settings", "Painel" e não "Dashboard" em tela de usuário final.
- Acentos sempre, inclusive em rótulos curtos e mensagens de erro ("Orçamento", "Não foi possível salvar").
- Sem gerúndio de telemarketing ("vamos estar enviando") e sem pedido de desculpa vago. Erro diz o que houve e como resolver: "O CEP não foi encontrado. Confira os números ou preencha o endereço à mão."
- Português ocupa cerca de 20 a 30% mais espaço que o inglês. Deixe folga em botões, abas e chips e teste com o texto real, nunca com lorem ipsum.

## 2. Formatos do Brasil

- **Data:** dd/mm/aaaa. Por extenso: "27 de outubro de 2026". Dia da semana com inicial minúscula no meio da frase ("terça-feira").
- **Hora:** relógio de 24 horas. "14h30" em texto corrido e "14:30" em campos e tabelas.
- **Dinheiro:** "R$ 1.234,56", com espaço depois do R$, ponto no milhar e vírgula nos centavos. No código: `Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' })`. Alinhe valores à direita e use algarismos tabulares em colunas.
- **Números:** vírgula decimal ("2,5 mm") e ponto no milhar.
- **Calendário:** semana começando no domingo, salvo se o produto já usa segunda.

## 3. Campos de formulário

- **CPF:** máscara `000.000.000-00`, validação dos dígitos verificadores e teclado numérico (`inputMode="numeric"`, ou `keyboardType="number-pad"` no React Native). Em listas e telas compartilhadas, mostre mascarado: `***.456.789-**`.
- **CNPJ:** máscara `00.000.000/0000-00`, com validação.
- **CEP:** máscara `00000-000`. Ao completar, busque o endereço (ex.: ViaCEP) e preencha rua, bairro, cidade e UF, deixando tudo editável e focando o campo "Número".
- **Telefone:** `(00) 00000-0000` para celular e `(00) 0000-0000` para fixo. Ofereça "Este número tem WhatsApp" quando o produto se comunicar por lá.
- **UF:** lista com as 27 siglas, ou preenchida pelo CEP.
- **Nome:** um campo "Nome completo", aceitando acentos, apóstrofo e partículas ("de", "da", "dos"). Não separe nome e sobrenome se não houver motivo.

## 4. Pagamento

- **Pix** vem em primeiro lugar: QR Code, o código "copia e cola" com botão "Copiar código" e o prazo de validade visível. Confirme o pagamento na tela assim que ele chegar.
- **Boleto:** linha digitável copiável, vencimento em destaque e aviso de que a compensação leva até 3 dias úteis.
- **Cartão:** parcelamento claro ("3x de R$ 100,00 sem juros") e o total sempre visível.

## 5. Privacidade (LGPD) e dados de saúde

- Dado de saúde é **dado pessoal sensível** (LGPD, art. 5º, II). O consentimento para tratá-lo precisa ser específico e destacado (art. 11, I): uma caixa própria, nunca marcada de fábrica, separada dos termos gerais, com uma frase dizendo para que o dado será usado.
- Mostre só o necessário em telas vistas por outras pessoas, como a recepção de uma clínica: mascare CPF e telefone, e esconda a observação clínica na lista.
- Deixe à vista um caminho "Seus dados" para ver, corrigir, exportar e pedir a exclusão.
- Nunca use dado de saúde em notificação de tela bloqueada ("Lembrete da sua consulta", e não "Lembrete do seu tratamento de canal").
- Isto orienta o design. Não é parecer jurídico: em caso de dúvida, peça validação de quem cuida da parte legal do produto.

## 6. Simples para quem tem pressa

Profissionais de saúde preenchem fichas entre um atendimento e outro. Para avaliação, plano de tratamento, orçamento e qualquer ficha:

- Menor número de toques possível. Conte os toques do caminho principal e corte o que puder.
- Valores padrão inteligentes: data de hoje, último profissional usado, procedimento mais comum.
- Tudo continua editável depois. Padrão nunca trava a pessoa.
- Rascunho salvo automaticamente: sair da tela não perde o que foi digitado.
- Um objetivo por tela, com o botão principal na área do polegar.
- Opções frequentes como chips de um toque; o campo de texto livre fica para o que é raro.

## 7. Apps de saúde e odontologia

- **Dois públicos, duas linguagens.** Tela do dentista usa o termo técnico ("endodontia", "dente 36"); tela do paciente usa a palavra simples ("tratamento de canal", "primeiro molar inferior esquerdo"). Antes de escrever, descubra de quem é a tela.
- **Numeração dos dentes:** use a notação FDI (permanentes de 11 a 48, decíduos de 51 a 85). No odontograma, cada estado tem cor **e** ícone ou rótulo, nunca só cor, e a legenda fica sempre visível.
- **Imagens clínicas e medidas:** qualquer função que mede na tela (radiografia, foto, régua) exige calibração 1:1. Peça ao usuário para calibrar antes da primeira medida, mostre que a medida depende da calibração e permita refazer.
- **Publicidade odontológica:** telas de marketing feitas para dentistas (página de vendas, post, campanha) seguem o Código de Ética Odontológica do CFO, alterado pela Resolução CFO-271/2025. Antes de mostrar preço, desconto, antes e depois ou depoimento, confira o texto vigente. Não invente regra.
- **Pacientes idosos:** texto base de pelo menos 16 px, respeito à fonte grande do sistema (no React Native, não desligue `allowFontScaling`), contraste mínimo WCAG AA e alvos de toque de pelo menos 48 dp no Android e 44 pt no iOS.

## 8. Celular (Expo e React Native)

- Respeite as áreas seguras (`react-native-safe-area-context`) e não deixe o teclado cobrir o campo em foco.
- Listas longas usam `FlatList` ou `FlashList`, com estado vazio que diga o que vai aparecer ali e como começar.
- Conexão ruim é a regra: mostre carregando, sem internet e tentar de novo, e nunca descarte o que a pessoa digitou.
- Botão voltar do Android fecha a camada de cima (modal, menu) antes de sair da tela.
- Modo escuro desenhado de verdade, não só invertido.

## 9. Conferência antes de entregar

- [ ] Todo texto em português do Brasil, com acentos e verbos no imperativo nos botões
- [ ] Datas, horas e dinheiro no formato brasileiro
- [ ] CPF, CEP e telefone com máscara, validação e teclado numérico
- [ ] Consentimento de dado de saúde separado e desmarcado, se houver dado de saúde
- [ ] Caminho principal com o menor número de toques e rascunho automático
- [ ] Nenhum estado comunicado só por cor
- [ ] Fonte grande do sistema e alvos de toque testados
- [ ] Se for marketing odontológico: regras do CFO conferidas no texto vigente
