<template>
  <div :class="'color_theme ' + colorMode" :style="mobileMenuIsActive && isMobileSize ? containerStyleWhenMenu() : ''">
    <header :class="mobileMenuIsActive ? 'menu_is_active' : ''">
      <div class="topbarMobile">
        <div class="website_title">
          <span class="first_name">Valentin</span>
          <span class="last_name">Gindre</span>
        </div>
        <button v-if="isMobileSize" id="mobileMenuButton" :class="mobileMenuIsActive ? 'active' : ''" @click="mobileMenuIsActive = !mobileMenuIsActive" :aria-label="headerFooterI18n.toggleMenuButtonAriaLabel[selectedLang]">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
      <transition name="slide-fade">
        <div class="menu" v-if="mobileMenuIsActive && isMobileSize || !isMobileSize">
          <nav>
            <router-link @click="mobileMenuIsActive = false" to="/">{{ headerFooterI18n.homeLink[selectedLang] }}</router-link>
            <router-link @click="mobileMenuIsActive = false" to="/about">{{ headerFooterI18n.aboutLink[selectedLang] }}</router-link>
            <router-link @click="mobileMenuIsActive = false" to="/projects">{{ headerFooterI18n.projectsLink[selectedLang] }}</router-link>
          </nav>
          <div class="mobile_bottom">
            <button class="color_modes_btn" @click="toggleTheme()" :aria-label="headerFooterI18n.colorModesBtnAriaLabel[selectedLang]">
              <img class="moon" src="@/assets/img/lightModeBtn/moon.svg" alt="">
              <img class="sunray" src="@/assets/img/lightModeBtn/sunray.svg" alt="">
              <img class="sun_circle" src="@/assets/img/lightModeBtn/sun-circle.svg" alt="">
            </button>
            <select v-model="selectedLang" name="langSelect">
              <option value="fr">FR</option>
              <option selected value="en">EN</option>
            </select>
            <a class="download_CV" :style="'background-color: var(' + downloadCVColorVar + ')'" target="_blank" href="https://drive.google.com/uc?export=download&id=16WR7K7XciMvofvZCqKJFq3eQyzyTQoli" download>{{ headerFooterI18n.CV[selectedLang] }}</a>
          </div>
        </div>
      </transition>
    </header>

    <router-view :selectedLang="selectedLang"/>

    <footer>
      <span class="credits">{{ headerFooterI18n.credits[selectedLang] }}</span>
      <button @click="scrollToTop" :aria-label="headerFooterI18n.goToTopButtonAriaLabel[selectedLang]">
        <img src="@/assets/img/go-up.svg" class="goToTop" :alt="headerFooterI18n.goToTopImageAlt[selectedLang]">
      </button>
      <span class="creator">{{ headerFooterI18n.creator[selectedLang] }}</span>
    </footer>

    <script type="module" src="https://widget.wantag.com/widget.js" crossorigin data-project-id="2" />
  </div>

</template>

<script>
import headerFooterI18n from '@/assets/I18n/header&footer.json'

export default {
  data () {
    return {
      colorMode: window.matchMedia && window.matchMedia('(prefers-color-scheme: light)').matches ? 'light' : 'dark',
      headerFooterI18n,
      selectedLang: 'fr',
      goToTopVisible: false,
      downloadCVColorVar: '#000',
      isMobileSize: false,
      mobileMenuIsActive: false,
      topbarAnimation: ''
    }
  },
  methods: {
    toggleTheme () {
      if (this.colorMode === 'dark') {
        this.colorMode = 'light'
      } else {
        this.colorMode = 'dark'
      }
    },
    changeDownloadCVColor (path) {
      switch (path) {
        case '/':
          this.downloadCVColorVar = '--home-color'
          break
        case '/about':
          this.downloadCVColorVar = '--about-color'
          break
        case '/projects':
          this.downloadCVColorVar = '--projects-color'
          break
        default:
          this.downloadCVColorVar = '--default-home-color'
      }
    },
    verifWidth () {
      if (window.innerWidth < 1000) {
        this.isMobileSize = true
      } else {
        this.isMobileSize = false
      }
    },
    scrollToTop () {
      window.scrollTo({ top: 0, behavior: 'smooth' })
    },
    containerStyleWhenMenu () {
      return 'overflow-y: hidden; height: 100vh; height: 100svh'
    }
  },
  watch: {
    '$route.path' (newPath) {
      this.changeDownloadCVColor(newPath)
    },
    selectedLang () {
      document.documentElement.setAttribute('lang', this.selectedLang)
    }
  },
  mounted () {
    this.changeDownloadCVColor(this.$route.path)
    this.verifWidth()
    window.onresize = this.verifWidth
  }

}
</script>
