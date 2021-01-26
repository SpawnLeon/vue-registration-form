<template>
  <div class="form-item form__item">
    <label class="form-item__name"
           v-if="name">{{ name }}</label>
    <v-select :options="languages"
    ></v-select>
  </div>

</template>

<script>
import vSelect from 'vue-select';

export default {
  name: 'AppSelect',

  components: {
    vSelect,
  },
  props: {
    languages: {
      type: Array,
      default: () => ({}),
    },
    name: String,
  },
};
</script>

<style lang="scss">
@import "node_modules/vue-select/src/scss/vue-select.scss";

.vs--open .vs__dropdown-toggle {
  border-radius : 6px;
  border        : 1px solid #dbe2ea;
}

.vs__dropdown-toggle {
  background-color : #fff;
  border           : 1px solid #dbe2ea;
  box-shadow       : 0 4px 8px rgba(44, 39, 56, 0.04);
  border-radius    : 6px;
  font-style       : normal;
  font-weight      : normal;
  font-size        : 16px;
  line-height      : 1.3125;
  color            : #2c2738;
  padding          : 10px 16px 13px 16px;
  font-family      : 'IBM Plex Sans', Helvetica, Arial, sans-serif;
  outline          : none;
}

.vs__actions {
  path {
    fill : #0880ae;
  }
}

.vs__dropdown-menu {
  padding       : 12px 0;
  top           : calc(100% + 4px);
  border        : 1px solid #dbe2ea;
  box-shadow    : 0px 4px 8px rgba(44, 39, 56, 0.04), 0px 20px 20px rgba(44, 39, 56, 0.04);
  border-radius : 6px;
}

.vs__dropdown-option {
  line-height : 1.3125;
  padding     : 10px 16px 13px 16px;
  font-family : 'IBM Plex Sans', Helvetica, Arial, sans-serif;
  font-style  : normal;
  font-weight : normal;
  font-size   : 16px;
  color       : #756f86;

}

.vs__dropdown-option--highlight {
  background : #ebf4f8;

}

.vs__selected {
  margin-left  : 0;
  padding-left : 0;
}

.form-item {
  display        : flex;
  flex-direction : column;

  // .form-item__name
  &__name {
    margin-bottom : 8px;
    font-weight   : 500;
    font-size     : 16px;
    line-height   : 1.2125;
    color         : #756f86;

  }
}
</style>
