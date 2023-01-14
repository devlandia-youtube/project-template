# 🎥 Vídeo
Repositório do vídeo "Como deixar seus projetos Node mais profissionais". 

## Resumo
**Eslint** <br />
A primeira ferramenta que utilizamos no vídeo foi o Eslint. Para fazer isso, usamos a biblioteca [eslint-config-standard-with-typescript](https://www.npmjs.com/package/eslint-config-standard-with-typescript).

Primeiro instale as dependências:
```bash
$ npm install --save-dev \
    typescript@\* \
    eslint@^8.0.1 \
    eslint-plugin-promise@^6.0.0 \
    eslint-plugin-import@^2.25.2 \
    eslint-plugin-n@^15.0.0 \
    @typescript-eslint/eslint-plugin@^5.0.0 \
    eslint-config-standard-with-typescript@latest
```

Após isso, crie na raiz do seu projeto um arquivo chamado `.eslintrc.json` com o seguinte código:
```json
{
  "extends": "standard-with-typescript",
  "parserOptions": {
    "project": "./tsconfig.json"
  }
}
```

Prontinho! Agora, para melhorar mais ainda sua produtividade, não esqueça de instalar a dependência do Eslint no vscode. Assim como eu fiz no vídeo no time 04:29 😉.

**Jest**
A segunda ferramenta foi o [Jest](https://jestjs.io/). Uma ferramenta muito massa para criar testes automatizados. Para usar ela, instalamos:
```bash
$ npm install --save-dev jest
```

Outra questão é que quando usa o Typescript devemos instalar o `@types/jest`:
```bash
$ npm install --save-dev @types/jest
```
Por fim, você pode precisar instalar alguma dependência como o `ts-jest` para ajudar com o typescript, mais sobre isso na [docs](https://kulshekhar.github.io/ts-jest/docs/getting-started/installation/#jest-config-file).

**Husky**
Ferramenta fundamental para manter a ordem em um time de desenvolvimento. Para instalar:
```bash
$ npm install husky --save-dev
```

Então, rodamos esses dois comandos, para criar um script no `package.json` e rodar ele para iniciar o husky:
```
npm pkg set scripts.prepare="husky install"
npm run prepare
```
*para mais informações sempre olhe a documentação oficial: https://github.com/typicode/husky* <br />

Com isso feito, instalamos o `lint-staged` para conseguir rodar determinadas ações apenas em arquivos que foram de fato modificados.
```bash
$ npm install lint-staged --save-dev
```
Para configurar, crie na raiz do projeto um arquivo chamado `lintstagedrc.json` e coloque o seguinte:
```json
{
  "*.ts": [
    "npm run lint:fix",
    "npm run test:staged"
  ]
}
```
Finalizando, podemos criar os nossos hooks que vão impedir que códigos mal indentado ou que quebre os testes, sejam commitados ou subido para o repositório:
```bash
$ npx husky add .husky/pre-commit "npx lint-staged"
```
E o hook do push:
```bash
$ npx husky add .husky/pre-push "npm run test:covarege"
```

🎉E VOILÁ! Terminamos as configurações. Essas ferramentas são muito profissionais, então, caso esteja no início, é muito provável que você sentiu que alguma ou todas
sejam desnecessárias. Mas, não se preocupe em querer usar todas elas do dia para noite, com o tempo vai aparecendo momentos em que você vai enxergar a real necessidade desse tipo
de ferramenta. E tenha um ótimo dia.

🧠 Você pode aprender qualquer coisa e até a próxima.

---
<p align="center">Feito com 💚 por <a href="https://github.com/404jv/" target="_blank">João Victor Ramalho Alves</a><p>
