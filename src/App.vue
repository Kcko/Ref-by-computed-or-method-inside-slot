<template>
  {{ computedRef }}
  <Foo :heading="refHeading" :textarea="refTextarea" :section="computedRef">
    <section ref="computedRef">
      <h2 ref="heading">Heading</h2>
      <textarea ref="textarea"></textarea>
    </section>
  </Foo>
</template>

<script>
import Foo from './components/Foo.vue';

export default {
  name: 'App',
  components: {
    Foo,
  },
  data() {
    return {
      isMounted: false,
    };
  },
  computed: {
    computedRef() {
      if (!this.isMounted) return;
      console.log(this.$refs.computedRef);
      return this.$refs.computedRef;
    },
  },
  methods: {
    refHeading() {
      return this.$refs.heading;
    },
    refTextarea() {
      return this.$refs.textarea;
    },
  },

  mounted() {
    this.isMounted = true;
  },
};
</script>
