<template>
  <div id='parent'>
    <div class="ListItem">
      <img :src=getImage(imageSrc)>
      <div class='itemTextDiv'>
        {{ text }}
      </div>
      <a :href=url></a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageTitle',
  props: {
    SiteName: String
  },
  data: function(){
    return {
      url: 'https://github.com/FilipTarajko',
      imageSrc: 'ft',
      text: 'created by Filip Tarajko'
    }
  },
  methods: {
    getImage: function() {
      var images = require.context('../assets/', false, /\.png$/)
      return images('./ft.png')
    }
  }
}
</script>

<style scoped>

:hover{
  color: hsl(calc(var(--main-hue) + 120), 50%, 50%);
}

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
  position: relative;

  display: flex;
  justify-items: center;
  align-items: center;
}
.ListItem:hover{
  transition-property: all;
  transition-duration: 0.5s;
  background-color: hsl(var(--main-hue), 60%, 70%);
  border-color: hsl(var(--main-hue), 45%, 50%);
  color: hsl(calc(var(--main-hue) + 120), 70%, 50%);
}

img {
  width: 10%;
}
.itemTextDiv {
  word-break: break-word;
  width: 80%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
}
a {
  --link-margin: -6px;
  position: absolute;
  left: var(--link-margin);
  right: var(--link-margin);
  bottom: var(--link-margin);
  top: var(--link-margin);
}

#parent{
  padding: 5% 10%;
}
@media (min-width: 1000px) {
  #parent {
    padding-left: 25%;
    padding-right: 25%;
  }
  img {
    width: 6.66%;
  }
}

@media (min-width: 1500px) {
  #parent {
    padding-left: 35%;
    padding-right: 35%;
  }
  img {
    width: 5%;
  }
}

</style>