<template>
  <div class="childPage">
    <h1> {{payload.title}} </h1>
    <h2> Payload from asyndData </h2>
    <div style="margin: 1rem 0;padding: 1rem 0; border: 1px solid #000"> {{payload}}</div>
    <h2> Check if page javascript is loaded </h2>
    <div style="border-bottom: 1px solid #000;margin-bottom: 1rem;"> {{textInput}} </div>
    <input v-model="textInput" />
  </div>
</template>
<script>
const SOME_DATA = {
  id0: { title: 'Title of id0' },
  id1: { title: 'Title of id1' }
}
export default {
  asyncData ({ params }) {
    const payload = SOME_DATA[params.id] || { title: 'ID not found' }
    return { payload }
  },
  data () {
    return {
      textInput: 'some text'
    }
  }
}
</script>
