<template>
  <div class="home">
    <div class="title">
      {{ homeI18n.title[selectedLang] }} <span class="title_colored">{{homeI18n.titleColored[selectedLang]}}</span>.
    </div>
    <p>{{ homeI18n.description[selectedLang] }}</p>
    <a class="contact_button" href="mailto: contact@valentin-gindre.fr">{{ homeI18n.contact[selectedLang] }}</a>
  </div>
</template>

<script>
import homeI18n from '@/assets/I18n/home.json'

export default {
  props: ['selectedLang'],
  data () {
    return {
      homeI18n
    }
  }
}
</script>
