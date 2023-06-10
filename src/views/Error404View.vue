<template>
    <div class="error404">
        <h2>{{ error404I18n.error404[selectedLang] }}</h2>
        <span>{{ error404I18n.message[selectedLang] }}</span>
    </div>
</template>

<script>
import error404I18n from '@/assets/I18n/error404.json'

export default {
  props: ['selectedLang'],
  data () {
    return {
      error404I18n
    }
  }
}
</script>
