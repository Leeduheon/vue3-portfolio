<template>
  <section id="detail" class="container">
    <h1>{{ item.title }}</h1>
    <article class="pb-5">
      <img
        :src="`${item.imgUrl}`"
        :alt="`${item.title}`"
      />
      <p>{{ item.desc }}</p>
      <small class="text-secondary">{{ item.skills }}</small>
      <p>
        <a
          :href="`${item.link}`"
          class="btn btn-primary mt-4"
          target="_blank"
        >홈페이지
        </a>
      </p>
      <br>
      <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Rerum soluta nihil earum harum possimus quidem minus voluptatibus vitae expedita quia voluptatem dolorum pariatur omnis, molestias, placeat quo cumque deserunt at.</p>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quos, consequatur. Alias dignissimos beatae sequi corrupti atque ducimus expedita optio voluptatum maiores nisi, vero nobis consequatur neque ut soluta nemo aliquam!</p>
      <button @click="$router.back()" class="btn btn-secondary">돌아가기</button>
    </article>
  </section>  
</template>
  
<script setup>
  import { computed } from 'vue'
  import { useRoute } from 'vue-router'

  const props = defineProps({
    data: Array,
  })

  const route = useRoute()

  // 1 ~ data.length 범위의 정수가 아니면 기본값 1
  const item = computed(() => {
    const id = Number(route.params.id)
    const isValid = Number.isInteger(id) && id >= 1 && id <= props.data.length
    return props.data[(isValid ? id : 1) - 1]
  })
</script>
  
<style lang="scss" scoped>
  #detail h1 {
    display: flex;
    gap: 1rem;
    align-items: center;
    .badge {
      font-size: small;
    }
  }

  article {
    img {
      width: 100%;
      aspect-ratio: 8/3;
      object-fit: cover;
      object-position: top;
      margin-bottom: 1em;
    }
  }
</style>
