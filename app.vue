<script setup lang="ts">

// 型定義をimportする際は import type
import type { Character } from "@/types/interface";

// キャラクターリストデータ
useState<Map<number, Character>>("characterList", (): Map<number, Character> => {
  const characterListInit = new Map<number, Character>();
  characterListInit.set(1, { id: 1, name: "ルフィ", bounty: 1000 });
  characterListInit.set(2, { id: 2, name: "ゾロ", bounty: 500 });
  return characterListInit;
})

</script>

<template>
  <BaseSection />
</template>

<style>
section {
  border: blue 5px solid;
  margin: 10px;
}
</style>