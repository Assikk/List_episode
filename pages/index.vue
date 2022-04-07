<template>
  <div class="m-[20px]">
    <h1 class="text-center text-3xl font-bold mb-[10px]">Список эпизодов</h1>
    <div class="flex justify-between items-center">
      <Add
      :class="show ? 'block' : 'hidden'"
      @click="getEpisodes">
      Загрузить
      </Add>
      <div>
        <Add
        @click="getEpisodes">
          По умолчанию
        </Add>
        <Add
        @click="decreasing">
          По убыванию количества персонажей
        </Add>
        <Add
        @click="increasing">
          По возрастанию количества персонажей
        </Add>
      </div>
    </div>
    <div class="grid gric-col gap-4 mt-[10px]">
      <Episode
      v-for="(episode, index) in episodes"
      :key="index"
      :episode="episode"
      @click="deleteEpisode(episode.episode_id, episodes)"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      episodes: '',
      show: true
    }
  },
  methods: {
    async getEpisodes() {
      try {
        let res = await this.$axios("https://breakingbadapi.com/api/episodes")
        this.show = false
        this.episodes = res.data
        console.log(this.episodes);
      } catch(err) {
        console.log(err);
      }
    },
    deleteEpisode(id, episodes) {
      episodes.splice(id, 1)
    },
    decreasing() {
      this.episodes.sort((a, b) =>  a.characters.length > b.characters.length ? 1: -1)
      console.log('123');
    },
    increasing() {
      this.episodes.sort((a, b) =>  a.characters.length < b.characters.length ? 1: -1)
    },
  },
}
</script>
