<template>
    <div class="card larger_card">
        <div class="image">
            <img :src="require(`../assets/img/ProjectsCards/${imageName}`)" :style="'--hover-translation: ' + imageHoverTranslation" :alt="imageAlt">
        </div>
        <div class="content">
            <div class="top_card">
                <h3>{{ title }}</h3>
                <div class="tags">
                    <span class="tag" v-for="(tag, id) in tags" :key="id">
                        {{ tag }}
                    </span>
                </div>
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
    'imageName',
    'imageAlt',
    'imageHoverTranslation',
    'title',
    'tags',
    'description',
    'githubLink',
    'githubLogoAlt',
    'websiteLink',
    'websiteLinkText',
    'externalLinkAlt'
  ]
}
</script>
