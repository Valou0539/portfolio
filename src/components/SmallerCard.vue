<template>
    <div class="card smaller_card">
        <div class="content">
            <div class="top_card">
                <h3>{{ title }}</h3>
                <p>{{ description }}</p>
            </div>
            <div class="bottom_card">
                <a v-if="githubLink" class="github" target="_blank" :href="githubLink">
                    <img :src="require(`../assets/img/github-logo.svg`)" :alt="githubLogoAlt">
                </a>
                <a class="website_link" target="_blank" :href="websiteLink">
                    <span>{{ websiteLinkText }}</span>
                    <img :src="require(`../assets/img/external-link.svg`)" :alt="externalLinkAlt">
                </a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  props: [
    'title',
    'description',
    'githubLink',
    'githubLogoAlt',
    'websiteLink',
    'websiteLinkText',
    'externalLinkAlt'
  ]
}
</script>
