# GraphQuest: Exploring and Implementing GraphQL

Ce projet contient plusieurs tâches pour apprendre GraphQL avec l'API Rick and Morty.

## Structure du projet

### Tâche 0 et 1: Requêtes GraphQL de base
- `/character/` - Contient les requêtes pour récupérer des personnages
- `/episode/` - Contient les requêtes pour récupérer des épisodes

### Tâche 3: Application React avec GraphQL
Pour créer l'application React, suivez les étapes suivantes :

1. Créez un répertoire `alx-graphql-0x01`
2. Exécutez : `npx create-next-app@latest alx-rick-and-morty-app --typescript --tailwind --eslint --no-app --import-alias "@/*"`
3. Installez les dépendances : `npm install @apollo/client graphql @types/graphql`

### Fichiers requis

#### graphql/apolloClient.ts
```typescript
import { ApolloClient, InMemoryCache, HttpLink} from "@apollo/client"

const client = new ApolloClient({
  link: new HttpLink({
    uri: "https://rickandmortyapi.com/graphql"
  }),
  cache: new InMemoryCache()
})

export default client;
```

#### graphql/queries.ts
```typescript
import { gql } from "@apollo/client";

export const GET_EPISODES = gql\`
  query getEpisodes($page: Int, $filter: FilterEpisode) {
    episodes(page: $page, filter: $filter) {
      info {
        pages
        next
        prev
        count
      }
      results {
        id
        name
        air_date
        episode
      }
    }
  }
\`;
```

#### pages/_app.tsx
```typescript
import "@/styles/globals.css";
import type { AppProps } from "next/app";
import { ApolloProvider } from "@apollo/client";
import client from "@/graphql/apolloClient";

export default function App({ Component, pageProps }: AppProps) {
  return (
    <ApolloProvider client={client}>
      <Component {...pageProps} />
    </ApolloProvider>
  )
}
```

### Tâche 4: Requête de l'endpoint GraphQL

Pour la tâche 4, dupliquez le répertoire `alx-graphql-0x01` vers `alx-graphql-0x02` et ajoutez les fichiers suivants :

#### interfaces/index.ts
```typescript
interface InfoProps {
    pages: number
    next: number
    prev: number
    count: number
}

export interface EpisodeProps {
  id: number
  name: string
  air_date: string
  episode: string
  info: InfoProps
}

export type EpisodeCardProps = Pick<EpisodeProps, 'id' | 'name'| 'air_date' | "episode">
```

#### components/common/EpisodeCard.tsx
```typescript
import { EpisodeCardProps } from "@/interfaces";

const EpisodeCard = ({ id, name, air_date, episode }: EpisodeCardProps) => {
  return (
    <div key={id} className="bg-white cursor-pointer shadow-md rounded-lg p-4 m-4 transition-transform duration-200 hover:scale-105">
      <div className="flex justify-between items-center">
        <h2 className="text-xl font-semibold text-gray-800">{name}</h2>
        <span className="border px-2 text-xs rounded-full bg-blue-600 text-white flex items-center">{episode}</span>
      </div>
      <p className="text-gray-600">{air_date}</p>
    </div>
  );
};

export default EpisodeCard;
```

## Instructions d'exécution

1. Naviguez vers le répertoire du projet React
2. Exécutez `npm run dev`
3. Ouvrez `http://localhost:3000` dans votre navigateur

## Validation

Assurez-vous que tous les fichiers sont créés selon la structure spécifiée et que l'application fonctionne correctement avec l'affichage des épisodes paginés.
