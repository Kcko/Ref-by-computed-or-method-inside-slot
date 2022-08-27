<template>
  <slot></slot>
</template>

<script>
export default {
  name: 'Foo',
  props: ['heading', 'textarea', 'section'],
  mounted() {
    this.textarea().value = 'set from Foo vue by ref';

    setTimeout(() => {
      this.heading().style.color = 'red';
      this.section.style.cssText += 'border: 2px solid green';
    }, 2000);
  },
};
</script>
