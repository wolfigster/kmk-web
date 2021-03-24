<template>
  <div class="main-container">
    <template v-for="person in persons">
      <Card :key="person.name" :person="person" />
    </template>
  </div>
</template>

<script>
export default {
  data () {
    return {
      persons: [
        {
          name: 'Chrissy Costanza',
          imageURL: 'https://i.pinimg.com/564x/64/2d/ed/642dedf132aa82c0611548a35cbc41ab.jpg',
          test: 'Kiss'
        },
        {
          name: 'Angela Merkel',
          imageURL: 'https://dspncdn.com/a1/media/692x/7f/f8/59/7ff8598a838f15328eb0f02e91f44d46.jpg',
          test: 'Marry'
        },
        {
          name: 'Ariana Grande',
          imageURL: 'https://www.mountaineers.org/images/placeholder-images/placeholder-300-x-400/image_preview',
          test: 'Kill'
        }
      ],
      dragElements: null,
      draggedElement: null
    }
  },
  watch: {
    draggedElement (value) {
      console.log('draggedElement:')
      console.log(value)
    }
  },
  mounted () {
    this.mountEvents()
  },
  methods: {
    mountEvents () {
      console.log('mountEvents')
      this.dragElements = document.querySelectorAll('.dragBox')
      this.dragElements.forEach((item) => {
        item.addEventListener('dragstart', this.handleDragStart, false)
        item.addEventListener('dragenter', this.handleDragEnter, false)
        item.addEventListener('dragover', this.handleDragOver, false)
        item.addEventListener('dragleave', this.handleDragLeave, false)
        item.addEventListener('drop', this.handleDrop, false)
        item.addEventListener('dragend', this.handleDragEnd, false)
      })
    },
    handleDragStart (event) {
      console.log('handleDragStart')
      event.target.style.opacity = '0.4'

      this.draggedElement = event.target

      event.dataTransfer.effectAllowed = 'move'
      event.dataTransfer.setData('text/html', event.target.innerHTML)
    },
    handleDragOver (event) {
      console.log('handleDragOver')
      if (event.preventDefault) {
        event.preventDefault()
      }
      event.dataTransfer.dropEffect = 'move'
    },
    handleDragEnter (event) {
      console.log('handleDragEnter')
      event.target.classList.add('over')
    },
    handleDragLeave (event) {
      console.log('handleDragLeave')
      event.target.classList.remove('over')
    },
    handleDrop (event) {
      console.log('handleDrop')
      if (event.stopPropagation) {
        event.stopPropagation()
      }
      if (this.draggedElement !== event.target) {
        this.draggedElement.innerHTML = event.target.innerHTML
        event.target.innerHTML = event.dataTransfer.getData('text/html')
      }
      return false
    },
    handleDragEnd (event) {
      console.log('handleDragEnd')
      event.target.style.opacity = '1.0'

      this.dragElements.forEach((item) => {
        item.classList.remove('over')
      })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
