# React

- O que é: biblioteca JS;
- Objetivo: criação de interfaces de usuário;
- Criação: 2011, Facebook;
- Trabalha com a estrutura PWA (renderização do lado do cliente), o que faz com que um arquivo estático renderize componentes - ou seja, as páginas da aplicação são componentes que vão sendo renderizados conforme se navega pelo site;
- Um componente nada mais é do que uma função que retorna um html;
    - O html dentro de uma função js recebe o nome de jsx, o qual é considerado uma sintaxe do html;
    - Componentes sempre devem ser criados com letra inicial maiúscula;
    - Basicamente tudo no React é um componente (tanto uma página quanto seus elementos);
    - A ideia de um componente é não precisar ficar reescrevendo código pois tudo pode ser reutilizado na forma de um componente;

### Modelo

- Modelo;

### Criar um projeto react pelo terminal

- npx create-react-app nome_do_projeto
- npx é um pacote do npm que baixa sempre do repositório mais recente
- Isso cria alguns diretórios, como:
    - node_modules: possui todas as dependências e bibliotecas que serão utilizadas - não é alterada durante o desenvolvimento do projeto;
    - public: possui os principais arquivos iniciais do React;
        - index.html: arquivo estático onde são adicionados os componentes do projeto para serem renderizados;
    - src: abriga todo o projeto;
        - package.json: arquivo que o React utiliza para saber todas as dependências contidas no projeto - assim, conforme forem sendo instaladas bibliotecas, elas vão sendo adicionadas nessas dependências;

### Rodar um projeto

- npm run start ou yarn run start

### Componentes de Classes X Funcionais

- Até a versão 15 do React só existiam componentes de classe, então era necessário criar classes para criar componentes;
- Para evitar verbosidade e outros problemas, foram criados os componentes funcionais, em que os componentes são criados dentro de funções;
- Usar rfc + tab para criar a estrutura de um componente funcional (com uso da extensão ES7+);

### React CLI

- Ferramenta que oferece todas as configurações necessárias para um projeto React;

### React Router

- É uma biblioteca para React que possibilita a navegação entre visualizações de vários componentes, alteração da URL do navegador, entre outras coisas.
- Link para instalação: v5.reactrouter.com/web/guides/quick-start
    - yarn add react-router-dom

### Styled-Components

- Link: [https://styled-components.com/](https://styled-components.com/)
- Permite utilizar utilizações css dentro do js;
- Instalar
    
    ```
    # with npm
    npm install --save styled-components
    # with yarn
    yarn add styled-components
    
    ```
    

### Hooks

- Até a versão 16.7 do React algumas funcionalidades só podiam ser acessadas através de classes;
- Na versão 16.8 foram lançados os hooks, que permitem o uso de vários recursos de forma simples através de funções e ajudam a organizar a lógica utilizada dentro dos componentes;
- Tipos de hooks:
    - **useState**
        - `import { useState } from ‘react’;`
            - Exemplo:
                - `import {useState} from ‘react’;`
                    
                    `const Test = () ⇒ {`
                    
                    `const [name, setName] = useState(’Pablo’)`
                    
                    `const handleChangeName = () ⇒ {`
                    
                    `setName(prev ⇒ prev === ’Pablo’ ? ‘José’ : ‘Pablo’)`
                    
                    `}` 
                    
                    - Objetivo: alterar nome de Pablo para José e vice-versa;
        - Serve para lidar com estado de algum comportamento dentro de um componente - ou seja, lida com alterações feitas em um componente ao longo do tempo;
    - **useEffect**
        - `import { useEffect } from ‘react’;`
            - Chama: `useEffect(()⇒{},[]);`
                - O primeiro parâmetro é uma função que vai fazer algo;
                - O segundo parâmetro é o array de dependência - ou seja, quando se quer que o useEffect execute novamente;
                    - Com o segundo parâmetro vazio, ele renderiza só uma vez;
                    - Com algum componente dentro do segundo parâmetro, ele renderiza toda vez que houver alguma mudança nesse segundo parâmetro;
        - Trabalha com o ciclo de vida do componente - ou seja, lida com os momentos de antes, durante e depois da renderização, deixada de tela, desmonte e pós-desmonte;
    - **useMemo**
        - Memoriza variáveis para evitar a necessidade de re-renderização;
        - Exemplo:
            - `const calculo = useMemo(() ⇒ {`
                
                   `return 10 * 2`
                
                `}, []);`
                
                `console.log(’renderizou’, calculo);`
                
            - Toda vez que um código é re-renderizado, as variáveis são refeitas Isso ocupa espaço e memória. Por isso, o useMemo é capaz de guardar variáveis e evitar essa sobrecarga do sistema pela dispensa da necessidade de refazer o cálculo;
                - Sem a adição de uma dependência, o useMemo guarda o cálculo ainda que hajam alterações em seus valores;
                - Caso seja adicionada uma dependência adequada, o useMemo reconhece se há alteração do valor, re-renderizado caso seja verdadeiro, mas mantendo o valor da memória caso seja falso;
                    - No seguinte exemplo, ainda ocorra alteração da idade, o resultado do cálculo não mudará:
                        - `const handleChangeAge = () ⇒ {`
                            
                               `setAge(prev ⇒  prev === 26 ? 32 : 26)`
                            
                            `}`
                            
                        
                        `const calculo = useMemo(() ⇒ {`
                        
                        `console.log(’calculou’, age)`
                        
                        `return 10 * age`
                        
                        `}, []);`
                        
                        `console.log(’renderizou’, calculo);`
                        
                    - Já aqui, coma adição da dependência “name”, o useMemo reconhece alterações no valor da idade e permite atualização do cálculo:
                        - `const handleChangeAge = () ⇒ {`
                            
                               `setAge(prev ⇒  prev === 26 ? 32 : 26)`
                            
                            `}`
                            
                        
                        `const calculo = useMemo(() ⇒ {`
                        
                        `console.log(’calculou’, age)`
                        
                        `return 10 * age`
                        
                        `}, [age]);`
                        
                        `console.log(’renderizou’, calculo);`
                        
    - **useCallback**
        - Funciona parecido com o useMemo, mas para memorizar funções e evitar o recarregamento daquelas que não foram alteradas;

### React Hook Form

- [https://react-hook-form.com/](https://react-hook-form.com/);
- npm install react-hook-form;

### Axios

- Função: fazer chamada http para api externas;
- h[ttps://axios-http.com/ptbr/docs/intro](https://axios-http.com/ptbr/docs/intro);
- npm install axios;

### Json-server

- [https://www.npmjs.com/package/json-server](https://www.npmjs.com/package/json-server);
- npm install -g json-server;

| código | função |
| --- | --- |
| npx create-react-app nome_do_projeto | criar o projeto |
| yarn||npm run start  | rodar o projeto |
| yarn add react-router-dom | instalar react router |
| npm install --save styled-components || yarn add styled-components | instalar styled-components |
| npm install react-hook-form | instalar react hook form |
| npm install axios |  |

| atalho | função | extensão |
| --- | --- | --- |
| ‘rfc’ + tab | criar a estrutura de um componente | ES7+ React/Redux/React-Native snippets |
|  |  |  |
|  |  |  |
|  |  |  |