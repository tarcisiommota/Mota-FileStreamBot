<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram File Stream Bot</title>
</head>
<body>

<h1 align="center">Telegram File Stream Bot</h1>

<p align="center">
  <a herf="https://github.com/EverythingSuckz/TG-FileStreamBot">
    <img src="https://telegra.ph/file/a8bb3f6b334ad1200ddb4.png" height="100" width="100" alt="Logotipo do File Stream Bot">
  </a>
</p>

<p align="center">
    Um bot do Telegram para <b>gerar link direto</b> para seus arquivos do Telegram.
</p>

<hr>

<blockquote>
  <p><strong>NOTA:</strong> Veja o <a href="https://github.com/EverythingSuckz/TG-FileStreamBot/tree/python">branch em Python</a> se estiver interessado nisso.</p>
</blockquote>

<hr>

<details open="open">
  <summary>Índice</summary>
  <ol>
    <li>
      <a href="#como-fazer-o-seu-próprio">Como fazer o seu próprio</a>
      <ul>
        <li><a href="#deploy-no-heroku">Deploy no Heroku</a></li>
      </ul>
      <ul>
        <li><a href="#baixar-e-executar">Baixar e executar</a></li>
        <li><a href="#executar-via-docker-compose">Executar via Docker Compose</a></li>
        <li><a href="#executar-via-docker">Executar via Docker</a></li>
        <li><a href="#compilar-e-executar">Compilar e executar</a>
          <ul>
            <li><a href="#ubuntu">Ubuntu</a></li>
            <li><a href="#windows">Windows</a></li>
          </ul>
        </li>
      </ul>
    </li>
    <li>
      <a href="#configurando-as-coisas">Configurando as coisas</a>
      <ul>
        <li><a href="#variáveis-de-ambiente-obrigatórias">Variáveis de ambiente obrigatórias</a></li>
        <li><a href="#variáveis-de-ambiente-opcionais">Variáveis de ambiente opcionais</a></li>
        <li><a href="#usando-múltiplos-bots">Usando múltiplos bots</a></li>
        <li><a href="#usando-sessão-de-usuário-para-adicionar-bots-automaticamente">Usando sessão de usuário para adicionar bots automaticamente</a>
          <ul>
            <li><a href="#o-que-isso-faz">O que isso faz?</a></li>
            <li><a href="#como-gerar-uma-string-de-sessão">Como gerar uma string de sessão?</a></li>
          </ul>
        </li>
      </ul>
    </li>
    <li><a href="#contribuindo">Contribuindo</a></li>
    <li><a href="#contate-me">Contate-me</a></li>
    <li><a href="#créditos">Créditos</a></li>
  </ol>
</details>

<h2 id="como-fazer-o-seu-próprio">Como fazer o seu próprio</h2>

<h3 id="deploy-no-heroku">Deploy no Heroku</h3>

<blockquote>
  <p><strong>NOTA:</strong> Você precisará <a href="https://github.com/EverythingSuckz/TG-FileStreamBot/fork">fazer um fork</a> deste repositório para fazer o deploy no Heroku.</p>
</blockquote>

<hr>

<h3 id="baixar-e-executar">Baixar e executar</h3>
<ul>
  <li>Acesse a aba <a href="https://github.com/EverythingSuckz/TG-FileStreamBot/releases">releases</a>, na seção <em>pre release</em>, baixe a versão para sua plataforma e arquitetura.</li>
  <li>Extraia o arquivo zip em uma pasta.</li>
  <li>Crie um arquivo chamado <code>fsb.env</code> e adicione todas as variáveis necessárias (veja o arquivo <code>fsb.sample.env</code> como referência).</li>
  <li>Dê permissão de execução ao arquivo executável usando o comando <code>chmod +x fsb</code> (não é necessário no Windows).</li>
  <li>Execute o bot usando o comando <code>./fsb run</code> (<code>./fsb.exe run</code> no Windows).</li>
</ul>

<hr>

<h3 id="executar-via-docker-compose">Executar via Docker Compose</h3>
<ul>
  <li>Clone o repositório:</li>
</ul>
<pre><code>git clone https://github.com/EverythingSuckz/TG-FileStreamBot
cd TG-FileStreamBot
</code></pre>

<ul>
  <li>Crie um arquivo chamado <code>fsb.env</code> e adicione todas as variáveis necessárias (veja o arquivo <code>fsb.sample.env</code> como referência).</li>
</ul>

<pre><code>nano fsb.env</code></pre>

<ul>
  <li>Construa e execute o arquivo Docker Compose:</li>
</ul>
<pre><code>docker-compose up -d
</code></pre>
<p>OU</p>
<pre><code>docker compose up -d
</code></pre>

<hr>

<h3 id="executar-via-docker">Executar via Docker</h3>
<pre><code>docker run --env-file fsb.env ghcr.io/everythingsuckz/fsb:latest
</code></pre>
<p>Onde <code>fsb.env</code> é o arquivo de ambiente contendo todas as variáveis.</p>

<hr>

<h3 id="compilar-e-executar">Compilar a partir do código-fonte</h3>

<h4 id="ubuntu">Ubuntu</h4>
<blockquote>
  <p><strong>NOTA:</strong> Certifique-se de instalar o Go 1.21 ou superior. Consulte <a href="https://stackoverflow.com/a/17566846/15807350">esta referência</a>.</p>
</blockquote>

<pre><code>git clone https://github.com/EverythingSuckz/TG-FileStreamBot
cd TG-FileStreamBot
go build ./cmd/fsb/
chmod +x fsb
mv fsb.sample.env fsb.env
nano fsb.env
# (adicione suas variáveis de ambiente, veja a próxima seção para mais informações)
./fsb run
</code></pre>

<p>Para parar o programa, pressione <kbd>CTRL</kbd>+<kbd>C</kbd>.</p>

<h4 id="windows">Windows</h4>
<blockquote>
  <p><strong>NOTA:</strong> Certifique-se de instalar o Go 1.21 ou superior.</p>
</blockquote>

<pre><code>git clone https://github.com/EverythingSuckz/TG-FileStreamBot
cd TG-FileStreamBot
go build ./cmd/fsb/
Rename-Item -LiteralPath ".\fsb.sample.env" -NewName ".\fsb.env"
notepad fsb.env
# (adicione suas variáveis de ambiente, veja a próxima seção para mais informações)
.\fsb run
</code></pre>

<p>Para parar o programa, pressione <kbd>CTRL</kbd>+<kbd>C</kbd>.</p>

<hr>

<h2 id="configurando-as-coisas">Configurando as coisas</h2>

<p>Se você estiver hospedando localmente, crie um arquivo chamado <code>fsb.env</code> no diretório raiz e adicione todas as variáveis lá. Você pode verificar o arquivo <code>fsb.sample.env</code>.</p>

<p>Um exemplo de arquivo <code>fsb.env</code>:</p>

<pre><code>API_ID=452525
API_HASH=esx576f8738x883f3sfzx83
BOT_TOKEN=55838383:seubottokenaqui
LOG_CHANNEL=-10045145224562
PORT=8080
HOST=http://seuipdoservidor
# (se você quiser configurar múltiplos bots)
MULTI_TOKEN1=55838373:seutokenworkerbotaqui
MULTI_TOKEN2=55838355:seutokenworkerbotaqui
</code></pre>

<h3 id="variáveis-de-ambiente-obrigatórias">Variáveis de ambiente obrigatórias</h3>
<p>Antes de executar o bot, você precisará configurar as seguintes variáveis obrigatórias:</p>
<ul>
  <li><code>API_ID</code> : Este é o ID da API para sua conta do Telegram, que pode ser obtido em my.telegram.org.</li>
  <li><code>API_HASH</code> : Este é o hash da API para sua conta do Telegram, que também pode ser obtido em my.telegram.org.</li>
  <li><code>BOT_TOKEN</code> : Este é o token do bot do Telegram Media Streamer, que pode ser obtido no <a href="https://telegram.dog/BotFather">@BotFather</a>.</li>
  <li><code>LOG_CHANNEL</code> : Este é o ID do canal de log onde o bot vai encaminhar as mensagens de mídia e armazenar esses arquivos para que os links diretos gerados funcionem. Para obter o ID do canal, crie um novo canal no Telegram (público ou privado), poste algo no canal, encaminhe a mensagem para <a href="https://telegram.dog/MissRose_bot">@missrose_bot</a> e <strong>responda à mensagem encaminhada</strong> com o comando /id. Copie o ID do canal encaminhado e cole-o neste campo.</li>
</ul>

<h3 id="variáveis-de-ambiente-opcionais">Variáveis de ambiente opcionais</h3>
<p>Além das variáveis obrigatórias, você pode configurar as seguintes variáveis opcionais:</p>
<ul>
  <li><code>PORT</code> : Define a porta que sua webapp vai escutar. O valor padrão é 8080.</li>
  <li><code>HOST</code> : Um nome de domínio totalmente qualificado se estiver presente, ou use o IP do seu servidor. (ex. <code>https://example.com</code> ou <code>http://14.1.154.2:8080</code>)</li>
  <li><code>HASH_LENGTH</code> : Tamanho personalizado para os URLs gerados. O comprimento deve ser maior que 5 e menor ou igual a 32. O valor padrão é 6.</li>
  <li><code>USE_SESSION_FILE</code> : Usa arquivos de sessão para o(s) bot(s) worker. Isso acelera o tempo de inicialização dos bots worker. (padrão: <code>false</code>)</li>
  <li><code>USER_SESSION</code> : Uma string de sessão do pyrogram para um bot de usuário. Usado para adicionar automaticamente os bots ao <code>LOG_CHANNEL</code>. (padrão: <code>null</code>)</li>
  <li><code>ALLOWED_USERS</code> : Uma lista de IDs de usuários separados por vírgula (<code>,</code>). Se isso for configurado, somente os usuários dessa lista poderão usar o bot. (padrão: <code>null</code>)</li>
</ul>

<hr>

<h2 id="contribuindo">Contribuindo</h2>
<p>Sinta-se à vontade para contribuir com este projeto se tiver alguma ideia adicional.</p>

<h2 id="créditos">Créditos</h2>
<ul>
  <li><a href="https://github.com/celestix">@celestix</a> pelo <a href="https://github.com/celestix/gotgproto">gotgproto</a></li>
  <li><a href="https://github.com/divyam234">@divyam234</a> pelo projeto <a href="https://github.com/divyam234/teldrive">Teldrive</a></li>
</ul>

</body>
</html>
