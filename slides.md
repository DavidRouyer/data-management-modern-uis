---
theme: seriph
background: https://images.unsplash.com/photo-1557264337-e8a93017fe92?q=90&w=2070
class: text-center
highlighter: shikiji
lineNumbers: false
info: |
  ## Client-server interaction
  Presentation slides for data management in front-end.
drawings:
  persist: false
transition: slide-left
title: Interaction client-serveur
mdc: true
---

# Interaction client-serveur

Penser une interface utilisateur moderne

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Pressez Espace pour commencer <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Introduction

Une interface interagit avec les données de trois manières différentes :
<br>
<br>
<br>
<br>
<br>
<br>
<div class="items-center w-full grid grid-cols-3">
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

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

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

<!--
Here is another comment.
-->

---
transition: slide-up
level: 2
---

# Partie 1 : Queries - L'état (state)

<br>

1. Télécharge les données (**fetch**) du serveur sur l'interface
<br>
<br>
2. Stockage dans l'état (**state**) de l'application
<br>
<br>
3. Le state est détruit quand on ferme l'onglet ou le navigateur

---
transition: slide-up
level: 2
---

# Partie 1 : Queries - UX avec l'état

<br>

1. Première fois que l'on accède à l'information
   - On affiche le chargement
   - Une fois le chargement terminé, on stocke la donnée dans l'état et on l'affiche
<br>
<br>
2. Les fois suivantes
   - On affiche les données de l'état
<br>
<br>
<br>
<p class="text-red-600">
  <lucide-shield-alert /> Que se passe-t-il si les données sont mises à jour ?
</p>

---
transition: slide-up
level: 2
---

# Partie 1 : Queries - La fraîcheur des données

<br>

Fraîcheur des données :
- Pendant une période, les données sont jugées fraîches (**fresh**)
- Passée cette période, la donnée est jugée périmée (**stale**)
<br>
<br>
<br>
<p class="text-red-600">
  <lucide-shield-alert /> Ajouter un état sur les données ne permet pas de les mettre à jour ?
</p>

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
---

# Partie 1 : Queries - Mettre à jour les données 1

<br>
<br>
<br>
<br>
<br>

- Quand on navigue sur l'application
- Quand on met à jour une partie de l'application
- Quand on clique sur F5

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
---

# Partie 1 : Queries - Mettre à jour les données 2

<br>
<br>
<br>
<br>
<br>

- Quand on retourne sur un onglet

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
---

# Partie 1 : Queries - Mettre à jour les données 3

<br>
<br>
<br>
<br>
<br>

- Quand on est déconnecté/reconnecté du réseau

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
---

# Partie 1 : Queries - UX avec l'état et la fraîcheur
Mise à jour des données
<br>

1. Les données sont fraîches
   - On n'interroge pas le serveur
   - On affiche les données de l'état (fraîches)

2. Les données sont périmées
   - On interroge le serveur
   - On affiche les données de l'état (périmées)
   - On met à jour les données dans l'état
   - On affiche les données de l'état (fraîches)

<p class="text-green-600">
  <lucide-sparkles /> Meilleure UX
</p>

---
transition: slide-up
level: 2
---

# Partie 1 : Queries - Le code

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

# Partie 1 : Queries - Exemple détail de vente

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

# Partie 1 : Queries - Exemple liste de ventes

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
---

# Partie 2 - Mutations - UX

<br>

Mises à jour optimistes

On part du principe que l'action sera effectuée avec succès

<p class="text-green-600">
  <lucide-sparkles /> Meilleure UX
</p>

---
transition: slide-up
level: 2
---

# Partie 2 - Mutations - Déroulement

<br>

1. Mettre à jour l'état (**state**)
<br>
<br>
2. Envoyer les données au serveur
<br>
<br>
3. Effectuer des queries OU annuler les changements

---
transition: fade-out
---

# Partie 2 - Mutations - Le code

<br>

```ts {all|2|3|5|16|17|19|20|all}
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
---

# Partie 3 : Subscriptions - Ecouter les changements

<br>

Message proactif du serveur nous indiquant qu'une mise à jour de données a été effectuée

---
transition: fade-out
---

# Partie 3 - Subscriptions - Le code

<br>

```ts {all|5|7|all}
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
---

# Aller plus loin

<br>

> Le state est détruit quand on ferme l'onglet ou le navigateur

Stocker l'état dans le cache du navigateur

---
layout: default
---

# Des questions ?