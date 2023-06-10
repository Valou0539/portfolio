<template>
  <div class="about">
    <section class="biography">
      <h2>{{ aboutI18n.biographyTitle[selectedLang] }}</h2>
      <p>{{ aboutI18n.biographyContent[selectedLang] }}</p>
    </section>
    <section class="skills">
      <h2>{{ aboutI18n.skillsTitle[selectedLang] }}</h2>
      <div class="skills_diagram">
        <h3>&lt; WEB /&gt;</h3>
        <div class="mastered_skills">
          <span>HTML</span>
          <span>CSS</span>
          <span>JavaScript</span>
        </div>
        <div class="good_skills">
          <span>Github</span>
          <span>Web Design</span>
          <span>Figma</span>
          <span>SASS</span>
          <span>VueJS</span>
        </div>
      </div>
    </section>
    <section class="education">
      <h2>{{ aboutI18n.educationTitle[selectedLang] }}</h2>
      <div class="establishment_container">
        <div class="establishment">
          <span class="years">2021 - 2023</span>
          <div class="separator">
            <div class="circle"></div>
            <div class="stroke"></div>
          </div>
          <div class="text">
            <h3 class="formation">{{ aboutI18n.lyceeTitle[selectedLang] }}</h3>
            <span class="place">{{ aboutI18n.lyceeEstablishment[selectedLang] }}</span>
            <p class="description">{{ aboutI18n.lyceeDescription[selectedLang] }}</p>
          </div>
        </div>
        <div class="establishment">
          <span class="years">2023 - {{ aboutI18n.CurrentDate[selectedLang] }}</span>
          <div class="separator">
            <div class="circle"></div>
            <div class="stroke"></div>
          </div>
          <div class="text">
            <h3 class="formation">{{ aboutI18n.BUTTitle[selectedLang] }}</h3>
            <span class="place">{{ aboutI18n.BUTEstablishment[selectedLang] }}</span>
            <p class="description">{{ aboutI18n.BUTDescription[selectedLang] }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import aboutI18n from '@/assets/I18n/about.json'

export default {
  props: ['selectedLang'],
  data () {
    return {
      aboutI18n
    }
  }
}
</script>
