<template>
    <div style="display:flex;justify-content: space-evenly;">
        <a
            class="block-button__button"
            :href="data.site.url"
        >{{data.site.text}}</a>
        <a
            class="block-button__button"
            :href="`mail:${data.write.url}`"
        >{{data.write.text}}</a>
        <a
            class="block-button__button"
            :href="`tel:${data.call.url}`"
        >{{data.call.text}}</a>
    </div>
</template>

<script>
export default {
  name: 'leftMenu',
  data: () => ({}),
  props: ['data', 'photo'],
  methods: {
    goUrl (url) {
      location.href = url
    }
  }
}
</script>

<style scoped>
    .block-button {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }
    .block-button__button {
        color: gray;
        padding: 10px 15px;
        margin: 10px 0px;
        width: 200px;
        border: 1px solid gray;
        border-radius: 10px;
    }
    .block-button__button:hover {
        color: #fff;
        background-color: rgb(199, 136, 74);
        border-color: rgb(199, 136, 74);
        cursor: pointer;
    }
</style>
