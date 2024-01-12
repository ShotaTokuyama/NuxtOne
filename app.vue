<script setup lang="ts">
// 型定義をimportする際は import type
import type { Character } from "@/types/interface";

const SITE_TITLE = "ワンピース";
useHead({
  // title: SITE_TITLE
  titleTemplate: (titleChunk: string | undefined): string => {
    return titleChunk != undefined ? `${titleChunk} | ${SITE_TITLE}` : SITE_TITLE;
  }
});

// キャラクターリストデータ
useState<Map<number, Character>>("characterList", (): Map<number, Character> => {
  const characterListInit = new Map<number, Character>();
  characterListInit.set(1, { id: 1, name: "ルフィ", bounty: 1000 });
  characterListInit.set(2, { id: 2, name: "ゾロ", bounty: 500 });
  return characterListInit;
})

</script>

<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<style>
main {
  border: black 5px solid;
  margin: 10px;
}

#breadcrumbs ul {
  padding-left: 0;
}

#breadcrumbs ul li {
  display: inline;
  list-style-type: none;
}

#breadcrumbs ul li::before {
  content: " > ";
}

#breadcrumbs ul li:first-child::before {
  content: none;
}
</style>