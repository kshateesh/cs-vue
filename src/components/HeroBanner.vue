<template>
  <div class="hero-banner" :style="{ background: `${data.bg_color}` }">
    <div :class="[title === 'about-content' ? title : 'home-content']" :style="{color:`${data.text_color}`}">
      <h1 class="hero-title">
        {{ data.banner_title }}
      </h1>
      <p
        :class="[
          'hero-description',
          title === 'about-content' ? 'about-desc' : ''
        ]"
        :style="{color:`${data.text_color}`}"
      >
        {{ data.banner_description }}
      </p>
      <template v-if="data.call_to_action.title && data.call_to_action.href">
        <router-link
          aria-current="page"
          class="btn tertiary-btn"
          to="/"
        >
          Read more
        </router-link>
      </template>
    </div>
    <img
      v-if="data.banner_image"
      :src="data.banner_image.url"
      :alt="data.banner_image.title"
    />
  </div>
</template>

<script lang="ts">

interface Title {
  title: string;
}

import {HeroBanner} from '../typescript/components';
import { defineComponent, PropType } from 'vue';

export default defineComponent({

  props:{
    data:{
      required: true,
      type: Object as PropType<HeroBanner>
    },
    title:{
      required: true,
      type: Object as PropType<Title>
    }
  }
});
</script>
