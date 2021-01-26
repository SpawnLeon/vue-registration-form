<template>
  <div class="form-item"
       :class="classes">
    <label :for="`form-item-${this._uid}`"
           class="form-item__name"
           v-if="name">{{ name }}</label>
    <input type="text"
           v-mask="mask"
           class="form-item__input"
           :placeholder="placeholder"
           :id="`form-item-${this._uid}`"
           v-model="model">
    <span class="form-item__error">{{ error }}</span>
  </div>

</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    },
    name: String,
    placeholder: String,
    classes: String,
    error: String,
    mask: Boolean,
  },
  name: 'AppInput',
  data() {
    return {};
  },
  computed: {
    model: {
      get() {
        return this.value;
      },
      set(val) {
        this.$emit('input', val);
      },
    },
  },
  directives: {
    mask: {
      bind: (el, binding) => {
        // eslint-disable-next-line no-param-reassign
        el.oninput = function (e) {
          if (!binding.value) return;
          if (!e.isTrusted) return;
          const x = this.value.replace(/\+.|\D/g, '').match(/(\d{0,3})(\d{0,3})(\d{0,2})(\d{0,2})/);
          // eslint-disable-next-line no-nested-ternary
          this.value = !x[1] ? '' : !x[2] ? `+7 (${x[1]}` : `+7 (${x[1]}) ${x[2]}${x[3] ? `-${x[3]}` : ''
          }${x[4] ? `-${x[4]}` : ''}`;
          el.dispatchEvent(new Event('input'));
        };
      },
    },
  },

};
</script>

<style scoped
       lang="scss">

::placeholder {
  color : #7c9cbf;
}

:-ms-input-placeholder {
  color : #7c9cbf;
}

::-ms-input-placeholder {
  color : #7c9cbf;
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

  // .form-item__input
  &__input {
    background-color : #fff;
    border           : 1px solid #dbe2ea;
    box-shadow       : 0 4px 8px rgba(44, 39, 56, 0.04);
    border-radius    : 6px;
    font-style       : normal;
    font-weight      : normal;
    font-size        : 16px;
    line-height      : 1.3125;
    color            : #2c2738;
    padding          : 16px 16px 15px 16px;
    font-family      : 'IBM Plex Sans', Helvetica, Arial, sans-serif;
    outline          : none;

    &:focus {
      border-color : #0880ae;
      box-shadow   : 0 0 0 1px #0880ae;
    }
  }

  // .form-item__error
  &__error {
    font-size   : 14px;
    line-height : 1.3857;
    color       : #ff7171;
    margin-top  : 8px;
    height      : 19px;
  }

}
</style>
