# AutoLog — como instalar no celular

**IMPORTANTE:** não abra o `index.html` direto do celular (endereço começando com `content://` ou `file://`). Assim ele não instala, não funciona sem internet e pode perder os dados. O app precisa estar hospedado em um endereço **https** (passo 1 abaixo).

Pacote com o app pronto: `index.html`, `manifest.webmanifest`, `sw.js` (funciona sem internet), ícones e o workflow do GitHub Pages.
O app só funciona instalado quando está em um endereço **https**. Abrir o arquivo direto do celular não instala.

## 1. Colocar no ar (grátis, só pelo celular)
**Opção A — GitHub Pages**
1. Crie uma conta em github.com e um repositório novo chamado `autolog`.
2. Em *Add file → Upload files*, envie TODO o conteúdo desta pasta (inclusive a pasta `.github`; se o celular não enviar pastas ocultas, crie o arquivo `.github/workflows/pages.yml` colando o conteúdo).
3. Em *Settings → Pages*, em *Source* escolha **GitHub Actions**. Depois de 1 a 2 minutos o endereço aparece em *Actions*.
4. Atenção: no plano gratuito do GitHub, Pages costuma exigir repositório público (confira as regras atuais). Seus dados NÃO ficam no repositório: ficam só no celular. No repositório vai apenas o código.

**Opção B — Cloudflare Pages** (aceita projeto privado): em *Workers & Pages → Create → Pages → Upload assets*, envie a pasta.

## 2. Instalar
Abra o endereço no **Chrome do Android** → menu ⋮ → **Instalar app** (ou *Adicionar à tela inicial*). O AutoLog passa a abrir em tela cheia, com ícone próprio e sem internet.

## 3. Gerar o APK (opcional)
1. Acesse pwabuilder.com e cole o endereço do app.
2. Escolha *Package for stores → Android* e baixe o pacote.
3. Guarde a chave de assinatura que ele gerar. Sem ela você não consegue atualizar o app depois.
4. Instale o APK no celular permitindo "instalar apps desconhecidos". Para esconder a barra de endereço, faça a verificação do domínio que o PWABuilder indica.

## 4. Passar os dados da versão do chat
No app antigo: Mais → **Copiar backup** (ou *Baixar backup*). No novo: Mais → **Restaurar backup**, cole o texto ou escolha o arquivo. O app verifica se o backup está íntegro e avisa se ele for mais antigo que os dados do aparelho.

## 5. Atualizar
Troque o `index.html` e aumente o número `autolog-v5` para `autolog-v6` em `sw.js`.

## Limitações reais
- Testado apenas em navegador de computador simulando celular (telas abrem, formulários salvam, dados persistem). **Não foi testado em um Android real.**
- Lembretes: o app avisa ao ser aberto e quando você autoriza notificações. Avisos com o app fechado exigem um servidor de push ou o app nativo.
- Importar XLSX carrega uma biblioteca da internet; CSV funciona offline.
- Backup no Google Drive e troca de celular assistida **não foram feitos**: dependem de credenciais OAuth suas. Use o backup em arquivo.
- Não há testes automatizados no código, só o teste de navegação feito na entrega.
- Dados ficam no armazenamento do navegador (IndexedDB). Limpar os dados do site apaga tudo: faça backup.
