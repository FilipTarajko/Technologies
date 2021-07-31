<template>
    <div id='sitename'>
        {{ SiteName }}
    </div>
</template>

<script>
export default {
  name: 'PageTitle',
  props: {
    SiteName: String
  }
}
</script>

<style scoped>
#sitename{
    /* margin-left: 1px; */
    transition-property: all;
    transition-duration: 0.5s;
    font-size: min(12vw, 100px);
    padding: 3% 0px 2%;
    font-weight: bold;
    user-select: none;
    word-break: break-word;
}

:hover{
  color: hsl(calc(var(--main-hue) + 120), 50%, 50%);
}
</style>