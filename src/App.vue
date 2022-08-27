<template>
  {{ computedRef }}
  <hr />
  <div v-if="myProp">
    {{ computedRefButton }}
  </div>

  <hr />
  <Foo :heading="refHeading" :textarea="refTextarea" :section="computedRef">
    <section ref="computedRef">
      <h2 ref="heading">Heading</h2>
      <textarea ref="textarea"></textarea>
      <br />
      <button ref="button">test</button>
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
      myProp: true,
    };
  },
  computed: {
    computedRef() {
      if (!this.isMounted) return;
      console.log(this.$refs.computedRef);
      return this.$refs.computedRef;
    },
    computedRefButton() {
      return this.$refs.button;
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

  updated() {
    console.log(this.$refs);
  },
};
</script>
