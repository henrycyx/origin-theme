<template>
  <!-- Error/empty state -->
  <SectionUndefined
    v-if="!heading && !text"
    heading="Heading with text"
    description="No heading or text added"
  />

  <section v-else class="container py-16 lg:py-24 xl:py-32">
    <div :class="{ 'md:flex': headingPosition === 'left' }">
      <div
        :class="{
          'md:w-1/3': headingPosition === 'left',
          'text-center mx-auto': headingPosition === 'top-center'
        }"
        class="max-w-2/3 md:mb-0"
      >
        <span v-if="label" class="block label-xs-bold mb-4">{{ label }}</span>
        <h2 v-balance-text class="m-0 md:text-5xl xl:text-7xl">
          {{ heading }}
        </h2>
      </div>

      <div
        v-if="text"
        :class="{
          'mx-auto md:w-2/3': headingPosition === 'top-center' && textColumns === 'single',
          'sw-multi-column': headingPosition.includes('top') && textColumns === 'dual',
          'text-justify md:mt-8 lg:mt-10 xl:mt-12': headingPosition.includes('top'),
          'mt-1 md:w-2/3 md:pl-12 lg:pl-16 xl:pl-20': headingPosition === 'left'
        }"
        class="lg:text-lg"
        v-html="text"
      ></div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SectionHeadingWithText',

  props: {
    type: {
      type: String,
      default: null
    },
    id: {
      type: String,
      default: null
    },
    label: {
      type: String,
      default: null
    },
    heading: {
      type: String,
      default: null
    },
    text: {
      type: String,
      default: null
    },
    headingPosition: {
      type: String,
      default: 'top-center'
    },
    textColumns: {
      type: String,
      default: 'dual'
    }
  }
}
</script>

<style lang="postcss" scoped>
.sw-multi-column {
  @screen md {
    column-count: 2;
    column-gap: 2rem;
  }
}
</style>
