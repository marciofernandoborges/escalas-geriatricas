# Escalas Geriátricas — pasta pronta para o GitHub Pages

App de 138 escalas de avaliação geriátrica e 3 ferramentas de farmacoterapia, com cálculo automático, interpretação, conduta sugerida
e texto pronto para o prontuário. Construído a partir do acervo **Geriatria Total** (328 obras).

Publicando esta pasta, o app ganha um endereço `https://` — e é isso que destrava o **ícone na tela
de início do iPhone**, o modo tela cheia e o funcionamento offline.

---

## O que tem aqui

| Arquivo | Para que serve |
|---|---|
| `index.html` | app de escalas — 138 escalas e 3 ferramentas |
| `aga.html` | app da Avaliação Geriátrica Ampla completa, com laudo e relatório impressos |
| `manifest.webmanifest` | diz ao iPhone/Android o nome, as cores e os ícones do app de escalas |
| `aga.webmanifest` | o mesmo, para o app da AGA — nome e ícone próprios |
| `sw.js` | service worker — guarda o app no aparelho para funcionar **sem internet** |
| `icon-180.png` · `icon-192.png` · `icon-512.png` · `icon-512-maskable.png` | ícones do app de escalas (**EG**, azul) |
| `icon-aga-180.png` · `icon-aga-192.png` · `icon-aga-512.png` · `icon-aga-512-maskable.png` | ícones do app da AGA (**AGA**, verde) |
| `.nojekyll` | impede o GitHub de reprocessar os arquivos |

Não mexa nos nomes dos arquivos — o `index.html` e o `sw.js` procuram uns aos outros por nome.

---

## Publicar — caminho sem terminal (10 minutos)

1. Crie uma conta em **github.com**, se ainda não tiver.
2. Clique em **New repository** (botão verde, ou o `+` no canto superior direito).
3. Preencha:
   - **Repository name:** `escalas-geriatricas`
   - Marque **Public** — o GitHub Pages gratuito só funciona em repositório público.
   - Não marque nenhuma outra opção. Clique em **Create repository**.
4. Na tela seguinte, clique em **uploading an existing file**.
5. Arraste **os arquivos de dentro desta pasta** (não a pasta em si) para a área de upload.
   São 15 arquivos. O `.nojekyll` é invisível no Finder — pressione `Command + Shift + .` para
   mostrar arquivos ocultos antes de arrastar.
6. Clique em **Commit changes**.
7. Vá em **Settings** (aba no topo do repositório) → **Pages** (menu da esquerda).
8. Em **Source**, escolha **Deploy from a branch**; em **Branch**, escolha `main` e a pasta `/ (root)`.
   Clique em **Save**.
9. Espere de 1 a 3 minutos e recarregue a página. O endereço aparece no topo:

   ```
   https://SEU-USUARIO.github.io/escalas-geriatricas/
   ```

   A Avaliação Geriátrica Ampla fica em `https://SEU-USUARIO.github.io/escalas-geriatricas/aga.html`
   — abra esse endereço no Safari e adicione à tela de início. Os dois apps ficam separados na tela,
   com ícones diferentes: **EG** em azul para as escalas, **AGA** em verde para a avaliação ampla.

## Publicar — caminho pelo terminal

```bash
cd "caminho/para/esta/pasta"
git init && git add -A && git commit -m "Escalas Geriátricas"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/escalas-geriatricas.git
git push -u origin main
```

Depois faça os passos 7 a 9 acima para ligar o Pages.

---

## Instalar no iPhone

1. Abra o endereço **no Safari** (precisa ser o Safari — Chrome no iOS não instala).
2. Toque no botão **Compartilhar** (o quadrado com a seta para cima).
3. Role e toque em **Adicionar à Tela de Início**.
4. Confirme o nome (**Escalas**) e toque em **Adicionar**.

O ícone aparece junto dos outros apps. Ao abrir por ele, o app roda em tela cheia, sem a barra do
Safari — e **funciona sem internet**, porque o `sw.js` guardou tudo no aparelho na primeira visita.

**No Android:** abra no Chrome e toque em **Instalar app** no menu de três pontos.

**No Mac:** basta salvar o endereço nos favoritos. O app já é otimizado para tela grande.

---

## Atualizar o app depois

Substitua o `index.html` no repositório pela versão nova e **incremente a versão do cache** na
primeira linha do `sw.js`:

```js
const CACHE = 'escalas-geriatricas-v8';   // era v7
```

Sem trocar esse número, os aparelhos que já instalaram continuam abrindo a versão antiga do cache.

---

## Duas coisas que vale saber

**O site fica público.** Qualquer pessoa com o endereço acessa. Isso não é um problema de
privacidade do paciente — o app não guarda nada: as respostas vivem só na memória da aba e somem ao
fechar. Nenhum dado sai do aparelho, nenhum servidor recebe nada. Mas o conteúdo em si fica visível
na internet, então evite acrescentar material que não possa ser público.

**Licenças dos instrumentos.** O MEEM tem direitos autorais da PAR Inc. e o MoCA exige registro e
treinamento formal do aplicador (por isso, no app, o MoCA aparece como calculadora de subescores, não
com os itens). Para uso clínico individual isso não costuma ser questionado; para publicar como
serviço aberto e divulgado, o cuidado é maior. Se preferir, remova ou substitua esses dois
instrumentos antes de publicar — RUDAS e SLUMS, ambos livres, cobrem a mesma função de rastreio.

---

## Conteúdo

138 escalas aplicáveis item a item, em 15 domínios: outros (18), cognição (15), fragilidade (15),
humor (14), mobilidade e quedas (14), prognóstico (12), delirium (10), funcionalidade (8), nutrição (8),
dor (8), comportamento (5), sono (4), pele (4), cuidador (2) e farmacoterapia (1).

Mais 3 ferramentas de farmacoterapia: calculadora de carga anticolinérgica (ACB) com 93 fármacos,
critérios de Beers 2023 (58 critérios buscáveis) e STOPP/START (63 critérios por sistema).

O app tem duas abas: **Aplicar**, onde as escalas são preenchidas, e **Sessão**, que acumula os
resultados do atendimento e monta o texto da evolução.

As condutas são sínteses das fontes do acervo e do consenso da área — orientam a decisão clínica,
não a substituem.
