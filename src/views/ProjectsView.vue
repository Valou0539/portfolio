<template>
    <div class="projects">
        <h2>{{ projectsI18n.projectsTitle[selectedLang] }}</h2>
        <div class="featured_projects_cards_container">
            <LargerCard v-for="(card, id) in cards.largerCards"
                :key="id"
                :imageName="card.imageName"
                :imageAlt="projectsI18n.cardsImageAlt[card.I18nIndex][selectedLang]"
                :imageHoverTranslation="card.imageHoverTranslation"
                :title="card.title"
                :tags="card.tags"
                :description="projectsI18n.cardsDescription[card.I18nIndex][selectedLang]"
                :githubLink="card.githubLink"
                :githubLogoAlt="projectsI18n.githubLogoAlt[selectedLang]"
                :websiteLink="card.websiteLink"
                :websiteLinkText="projectsI18n.cardsLink[selectedLang]"
                :externalLinkAlt="projectsI18n.externalLinkAlt[selectedLang]"
            />
        </div>
        <div class="other_projects_cards_container">
            <SmallerCard v-for="(card, id) in cards.smallerCards"
                :key="id"
                :title="card.title"
                :description="projectsI18n.cardsDescription[card.I18nIndex][selectedLang]"
                :githubLink="card.githubLink"
                :githubLogoAlt="projectsI18n.githubLogoAlt[selectedLang]"
                :websiteLink="card.websiteLink"
                :websiteLinkText="projectsI18n.cardsLink[selectedLang]"
                :externalLinkAlt="projectsI18n.externalLinkAlt[selectedLang]"
            />
        </div>
    </div>
</template>

<script>
import LargerCard from '@/components/LargerCard.vue'
import SmallerCard from '@/components/SmallerCard.vue'
import projectsI18n from '@/assets/I18n/projects.json'
import cards from '@/assets/projectsCards.json'

export default {
  components: {
    LargerCard, SmallerCard
  },
  props: ['selectedLang'],
  data () {
    return {
      projectsI18n,
      cards
    }
  }
}
</script>
