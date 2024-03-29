---
background: https://images.unsplash.com/photo-1557264337-e8a93017fe92?q=90&w=2070
class: text-center
highlighter: shikiji
info: |
  ## Client-server interaction

  Presentation slides for data management in front-end.

  [David Rouyer](https://github.com/davidrouyer) for [Choose](https://www.appchoose.io)
transition: slide-left
layout: cover
---

# Interaction client-serveur

Penser une interface utilisateur moderne

<div class="text-sm">
David Rouyer
</div>


---
layout: center
---

# Introduction

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: fade-out
layout: section
---

## Interface client-serveur en trois concepts
<div class="items-center w-full grid grid-cols-3 my-auto mt-16">
  <div>
    <h2>Queries</h2>
    <p>La récupération de données</p>
  </div>
  <div>
    <h2>Mutations</h2>
    <p>La modification de données</p>
  </div>
  <div>
    <h2>Subscriptions</h2>
    <p>L'écoute des changements</p>
  </div>
</div>

---
transition: slide-up
level: 2
layout: center
---

# Partie 1 : Queries

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# L'état de l'application <code>state</code>

::left::

<br>
<br>

1. La query demande et récupère les données <code>fetch</code> du serveur
<br>
<br>
2. On stocke l'information dans l'état <code>state</code> de l'application
<br>
<br>
3. L'état est détruit quand on ferme l'onglet ou le navigateur

::right::

<img src="/undraw_download_re_li50.svg" class="aspect-square p-16" />

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Première fois que l'on accède à l'information

::left::

<br>
<br>

- On affiche le placeholder
<br>
<br>
- L'information est stockée dans l'état
<br>
<br>
- On remplace le placeholder par l'information

<br>
<br>
<br>
<br>
<br>

::right::

<div class="flex flex-col h-full justify-center">
  <div class="border border-blue-300 shadow rounded-md p-4 mb-24 max-w-sm w-full mx-auto">
    <div class="animate-pulse flex space-x-4">
      <div class="rounded-full bg-slate-700 h-10 w-10"></div>
      <div class="flex-1 space-y-6 py-1">
        <div class="h-2 bg-slate-700 rounded"></div>
        <div class="space-y-3">
          <div class="grid grid-cols-3 gap-4">
            <div class="h-2 bg-slate-700 rounded col-span-2"></div>
            <div class="h-2 bg-slate-700 rounded col-span-1"></div>
          </div>
          <div class="h-2 bg-slate-700 rounded"></div>
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Les fois suivantes

::left::

<br>
<br>
<br>
<br>
<br>
<br>
<br>

- On affiche les données de l'état

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

::right::

<div class="flex flex-col h-full justify-center">
  <div class="border border-blue-300 shadow rounded-md p-4 max-w-sm w-full mx-auto">
    <div class="flex space-x-4">
      <img class="rounded-full h-10 w-10" src="https://www.thegoodgoods.fr/wp-content/uploads/2020/06/montlimart-logo.webp" />
      <div class="flex-1 space-y-6 py-1">
        <div class="h-2 rounded">Montlimart</div>
        <div class="space-y-3">
          <div class="grid gap-4 text-xs">
            Du 01/01/1970 au 19/01/2038
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
level: 2
layout: center
---

# Interface instantanée <streamline-emojis-confetti-ball />

---
transition: slide-up
level: 2
layout: center
---


# Les données peuvent être mises à jour <streamline-emojis-bomb />

---
transition: slide-up
level: 2
layout: two-cols-header
---

# La fraîcheur des données

::left::

<div class="flex flex-col flex-no-wrap justify-center items-center mb-40 px-8">
<streamline-emojis-blossom class="w-24 h-24" />
<p class="text-center">Pendant une période, les données sont jugées fraîches <code>fresh</code></p>
</div>

::right::

<div class="flex flex-col flex-no-wrap justify-center items-center mb-40 px-8">
<streamline-emojis-ambulance class="w-24 h-24" />
<p class="text-center">Passée cette période, la donnée est jugée périmée <code>stale</code></p>
</div>


<div class="abs-br">
  <div className="rounded-md border p-4">
    <div className="flex">
      <div className="flex-shrink-0">
        <lucide-terminal aria-hidden="true" />
      </div>
      <div className="ml-3">
        <span className="text-sm font-medium font-mono">Configuration TanStack Query</span>
        <div className="mt-2 text-sm font-bold font-mono font-italic">
          staleTime
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
level: 2
layout: center
---

# Quand mettre à jour <code>refetch</code><br> les données périmées ? <streamline-emojis-electric-plug />

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Mettre à jour via la navigation

::left::

<br>
<br>
<br>
<br>

- Quand on navigue sur l'application
<br>
<br>
- Quand on met à jour une partie de l'application
<br>
<br>
- Quand on clique sur F5

::right::

<img src="/undraw_destination_re_sr74.svg" class="aspect-square p-16 pb-32" />

<div class="abs-br">
  <div className="rounded-md border p-4">
    <div className="flex">
      <div className="flex-shrink-0">
        <lucide-terminal aria-hidden="true" />
      </div>
      <div className="ml-3">
        <span className="text-sm font-medium font-mono">Configuration TanStack Query</span>
        <div className="mt-2 text-sm font-bold font-mono font-italic">
          refetchOnMount
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Mettre à jour via la présence

::left::

<br>
<br>
<br>
<br>
<br>

- Quand on quitte/retourne sur l'application sans la fermer

::right::

<img src="/undraw_undraw_flying_drone_u3r2_-3-_egfy.svg" class="aspect-square p-16 pb-32" />

<div class="abs-br">
  <div className="rounded-md border p-4">
    <div className="flex">
      <div className="flex-shrink-0">
        <lucide-terminal aria-hidden="true" />
      </div>
      <div className="ml-3">
        <span className="text-sm font-medium font-mono">Configuration TanStack Query</span>
        <div className="mt-2 text-sm font-bold font-mono font-italic">
          refetchOnWindowFocus
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Mettre à jour après déconnexion

::left::

<br>
<br>
<br>
<br>
<br>

- Quand on est déconnecté/reconnecté du réseau

::right::

<img src="/undraw_travel_mode_re_2lxo.svg" class="aspect-square p-16 pb-32" />

<div class="abs-br">
  <div className="rounded-md border p-4">
    <div className="flex">
      <div className="flex-shrink-0">
        <lucide-terminal aria-hidden="true" />
      </div>
      <div className="ml-3">
        <span className="text-sm font-medium font-mono">Configuration TanStack Query</span>
        <div className="mt-2 text-sm font-bold font-mono font-italic">
          refetchOnReconnect
        </div>
      </div>
    </div>
  </div>
</div>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Mises à jour et fraîcheur

::left::

## Les données sont<br> fraîches <streamline-emojis-blossom />
<br>

  - On n'interroge pas le serveur
  - On affiche les données de l'état

<br>
<br>
<br>
<br>

::right::

## Les données sont<br> périmées <streamline-emojis-ambulance />
<br>

  - On affiche les données de l'état (périmées)
  - On interroge le serveur et on met à jour les données dans l'état
  - On affiche les données de l'état (fraîches)

<br>
<br>
<br>
<br>

---
transition: slide-up
level: 2
layout: center
---

# Interface instantanée et <br> données mises à jour <streamline-emojis-confetti-ball /><streamline-emojis-confetti-ball />

---
transition: slide-up
level: 2
---

# Le code

<br>

```ts {all|2|3|4|5|all}

const { data, isLoading, isFetching, error } = useQuery({
  queryKey: [`sales`],
  queryFn: () => fetch('/sales'),
  queryOptions
})
```

---
transition: slide-up
level: 2
---

# Exemple détail de vente

<br>

```ts {all|2|all}
const { data, isLoading, isFetching, error } = useQuery({
  queryKey: [`sale`, { id: 1 }],
  queryFn: () => fetch('/sale/1'),
  queryOptions
})
```


---
transition: fade-out
---

# Exemple liste de ventes

<br>

```ts {all|2|all}
const { data, isLoading, isFetching, error } = useQuery({
  queryKey: [`sales`, { status: 'ongoing', page: 1 }],
  queryFn: () => fetch('/sales?status=ongoing&page=1'),
  queryOptions
})
```

---
transition: slide-up
level: 2
layout: center
---

# Partie 2 - Mutations

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Mises à jour classiques

::left::

- On clique sur un bouton
<br>
<br>
- On affiche un chargement pendant que<br> la requête est envoyée au serveur
<br>
<br>
- On affiche le résultat à l'utilisateur

<br>
<br>
<br>
<br>

::right::

<div class="flex flex-col h-full justify-center">
  <div class="pb-24">
    <button type="button" class="inline-flex items-center px-4 py-2 font-semibold leading-6 text-sm shadow rounded-md text-white bg-indigo-500 hover:bg-indigo-400 transition ease-in-out duration-150 cursor-not-allowed" disabled="">
      <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
      </svg>
      Processing...
    </button>
  </div>
</div>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Mises à jour optimistes

::left::

<br>
<br>
<br>
<br>
<br>

- On clique sur un bouton
<br>
<br>
- On affiche le résultat à l'utilisateur

::right::

<img src="/undraw_completed_m9ci.svg" class="aspect-square p-16 pb-32" />

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Comment ça fonctionne ?

::left::

<br>
<br>
<br>
<br>

1. On envoie les données au serveur
<br>
<br>
2. On met à jour l'état
<br>
<br>
3. En cas d'erreur <streamline-emojis-cross-mark />, on annule les changements<br> et on affiche un message d'erreur

::right::

<img src="/undraw_join_re_w1lh.svg" class="aspect-square p-16 pb-32" />

---
transition: fade-out
---

# Le code

```ts {all|2|16|19|2|3|5|16|17|19|20|all}
const { mutateAsync } = useMutation({
    onMutate: ({ id }) => {
      const previousSale = queryClient.getQueryData([`sale`, { id: 1 }]);

      queryClient.setQueryData(
        [`sale`, { id: 1 }],
        (oldQueryData) =>
          ({
            ...oldQueryData,
            status: 'closed',
          })
      );

      return { previousSale: previousSale };
    },
    onError: (err, { id }, context) => {
      queryClient.setQueryData([`sale`, { id: 1 }], context?.previousSale);
    },
    onSettled: (_, __, { id }) => {
      queryClient.invalidateQueries({ queryKey: [`sale`, { id: 1 }] });
    },
  });
```

---
transition: slide-up
level: 2
layout: center
---

# Partie 3 - Subscriptions

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
level: 2
layout: two-cols-header
---

# Ecouter les changements

::left::

<br>
<br>
<br>

- On ouvre une conversation avec le serveur
<br>
<br>
- Quand une donnée change, le serveur nous envoie un message pour dire qu'une donnée a changé
<br>
<br>
- On ferme la conversation avec le serveur

::right::

<img src="/undraw_audio_conversation_re_3t38.svg" class="aspect-square p-16 pb-32" />

---
transition: fade-out
---

# Le code

<br>

```ts {all|3|5|7|all}
client
  .request({
    query: 'saleUpdated'
  })
  .subscribe({
    next() {
      queryClient.invalidateQueries({ queryKey: [`sale`, { id: 1 }] })
    }
  })
```

---
transition: slide-left
layout: two-cols-header
---

# Aller plus loin

::left::

<br>
<br>
<br>

> L'état est détruit quand on ferme l'onglet ou le navigateur

Amélioration <streamline-emojis-direct-hit />
<br>
Stocker l'état dans le cache du navigateur

<br>

Autre architecture <streamline-emojis-astronaut-1 />
<br>
Local-first application (**Pas à notre portée**)

::right::

<img src="/undraw_maker_launch_re_rq81.svg" class="aspect-square p-16 pb-32" />

---
layout: fact
---

# Des questions ?

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>