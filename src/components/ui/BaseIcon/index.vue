<template>
  <svg xmlns="http://www.w3.org/2000/svg">
    <title v-if="title">{{ title }}</title>
    <use :xlink:href="iconPath" xmlns:xlink="http://www.w3.org/1999/xlink" />
  </svg>
</template>

<script>
  export default {
    name: 'BaseIcon',

    props: {
      name: {
        type: String,
        required: true,
      },
      title: String,
    },

    computed: {
      iconPath() {
        let icon = require(`@/assets/icons/svg/${this.name}.svg`);
        if (Object.prototype.hasOwnProperty.call(icon, 'default')) {
          icon = icon.default;
        }

        return icon.url;
      },
    },
  };
</script>
