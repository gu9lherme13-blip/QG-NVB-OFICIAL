# QG NVB — Recrutamento com aprovação pelo Discord

## Canal configurado
- Canal de candidaturas: `1555845609343164436`
- O código usa `RECRUIT_CHANNEL_ID (também aceita RECRUT_CHANNEL_ID por compatibilidade)` do Render se definido; caso contrário, usa o ID acima.

## Funcionamento
1. O candidato preenche as sete perguntas do formulário no QG.
2. O site envia uma única solicitação para `/api/recruitment`.
3. O servidor envia a ficha ao canal configurado com botões **🟢 Aprovar** e **🔴 Recusar**.
4. A staff autorizada pode decidir diretamente na mensagem do Discord.
5. A mensagem é atualizada com o status e os botões são removidos após a decisão.

## Variáveis necessárias no Render
- `DISCORD_TOKEN`: token do bot.
- `CLIENT_ID`: ID da aplicação Discord.
- `GUILD_ID`: ID do servidor NVB (recomendado para conferir cargos e permissões).
- `RECRUIT_CHANNEL_ID (também aceita RECRUT_CHANNEL_ID por compatibilidade)`: opcional; se definido, deve ser `1555845609343164436`.
- `MAIN_DISCORD_INVITE`: convite enviado quando a candidatura é aprovada.
- `QG_PUBLIC_URL`: URL pública do QG.

O bot precisa estar no servidor e ter no canal de candidaturas as permissões **Ver canal**, **Enviar mensagens** e **Incorporar links**. A staff precisa ter um dos cargos autorizados pelo código para aprovar/recusar.

## Correções incluídas
- Um único handler de envio no formulário, evitando que dois listeners façam requisições concorrentes.
- O handler captura o envio antes de outros listeners e sempre reativa o botão ao terminar.
- A espera do navegador permite até 65 segundos para lidar com a inicialização lenta de instâncias gratuitas.
- O servidor aguarda até 60 segundos pela operação de envio ao Discord e registra os passos nos logs.

## Publicação
Substitua os arquivos correspondentes no repositório `QG-NVB`, branch `main`, faça commit e espere o Render concluir um deploy **Live**. Depois envie uma única candidatura de teste e verifique os logs. Este pacote foi validado sintaticamente, mas o envio real depende do token, do canal e das permissões configuradas no Render/Discord.
