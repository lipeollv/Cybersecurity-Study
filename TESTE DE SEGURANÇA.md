# Relatório Técnico de Auditoria de Segurança: Broken Access Control (Dash/Plotly Application)

## 1. Visão Geral do Alvo e Objetivo

- **Alvo:** Aplicação baseada em **Plotly Dash** (`painelen.azkpi.com.br), utilizando autenticação centralizada baseada em **OAuth2/OpenID Connect** (via Authentik) e tokens **JWT (JSON Web Tokens)** assinados com o algoritmo **RS256**.
    
- **Objetivo:** Auditar a aplicação em busca de falhas de _Broken Access Control_ (Controle de Acesso Quebrado), tentando elevar privilégios de um usuário comum (`auxiliar.adm8` / grupo `painelen_programacao`) para um perfil administrativo (`painelen_admin`) e identificar eventuais exposições de rotas ou componentes sensíveis.
    

## 2. Metodologia e Vetores de Teste Executados

### A. Manipulação e Injeção de Payload em JWT (Access Token)

- **Abordagem:** Desenvolvimento de um script em Python para decodificar o token JWT da sessão, alterar o array de grupos de `["painelen_programacao"]` para `["painelen_admin"]`, e injetar o token modificado tanto via script de requisições quanto diretamente no armazenamento de cookies do navegador.
    
- **Resultado:** O backend recusou imediatamente as requisições autenticadas com tokens modificados, retornando códigos de redirecionamento para o login (`HTTP 302 /login?proximo=/idg`) ou invalidando a sessão.
    
- **Conclusão Técnica:** O servidor realiza a **validação estrita da assinatura criptográfica (RS256)** de ponta a ponta utilizando a chave pública/privada correspondente. Como o payload foi adulterado sem a chave privada real do emissor do token, a integridade matemática falhou, impedindo qualquer forma de adulteração direta de privilégios via token.
    

### B. Análise de Exposição em Endpoints de Configuração do Dash

- **Abordagem:** Inspeção de endpoints internos padrão do Dash (`/_dash-layout`) e monitoramento das requisições assíncronas (`/_dash-update-component`) via ferramentas de desenvolvedor (DevTools).
    
- **Resultado:** A aplicação emprega uma arquitetura de **Single-Page Application (SPA) com roteamento dinâmico** (`dcc.Location`). O payload inicial entregue ao navegador contém apenas o esqueleto e o container genérico de páginas (`id="pagina"`), sem renderizar ou vazar componentes estáticos restritos ou dados sensíveis de outras permissões.
    

### C. Teste de Forçamento de Rotas (Forced Browsing)

- **Abordagem:** Tentativa de acesso direto a sub-rotas e caminhos não listados ou restritos na interface do usuário (ex: parâmetros adicionais na URL e caminhos administrativos).
    
- **Resultado:** O roteador client-side e o backend trataram as entradas inválidas ou não autorizadas redirecionando o fluxo de navegação de volta para o painel padrão ou para a tela de restrição de acesso, sem permitir o bypass de visualização.
    

## 3. Conclusão da Auditoria

Os testes conduzidos demonstraram que os mecanismos de segurança implementados na aplicação possuem uma **postura de defesa robusta** contra ataques direcionados de manipulação de sessão e escalação horizontal/vertical de privilégios via token:

1. **Integridade Criptográfica Forte:** A validação estrita de RS256 bloqueia com eficácia ataques de tampering em payloads de JWT.
    
2. **Isolamento de Componentes:** O framework Dash está configurado de forma a não expor lógica administrativa ou layouts ocultos no código-fonte estático entregue a usuários comuns.