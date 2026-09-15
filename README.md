# Lupa

Um fórum-comunidade de ideias. 4chan (fóruns/boards livres) + Orkut (perfis e recados) + SpaceHey (perfil customizável), rodando como app instalável no seu computador.

> **Este pacote já vem configurado no modo online.** O `config.json` já está preenchido com o serviço online do Lupa — quem baixar, extrair e abrir já entra direto em **online — dados compartilhados**, sem mexer em nada. Se um dia você trocar de projeto serviço online, é só editar o `config.json` de novo (veja a seção "Modo online" mais abaixo).

## Como abrir (jeito mais fácil, Windows)

Dê **duplo-clique em `abrir-lupa.bat`**, na pasta do Lupa. Ele já cuida de tudo (instala o necessário na primeira vez e abre o app). Só precisa ter o [Node.js](https://nodejs.org) instalado antes — se não tiver, o próprio `.bat` avisa e te manda pro link certo.

Nas próximas vezes, é só dar duplo-clique de novo — abre direto, sem instalar nada outra vez.

## Rodar em modo desenvolvimento (via terminal, qualquer sistema)

Pré-requisito: [Node.js](https://nodejs.org) instalado (versão 18 ou mais recente).

```bash
npm install
npm start
```

Isso abre o Lupa como uma janela própria no seu PC. Os dados (perfis, tópicos, comunidades, recados) ficam salvos localmente, e continuam lá da próxima vez que você abrir o app.

## Gerar um instalador de verdade (.exe / .dmg / .AppImage)

```bash
npm install
npm run dist
```

O instalador pronto aparece na pasta `dist/`. Gere o instalador **no mesmo sistema operacional** de quem vai usar (rode no Windows pra gerar `.exe`, no Mac pra gerar `.dmg`, no Linux pra gerar `.AppImage`).

## Contas — versão 4.0 (uma conta por dispositivo, sem login)

Não existe mais criar conta, nem fazer login, nem username, nem senha. Cada dispositivo tem **uma única conta**, criada automaticamente na primeira vez que o Lupa abre — o app já entra direto, sem tela nenhuma no meio do caminho. O apelido exibido (editável na aba **Eu**) pode ter até **30 caracteres**, e mensagens de tópicos, respostas, mural de comunidade e recados têm limite de **600 caracteres**.

O id dessa conta fica guardado num arquivo fora da pasta do Lupa (na pasta de dados do usuário do sistema), então continua sendo o mesmo: ao atualizar o Lupa pra uma versão nova, e mesmo ao reinstalar o app — porque a conta é do **dispositivo**, não do download ou da versão instalada.

> **Se você já tinha uma versão anterior do Lupa rodando** (com username + senha, ou antes disso, um e-mail falso por baixo dos panos): era esse sistema de conta que causava os erros aleatórios na hora de criar conta. Rode o `online-setup.sql` novamente (arquivo atualizado, na pasta do Lupa) pra remover essa tabela de contas antiga — os perfis já existentes continuam intactos.

## Idioma (Português, English, Español)

O Lupa tem suporte a **português (Brasil), inglês e espanhol**.

- **Configurável na instalação (Windows, `.exe`):** ao gerar o instalador com `npm run dist` no Windows, a primeira tela pergunta o idioma (Português/English/Español). O idioma escolhido já vem pré-selecionado quando o app abre pela primeira vez.
- **Configurável a qualquer momento na aba "Eu":** tem um campo **Idioma** lá embaixo, com os três idiomas — muda a interface inteira na hora, sem reiniciar o app.

Se nada for escolhido (ex.: `npm start` em modo dev, ou instalação no Mac/Linux, que não passam pela tela do instalador), o Lupa tenta usar o idioma do sistema operacional e cai pro português se não reconhecer.

## Anônimo temporário

Na aba **Eu**, tem uma opção **"ficar anônimo temporariamente"**. Enquanto ela estiver marcada, tudo que você postar (tópicos, respostas, mural, recados) aparece assinado como **Anônimo** em vez do seu apelido — do jeito clássico de fórum. Desmarcar volta a assinar com seu nome normalmente. Sua conta continua a mesma; é só a assinatura dos posts que muda.

## Fóruns

Os fóruns (boards) seguem a organização por categoria e os códigos curtos no estilo `/a/`, `/v/`, `/g/` etc — todos os quadros seguros para o trabalho (SFW), agrupados em: **Cultura Japonesa**, **Video Games**, **Interesses**, **Criativo** e **Outros**.

## Como funciona hoje

- **Fóruns**: dezenas de quadros fixos organizados por categoria (Cultura Japonesa, Video Games, Interesses, Criativo, Outros — veja a seção "Fóruns" acima), onde qualquer um abre tópicos e responde, no estilo fórum antigo. Dá pra anexar uma foto em qualquer tópico ou resposta.
- **Comunidades**: grupos permanentes que qualquer pessoa cria, entra e posta no mural — like Orkut. O mural também aceita fotos.
- **Perfis**: cada apelido tem uma página com bio, avatar (inicial do nome, ou uma foto), cor de tema, contador de visitas, "quem passou por aqui" e um mural de recados que outros deixam pra você (também com foto e curtidas) — like Orkut/SpaceHey.
- **Busca**: acha tópicos, comunidades e perfis por palavra-chave, direto na barra da sidebar.
- **Notificações**: sino na sidebar avisa quando alguém responde seu tópico ou deixa um recado.
- **Curtidas e edição**: qualquer post/resposta/recado pode ser curtido; você pode editar ou apagar os seus (o primeiro post de um tópico só pode ser editado, não apagado).
- **Player de música**: disquinho no canto inferior direito — clique pra tocar uma bossa nova em loop, clique de novo pra pausar. Puramente decorativo, opcional.
- **Efeitos sonoros**: som ao abrir o app, ao enviar qualquer post/resposta/recado, e um "ding" quando chega notificação nova.
- **"Eu"**: onde você define seu apelido, bio, gostos (filmes, séries, livros, músicas, jogos), avatar (inicial do nome, ou uma foto de verdade), cor e se quer ficar anônimo temporariamente. Não tem login: a conta é uma só por dispositivo, criada automaticamente.
- **Seguir**: siga qualquer perfil; aparece uma aba "Seguindo" no perfil de cada um, e você é avisado quando alguém que você segue abre um tópico novo, ou quando alguém passa a te seguir.
- **@menção e #board**: escreva `@ApelidoSemEspaco` em qualquer post pra mencionar alguém (ele recebe notificação), ou `#a` (o código de um fórum) pra linkar direto pro quadro.
- **Respostas aninhadas**: dentro de um tópico, dá pra responder a um comentário específico (não só ao tópico), formando uma conversa em árvore, tipo Reddit.
- **Repost**: republique um tópico ou post de mural pro seu próprio perfil.
- **Mensagens diretas**: só funciona no modo online, e só entre duas pessoas que se seguem mutuamente. Mostra quando a outra pessoa está online e quando está digitando.
- **Fotos e vídeos**: qualquer tópico, post de mural ou recado aceita uma foto (comprimida e guardada junto com os dados) ou um vídeo curto (até 30MB — sobe pro serviço online, ou fica salvo localmente se você estiver no modo local).

> Nota sobre fotos e vídeos: fotos ficam salvas comprimidas junto com os dados (local ou no serviço online). Vídeos não são comprimidos — no modo online sobem pro serviço de armazenamento à parte; no modo local ficam numa pasta dentro dos dados do app. Não é o YouTube — é pra um clipezinho, não pra um filme inteiro.

**Se você já tinha o Lupa rodando em modo online (serviço online) antes dessa versão:** rode novamente o `online-setup.sql`. Ele adiciona as tabelas/colunas novas (seguir, mensagens diretas, gostos, repost) e o bucket de vídeos, sem apagar nada que já existia.

## Modo online (dados compartilhados entre todo mundo)

O Lupa já vem pronto pra funcionar com um banco de dados compartilhado via **serviço online** (tem plano gratuito). Sem configurar nada, ele roda **local** (cada instalação isolada). Configurando, todo mundo que instalar o Lupa com o mesmo `config.json` vê os mesmos tópicos, comunidades e perfis.

**1. Crie o projeto serviço online**
- Vá em painel do serviço online, crie uma conta gratuita e um novo projeto.
- Espere o projeto terminar de provisionar (leva ~1-2 minutos).

**2. Crie as tabelas**
- No painel do projeto, abra o **SQL Editor**.
- Cole o conteúdo do arquivo `online-setup.sql` (está na pasta do Lupa) e clique em **Run**.

**3. Pegue suas credenciais**
- Vá em **Project Settings → API**.
- Copie a **Project URL** e a chave **anon public**.

**4. Preencha o `config.json`**
Abra o arquivo `config.json` na pasta do Lupa com o Bloco de Notas (ou qualquer editor de texto) e cole os valores:

```json
{
  "urlOnline": "https://SEU-PROJETO.exemplo",
  "chaveOnline": "sua-chave-aqui"
}
```

Salve o arquivo, feche o Lupa se estiver aberto, e abra de novo (`npm start` ou o `abrir-lupa.bat`). O canto inferior esquerdo passa a mostrar **online — dados compartilhados**.

**5. Distribua com as credenciais já dentro**
Se você quer que qualquer pessoa que baixe o app já entre direto no modo compartilhado (sem precisar mexer em nada), é só deixar o `config.json` já preenchido com as suas credenciais **antes** de subir o projeto pro GitHub ou gerar o instalador (`npm run dist`). A chave "anon" é feita pra ser pública — o controle de acesso fica nas regras que o `online-setup.sql` já configura.

> Nota: por não ter sistema de login, qualquer pessoa com o app consegue ler e escrever nos dados — é o mesmo espírito informal de fóruns antigos. Não é o lugar certo pra guardar algo sensível.

Sem configurar o serviço online, os dados continuam salvos **localmente** no navegador embutido do Electron (persistem entre aberturas do app, mas não são compartilhados entre instalações diferentes).

## Publicando no GitHub

1. Crie um repositório novo e suba esta pasta inteira (menos `node_modules/` e `dist/` — inclua um `.gitignore` com essas duas linhas).
2. No README do repositório, deixe instruções de instalação (pode copiar as desta seção).
3. Se quiser distribuir binários prontos (sem a pessoa precisar rodar `npm install`), use `npm run dist` e suba os arquivos gerados em `dist/` como *Release* do GitHub.

## Próximos passos possíveis

A base online já está preparada. As próximas evoluções podem ser coisas como moderação (banimento por dispositivo, limite de posts por tempo), paginação de tópicos grandes, ou grupos privados dentro das comunidades.
