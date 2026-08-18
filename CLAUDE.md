# Up Travel Park — contexto do projeto

Este arquivo é o contexto permanente deste repositório. Leia antes de alterar qualquer coisa.

## O que é este projeto

Uma landing page única de captação para a Up Travel Park, agência de viagens da Gabriela Bordin, especializada em parques de diversões. O repositório tem um arquivo só que importa: `index.html`. Ele é auto-contido — CSS, JavaScript e imagens (em base64) estão todos dentro dele. Não existe build, não existe framework, não existe dependência.

Publicado na Vercel: https://up-travel-park.vercel.app/

## Como funciona a publicação

Todo commit na branch `main` faz a Vercel republicar sozinha, em menos de um minuto. Não há nada a configurar.

## Regras da Gabriela — obrigatórias

1. **Não invente informação, preço, pacote ou prazo que ela não forneceu.** Quando faltar um dado, pergunte antes de assumir.
2. **Não use marcas nem personagens da Disney** em nada que for criado. Os destinos principais dela são os parques de Orlando e de Paris, mas na página eles aparecem como "Guiamento virtual em Orlando" e "Guiamento virtual em Paris". Manter assim, salvo se ela autorizar explicitamente o contrário.
3. **Não prometa resultado garantido** de vendas, faturamento ou experiência.
4. **Fale com ela como sócio prático e direto**, não como assistente que só concorda. Se algo não for boa ideia, diga e explique. Separe fato de opinião.
5. **Não use travessões (—) nas frases.** Ela não gosta. Use vírgula ou reescreva.

## Tom de voz da marca

- Acolhedora e especialista, ao mesmo tempo
- Expressões dela: "parqueiros", "magia", "se você pode sonhar você pode realizar"
- Nunca: palavrões, negatividade
- Emoji com moderação. Ela usa 🧡

## Os serviços (não alterar valores sem ordem dela)

| Serviço | Preço na página | Como funciona |
|---|---|---|
| Consultoria de viagem | R$ 250 | Formulário + 1h de conversa |
| Roteiro personalizado | Sob consulta | Formulário → 1h de alinhamento com pré-esboço → roteiro completo → 1h de apresentação → ajuste em até 48h |
| Guiamento virtual em Orlando | Sob consulta | Formulário → reunião de até 2h → marca filas rápidas → acompanhamento em tempo real no dia do parque |
| Guiamento virtual em Paris | Sob consulta | Igual ao de Orlando |

Ela não vende ingressos nem hotéis.

## Diferenciais que podem ser usados (todos verificados com ela)

- Já visitou mais de 22 parques e andou em mais de 116 montanhas russas
- Quase 5 anos como criadora de conteúdo de viagem, com comunidade construída
- Ela mesma sonhou e economizou por anos para fazer essa viagem
- Mora nos Países Baixos, clientes no Brasil — pode demorar horas para responder, e a página assume isso com transparência

## Cliente ideal

Casais e grupos de amigos em primeira viagem. Mulheres de 28 a 45 anos, com liberdade financeira. O que mais desejam: uma viagem bem estruturada, sem preocupações. O que mais temem: achar que estão fazendo um mau negócio. Esse medo é a âncora de qualquer texto de objeção.

## Identidade visual

Vem do logotipo dela, não invente outra:

```
--navy:      #1A3A6B   /* azul-marinho principal */
--navy-deep: #12294D   /* fundo do topo, rodapé */
--orange:    #FF6B1A   /* laranja da marca, destaques */
--orange-btn:#ED5F0C   /* laranja um pouco mais escuro, só em botões, por contraste */
--cream:     #FFF8F3   /* fundo alternado das seções */
```

Fontes: Playfair Display nos títulos, Poppins no texto.

O logo redondo está embutido em base64 no `index.html`. O arquivo original tinha fundo preto — foi recortado no anel laranja e o fundo virou transparente. Se for trocar o logo, refaça esse recorte, senão volta a aparecer um anel escuro.

## Integração com o Google Forms

O formulário da página envia por POST para o Google Forms, dentro de um iframe oculto, sem a pessoa sair da página.

- Endpoint: `https://docs.google.com/forms/d/e/1FAIpQLScKNCdN91jrxhVMeXF7l5z1GTU7sL5K3wy9GoFyAQmaeN6Z_Q/formResponse`
- `entry.882995110` — nome
- `entry.2061155044` — e-mail
- `entry.677966377` — serviço de interesse
- `entry.1009808471` — já tem data para a viagem
- `entry.1996814120` — origem (campo oculto)

**Cuidados aprendidos na prática:**

- O texto de cada opção enviada precisa bater **letra por letra** com as opções cadastradas no Google Forms. Uma vírgula diferente e o Google recusa o envio inteiro, em silêncio.
- O formulário do Google precisa estar **publicado e liberado para qualquer pessoa com o link**. Se não estiver, o envio some sem erro visível. Isso já aconteceu uma vez.
- A tela de "Recebi!" da página aparece quando o envio sai daqui. Ela **não** prova que o Google aceitou. Toda validação tem que ser conferida na aba Respostas do formulário.

## Rastreio de origem

A página lê o parâmetro `?o=` da URL e preenche o campo oculto de origem:

- `?o=yt` → YouTube
- `?o=ig` → Instagram
- `?o=tk` → TikTok
- sem parâmetro → Direto

Os links de divulgação precisam sempre carregar o parâmetro. É o que vai responder qual canal traz cliente.

## Contexto estratégico

O gargalo do negócio é captação, não a página. Em agosto de 2026 a agência recebia cerca de 1 orçamento por mês e fechava menos de uma venda por mês, com quase 5 anos de audiência construída. Esta página existe para transformar audiência em contato registrado.

Por isso: qualquer mudança que **aumente o atrito até o formulário** é uma mudança ruim, por mais bonita que pareça. O formulário é o objetivo da página inteira.

Próximos projetos já priorizados, nesta ordem: motor de conteúdo assistido para o Instagram, depois a sequência comercial (modelo de orçamento, follow-up agendado, pós-venda). A decisão entre os dois depende de quantos contatos esta página gerar até meados de outubro de 2026.

## Pendências conhecidas

- Ela ainda não tem número de WhatsApp da agência. Por isso não há WhatsApp na página. O guiamento virtual promete acompanhamento em tempo real, o que depende desse número para ser entregue.
- Ela tem um texto de orçamento semi pronto que ainda não foi transformado em modelo.
