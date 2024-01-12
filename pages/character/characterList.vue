<script setup lang="ts">
// 型定義をimportする際は import type
import type { Character } from "@/types/interface";

definePageMeta({ layout: "character" });
const PAGE_TITLE = "キャラクターリスト";
useHead({ title: PAGE_TITLE });

// キャラクターリストをステートから取得
const characterList = useState<Map<number, Character>>("characterList");
</script>

<template>
  <nav id="breadcrumbs">
    <ul>
      <li>
        <NuxtLink :to="{ name: 'index' }">TOP</NuxtLink>
      </li>
      <li>{{ PAGE_TITLE }}</li>
    </ul>
  </nav>
  <section>
    <h2>{{ PAGE_TITLE }}</h2>
    <p>追加は<NuxtLink :to="{ name: 'character-characterAdd' }">こちら</NuxtLink>から</p>
    <section>
      <ul>
        <li v-for="[id, character] in characterList" :key="id">
          <NuxtLink :to="{ name: 'character-characterDetail-id', params: { id: id } }">
            No:{{ id }} {{ character.name }}
          </NuxtLink>
        </li>
      </ul>
    </section>
  </section>
</template>