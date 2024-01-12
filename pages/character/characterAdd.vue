<script setup lang="ts">
// 型定義をimportする際は import type
import type { Character } from "@/types/interface";
import { reactive } from "vue";

const router = useRouter();
// router.push() => 指定の居場所へ
// router.back() => 履歴上で一つ前の画面

// キャラクターリストをステートから取得
const characterList = useState<Map<number, Character>>("characterList");
// 入力データと同期させるCharacterオブジェクトの用意
const character: Character = reactive({
  id: 0,
  name: "",
  bounty: 0,
})

// 登録ボタンが押された時の処理
const onAdd = (): void => {
  characterList.value.set(character.id, character);
  router.push({ name: "character-characterList" });
}
</script>

<template>
  <h1>キャラクター設定</h1>
  <nav id="breadcrumbs">
    <ul>
      <li>
        <NuxtLink :to="{ name: 'index' }">TOP</NuxtLink>
      </li>
      <li>
        <NuxtLink :to="{ name: 'character-characterList' }">キャラクターリスト</NuxtLink>
      </li>
      <li>キャラクター追加</li>
    </ul>
  </nav>
  <section>
    <h2>キャラクターリスト</h2>
    <p>追加はこちらから</p>
    <section>
      <h2>キャラクター追加</h2>
      <p>情報を入力し、登録ボタンを押してください。</p>
      <form :submit.prevent="onAdd">
        <table>
          <tr>
            <td>
              <label for="addId">No:</label>
            </td>
            <td>
              <input type="number" id="addId" v-model.number="character.id" required>
            </td>
          </tr>
          <tr>
            <td>
              <label for="addName">名前:</label>
            </td>
            <td>
              <input type="text" id="addName" v-model="character.name" required>
            </td>
          </tr>
          <tr>
            <td>
              <label for="addBounty">懸賞金:</label>
            </td>
            <td>
              <input type="number" id="addBounty" v-model.number="character.bounty" required>
            </td>
          </tr>
        </table>
        <button @click="onAdd">登録</button>
      </form>
    </section>
  </section>
</template>