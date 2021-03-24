<template>
  <div class="card" :style="{ backgroundImage: `url(${person.imageURL})`}">
    <h2>{{ person.name }}</h2>
    <div class="dragBox" draggable="true">
      &times; {{ person.test }}
    </div>
  </div>
</template>

<script>

export default {
  props: {
    person: {
      type: Object,
      default () {
        return null
      }
    }
  },
  data () {
    return {

    }
  },
  created () {

  },
  mounted () {

  },

  methods: {

  }
}
</script>

<style scoped>
.card {
  height: 400px;
  width: 300px;
  float: left;
  position: relative;

  margin: 0 5vw;

  border: 5px solid var(--blue);
  transition: all 1s, top 1s, left 1s;
  transition-property: box-shadow, border;
}

.card h2 {
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: var(--color-grey);
  text-align: center;
  font-weight: 800;
  margin: 2vh 0;
  width: 100%;
}

.dragBox {
  text-align: center;
  position: absolute;
  bottom: 2vh;
  left: 63px;
  width: 150px;
  font-weight: 600;
  border: 1px solid var(--gray);

  padding: 10px;
  cursor: move;
  background-color: var(--gray)
}

.dragBox.over {
    opacity: 0.4;
}

[draggable] {
    user-select: none;
}
</style>
