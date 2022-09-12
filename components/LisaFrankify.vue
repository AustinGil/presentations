<script>
export default {
  computed: {
    letters() {
      const slotContent = this.$slots.default() || []
      if (!slotContent.length) return []
      const text = slotContent[0].children;
      return `✧･ﾟ:*✧･ﾟ:*${text}*:･ﾟ✧*:･ﾟ✧`.split('')
    }
  }
}
</script>
<template>
  <div class="lisa-frankify">
    <span 
      v-for="(letter, i) in letters"
      :key="i"
      :aria-hidden="i < 10 ? true : i >= letters.length - 10 ? true : null"
    >
      {{ letter }}
    </span>
  </div>
</template>
<style>
.lisa-frankify span {
  display: inline-block;
  min-width: .5em;
  min-height: .5em;
  border-radius: 1000px;
  font-size: 30px;
  font-family: "Comic Sans MS", "Comic Sans", sans-serif;
  font-weight: 900;
  text-align: center;
}
.lisa-frankify :nth-child(8n+1) {
  background: hsl(0,100%,70%);
}
.lisa-frankify :nth-child(8n+2) {
  background: hsl(45,100%,70%);
}
.lisa-frankify :nth-child(8n+3) {
  background: hsl(90,100%,70%);
}
.lisa-frankify :nth-child(8n+4) {
  background: hsl(135,100%,70%);
}
.lisa-frankify :nth-child(8n+5) {
  background: hsl(180,100%,70%);
}
.lisa-frankify :nth-child(8n+6) {
  background: hsl(225,100%,70%);
}
.lisa-frankify :nth-child(8n+7) {
  background: hsl(270,100%,70%);
}
.lisa-frankify :nth-child(8n+8) {
  background: hsl(315,100%,70%);
}
</style>