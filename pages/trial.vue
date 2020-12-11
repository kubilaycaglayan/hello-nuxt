<template>
  <body>
    <button
      type="button"
      @click="toggleData"
    >Toggle Class Names</button>

    <div
      class="container"
      :class="[classes, {'CONTROL': true}]"
    >

    </div>
  </body>
</template>

<style>
  .container {
    width: 50px;
    height: 50px;
  }

  .red {
    background-color: red;
  }

  .green {
    background-color: green;
  }
</style>

<script>
  const nComponent = {
    name: 'nComponent',
    data: () => ({
      active: false,
      experimental: true,
      green: true,
      red: false,
    }),
    computed: {
      classes() {
        console.log(" XX -> in classes() this.active", this.active);
        return {
          'primary': this.active,
          'red': this.red,
          'green': this.green
        };
      },
      dialogClasses() {
        return {
          'md-fullscreen': this.mdFullscreen,
          'md-transition-off': this.transitionOff,
          'md-reference': this.mdOpenFrom || this.mdCloseTo
        };
      },
      styles() {
        return {
          transform: this.dialogTransform
        };
      },
      computedActive() {
        return this.active
      }
    },
    methods: {
      toggleData() {
        window.setTimeout(() => {
          this.red = !this.red,
          this.green = !this.green,
          this.active = !this.active
        })
      },
    }
  };
  export default nComponent;
</script>
