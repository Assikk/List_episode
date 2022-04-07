<template>
  <div class="w-[300px] h-[100px] border-[1px] border-[#000] mx-auto p-[10px]">
    <div class="flex items-center justify-between mb-[5px]">
      <div class="flex gap-4 items-center">
        <button class="px-[5px] bg-[#00b700] rounded"
        @click="remove">
        -
        </button>
        <button class="px-[5px] bg-[#00b700] rounded"
        @click="add">
          +
        </button>
      </div>
      <button class="px-[5px] bg-[#00b700] rounded"
      @click="$emit('click')">
        X
      </button>
    </div>
    <p>
      Title: {{episode.title}}
    </p>
    <p>
      {{episode.characters.length}} {{secondText}}
    </p>
  </div>
</template>
<script>
export default {
  props: ['episode'],
  data() {
    return {
      text: 'Персонаж',
    }
  },
  computed: {
    secondText() {
      if(this.episode.characters.length == 1) {
        this.text = 'Персонаж'
      }
      if(this.episode.characters.length > 1 || this.episode.characters.length < 5) {
        this.text = 'Персонажа'
      }
      if(this.episode.characters.length >=5 ) {
        this.text = 'Персонажей'
      }
      return this.text
    },
    example() {
      return this.episode.characters.length
    }
  },
  methods: {
    remove() {
      this.episode.characters.pop()
    },
    add() {
      this.episode.characters.push({})
    }
  }
}
</script>
