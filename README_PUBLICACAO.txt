INFINITYS — PACOTE PREPARADO PARA PUBLICAÇÃO

ARQUIVOS
- frontend/index.html: site com skin Aconchegante padrão, skins Neon/Retrô,
  avatar expressivo, status, conquistas e recursos de áudio.
- backend/main.py: API FastAPI compatível com APIs de chat completions.
- render.yaml: configuração inicial de frontend estático + backend Python no Render.

PLATAFORMA SUGERIDA: RENDER
A documentação oficial permite publicar Static Sites e Web Services em plano
Free. O serviço web gratuito entra em suspensão após 15 minutos sem tráfego e
pode levar cerca de um minuto para acordar. Não é ideal para produção contínua.
Consulte https://render.com/docs/free e https://render.com/docs/deploy-fastapi.
A camada gratuita da API de hospedagem não significa que o provedor de IA seja
gratuito; uso de modelo pode gerar cobrança conforme o provedor escolhido.

PASSOS
1. Crie/acesse uma conta Render e conecte um repositório Git que contenha esta
   estrutura (o arquivo render.yaml deve ficar na raiz).
2. Crie os serviços pelo Blueprint do repositório.
3. No serviço infinitys-api, configure como variáveis secretas:
   AI_API_KEY = chave emitida pelo provedor escolhido
   AI_BASE_URL = endpoint base do provedor, se necessário
   AI_MODEL = identificador exato do modelo habilitado
   FRONTEND_ORIGINS = origem exata do Static Site (por exemplo,
   https://infinitys-site.onrender.com). Ajuste se o domínio atribuído diferir.
4. Faça deploy e teste https://URL-DA-API/health.
5. Abra o site, na caixa "Endereço do backend", informe
   https://URL-DA-API/api/chat e salve.
6. Envie uma mensagem e confirme a resposta. Se CORS bloquear, atualize
   FRONTEND_ORIGINS com a origem exata do site, sem barra final, e redeploy.
7. Nunca cole AI_API_KEY no navegador, no HTML, no Git ou neste chat.

SEGURANÇA E LIMITAÇÕES
- Foi incluído um limite simples por IP em memória (15 chamadas/minuto/processo).
  Ele não substitui autenticação, limites do provedor ou gateway de produção.
- Antes de abrir ao público, implemente autenticação/quotas por usuário,
  monitoramento de gastos, proteção contra abuso e política de privacidade.
- O site guarda preferências e histórico no localStorage do navegador.
- O exemplo ainda não tem pesquisa web integrada nem memória remota persistente.
- O plano gratuito do Render pode suspender o backend após 15 minutos ocioso;
  pode haver latência ao primeiro acesso. Verifique os limites atuais na página
  oficial antes de qualquer upgrade ou cobrança.
