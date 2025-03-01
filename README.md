# Tarefa - Exibição de Filmes com React e TypeScript 🎬

Este é um projeto de treinamento em desenvolvimento web onde o objetivo é consumir uma API ou um arquivo **JSON** contendo informações sobre filmes e exibir essas informações em uma interface simples utilizando **React** e **TypeScript**. A tarefa foi realizada no contexto do programa de capacitação **3035Teach** da **3035 Tech**, com foco no aprendizado sobre consumo de APIs e manipulação de dados em formato JSON.

Acesse o projeto [aqui](https://felipecardosovargas.github.io/tarefa-filmes/).

## Descrição 📋

O projeto tem como objetivo consumir um arquivo JSON contendo informações sobre filmes e exibi-las de forma interativa. O projeto inclui as seguintes funcionalidades:

- Exibição do **nome** e **poster** de cada filme.
- Exibição de uma **descrição** curta para cada filme.
- Layout simples e responsivo para visualização em diferentes dispositivos.

## Tecnologias Utilizadas 🛠️

- **React**: Biblioteca JavaScript para construção de interfaces de usuário. ⚛️
- **TypeScript**: Superset de JavaScript que adiciona tipagem estática ao código. 📜
- **Vite**: Ferramenta de build rápida para projetos modernos. 🚀
- **CSS**: Estilização básica do componente. 🎨

## Estrutura de Diretórios 📂

A estrutura de diretórios do projeto é organizada da seguinte maneira:

```
Tarefa_Filmes/
│
├── public/               # Arquivos públicos (ex.: index.html)
├── src/
│   ├── App.tsx           # Componente principal da aplicação
│   ├── main.tsx          # Ponto de entrada da aplicação
│   └── styles.css        # Estilos globais
├── package.json          # Dependências e scripts do projeto
├── tsconfig.json         # Configuração do TypeScript
└── README.md             # Arquivo de documentação do projeto
```

### Detalhes

- **`MovieCard.tsx`**: Componente React que recebe as informações de cada filme e as exibe.
- **`App.tsx`**: Componente principal que carrega os filmes e os renderiza utilizando o componente `MovieCard`.
- **`main.tsx`**: Ponto de entrada da aplicação, onde o React é renderizado no DOM.
- **`styles.css`**: Arquivo de estilos CSS para a aplicação.
- **`tsconfig.json`**: Configuração do TypeScript para garantir tipagem estática.

## Como Usar 🚀

1. **Clone o Repositório**:
   Para começar, faça o clone do repositório para sua máquina local:
   ```bash
   git clone https://github.com/Felipecardosovargas/Tarefa_Filmes.git
   ```

2. **Acesse o Diretório**:
   Navegue até o diretório do projeto clonado:
   ```bash
   cd Tarefa_Filmes
   ```

3. **Instale as Dependências**:
   Instale as dependências necessárias usando o npm ou yarn:
   ```bash
   npm install
   # ou
   yarn install
   ```

4. **Execute o Projeto**:
   Inicie o servidor de desenvolvimento com o Vite:
   ```bash
   npm run dev
   # ou
   yarn dev
   ```

5. **Acesse a Aplicação**:
   Abra o navegador e acesse o endereço indicado no terminal (geralmente `http://localhost:5173`).

## Funcionalidades 🎯

- **Exibir filmes**: O projeto consome um JSON contendo informações sobre filmes e exibe o nome, poster e descrição dos filmes.
- **Layout responsivo**: A página é projetada para ser responsiva e funcionar bem em dispositivos móveis e desktop.

## Exemplo de Código de Exibição de Filmes

Aqui está um exemplo do código de um componente `MovieCard.tsx` que exibe as informações de cada filme:

```tsx
import React from 'react';

interface MovieProps {
  title: string;
  description: string;
  poster: string;
}

const MovieCard: React.FC<MovieProps> = ({ title, description, poster }) => {
  return (
    <div className="movie-card">
      <img src={poster} alt={title} />
      <h3>{title}</h3>
      <p>{description}</p>
    </div>
  );
};

export default MovieCard;
```

No componente `App.tsx`, você pode importar e usar o `MovieCard` para exibir os filmes:

```tsx
import React, { useEffect, useState } from 'react';
import MovieCard from './components/MovieCard';

const App: React.FC = () => {
  const [movies, setMovies] = useState<any[]>([]);

  useEffect(() => {
    fetch('/movies.json')  // ou a URL da API de filmes
      .then((response) => response.json())
      .then((data) => setMovies(data));
  }, []);

  return (
    <div className="app">
      <h1>Lista de Filmes</h1>
      <div className="movie-list">
        {movies.map((movie) => (
          <MovieCard
            key={movie.id}
            title={movie.title}
            description={movie.description}
            poster={movie.poster}
          />
        ))}
      </div>
    </div>
  );
};

export default App;
```

## Aprendizados 📚

Durante o desenvolvimento deste projeto, pude praticar e consolidar os seguintes conceitos:

- **Consumo de JSON/API**: Como consumir dados de um arquivo JSON ou API externa.
- **Componentes React**: Criação e utilização de componentes funcionais.
- **State (`useState`)**: Uso de hooks para gerenciar dados do componente.
- **Manipulação de Eventos**: Trabalhar com interações e manipulação de eventos.
- **Estilização CSS**: Como estilizar componentes de forma simples.
