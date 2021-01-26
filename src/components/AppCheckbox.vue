<template>
  <label class="form-checkbox"
         :class="classes">
    <input type="checkbox"
           class="form-checkbox__input">
    <span class="form-checkbox__checkbox"></span>
    <span class="form-checkbox__name">Принимаю <a href="">условия</a> использования</span>
  </label>

</template>

<script>
export default {
  name: 'AppCheckbox',
  props: {
    classes: String,
  },
};
</script>

<style scoped
       lang="scss">
.form-checkbox {
  display     : flex;
  align-items : center;

  // .form-checkbox__input
  &__input {
    position : absolute !important;
    clip     : rect(1px 1px 1px 1px); /* IE6, IE7 */
    clip     : rect(1px, 1px, 1px, 1px);
    padding  : 0 !important;
    border   : 0 !important;
    height   : 1px !important;
    width    : 1px !important;
    overflow : hidden;

    &:checked + .form-checkbox__checkbox {
      border-color        : #0880ae;
      background-image    : url(../assets/tick.svg);
      background-position : center;
      background-size: cover;
    }

  }

  // .form-checkbox__name
  &__name {
    font-weight : 500;
    font-size   : 16px;
    line-height : 1.3125;
    color       : #756f86;

    > a {
      color           : #0880ae;
      text-decoration : none;
    }
  }

  // .form-checkbox__checkbox
  &__checkbox {
    border        : 1px solid #dbe2ea;
    box-shadow    : 0 4px 8px rgba(44, 39, 56, 0.04);
    border-radius : 4px;
    width         : 28px;
    height        : 28px;
    display       : inline-block;
    margin-right  : 8px;
    cursor        : pointer;
  }
}
</style>
