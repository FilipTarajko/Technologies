<template>
  <div :class="[filteredTag == tag.text ? 'currentlySelected' : '', 'ListItem']" @click='changeTag(tag.text)' >
    <img :src=getImageSrc(tag.imageSrc)>
    <div class='tagTextDiv'>
      {{ tag.text }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    tag: Object,
    filteredTag: String
  },
  computed: {
    imageSrc: function() {
      return '../assets/'+this.item.imageSrc+'.png'
    }
  },
  methods: {
    getImageSrc(src) {
      try{
        var images = require.context('../assets/', false, /\.png$/)
        return images('./'+src+'.png')
      } catch (error) {
          console.log('trying to src.ico')
          return 'https://icons.duckduckgo.com/ip2/'+src+'.ico'
      }
    },
    changeTag(tag){
        console.log('32')
        this.$emit('changeTag', tag)
        console.log('34')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.ListItem{
  transition-property: background-color, border-color;
  transition-duration: 0.5s;
  background-color: hsl(var(--main-hue), 45%, 70%);
  border-color: hsl(var(--main-hue), 30%, 50%);
  border-style: solid;
  border-width: 3px;
  font-size: calc(10px + 0.6vw);
  margin: 5px;
  border-radius: 10px;
  user-select: none;
  word-break: break-word;
  padding: 5px 5px;
  /* width: calc(33.333% - 26px); */
  position: relative;
}
.ListItem:hover{
  transition-property: all;
  transition-duration: 0.5s;
  background-color: hsl(var(--main-hue), 70%, 70%);
  border-color: hsl(var(--main-hue), 55%, 50%);
  color: hsl(calc(var(--main-hue) + 120), 70%, 50%);
}
.tagTextDiv {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
img {
  width: 13%;
  float: left;
}
a {
  --link-margin: -6px;
  position: absolute;
  left: var(--link-margin);
  right: var(--link-margin);
  bottom: var(--link-margin);
  top: var(--link-margin);
}
.currentlySelected{
  background-color: hsl(var(--main-hue), 70%, 70%);
  border-color: hsl(var(--main-hue), 55%, 50%);
}
</style>
