<template>
  <div id="app">
    <editor
    v-model="content"
    api-key="no-api-key"
    :init="{
      height: 300,
      menubar: false,
      plugins: [
        'advlist autolink lists link image charmap print preview anchor',
        'searchreplace visualblocks code fullscreen',
        'insertdatetime media table paste code help wordcount'
      ],
      toolbar:
        'undo redo | formatselect | bold italic backcolor | \
        alignleft aligncenter alignright alignjustify | \
        bullist numlist outdent indent | removeformat | help'
    }"
    />
    <p>This is the content you entered:</p>
    <div class="result"><pre>{{ content }}</pre></div>
  </div>
</template>

<script>
import Editor from '@tinymce/tinymce-vue'

export default {
  name: 'EditContent',
  components: {
    Editor
  },
  data () {
    return {
      content: ''
    }
  }
}
</script>

<style>
.result {
  text-align: initial;
  display: flex;
  justify-content: center
}

pre {
  background: #e3e3e3;
  display: block;
  width: 200px;
  padding: 36px 24px;
}
</style>
