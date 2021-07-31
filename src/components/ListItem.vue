<template>
  <div class="ListItem">
    <img :src=getImageSrc(item.imageSrc)>
    <div class='itemTextDiv'>
      {{ item.text }}
    </div>
    <a :href=item.url></a>
  </div>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    item: Object
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
  background-color: hsl(var(--main-hue), 60%, 70%);
  border-color: hsl(var(--main-hue), 45%, 50%);
  color: hsl(calc(var(--main-hue) + 120), 70%, 50%);
}
.itemTextDiv {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
img {
  width: 20%;
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
</style>
